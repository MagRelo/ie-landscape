# Product overview: referralTree + Incentive Exchange

_Last checked against [MagRelo/referralTree](https://github.com/MagRelo/referralTree) `main` @ `800da1d` (2026-10-03) and <https://exchange.mattlovan.dev/> on 2026-10-12._

## What it is

Two layers (from the live site):

1. **referralTree**: an on-chain system of record for who referred whom and who got paid. Referral edges are durable and public. Credit is a settlement event in the same transaction as the payout, not a registration. Skiplisting cuts future pay without erasing the graph.
2. **Graph health service** (Incentive Exchange): an opinionated scoring layer. The chain doesn't prove a tree is genuine; farms and long chains still look like referrals. The service scores branching, payout-by-generation and composite health so projects and agents can tell a productive network from a chainy one.

**Live implementation:** Play the Cut (fantasy contests; when someone in your chain wins, a locked share of the pot pays up the invite line). The site showed **$186K paid out, 312 settlements, 40.3% settlement rate, 0.9% skiplist rate** on 2026-10-12.

## Mechanism (as implemented)

Contracts: `src/core/ReferralGraph.sol`, `src/core/RewardCalculator.sol`.

### Graph
- Trees are per `groupId`; a group exists once its first user registers.
- Only **oracles authorized for that group** can `register` / `batchRegister` edges and manage the skiplist. Authorization is per group (`authorizeOracle`, owner only).
- Root registrations point at the sentinel `REFERRAL_ROOT` (`0x…01`). **`REFERRAL_ROOT` is never paid**; ancestor walks stop when they reach it.
- Skiplisted addresses stay in the graph but are omitted from payout walks, and they **don't consume a level**.

### Payout chain
- `getPayoutChain(user, groupId, maxLevels)` returns the trigger user plus up to `maxLevels - 1` skiplist-aware ancestors (seed first).
- `getPayoutAncestors(user, groupId, maxLevels)` returns ancestors **above** the user only.
- **`rewardRoots` uses `getPayoutAncestors(user, groupId, 10)`**: since the Unreleased CHANGELOG entry (commit `1c99267`, 2026-10-03), the trigger user is *not* paid by `rewardRoots`; position 0 is the trigger's nearest payable referrer. `rewardLeaf` pays the trigger user directly. The same user passed to both is paid once. `rewardRoots` reverts `EmptyPayoutChain` if there's no payable ancestor.
- `MAX_PAYOUT_LEVELS = 10`.

> **Correction vs. earlier docs.** The briefs, the parent summary and `docs/theory/graph-topologies.md` (merged 2026-10-01, PR #9) describe position 0 as the trigger user. That was true of `getPayoutChain`, and of `rewardRoots` until 2026-10-03. Current `main` pays ancestors only, so the "trigger keeps 40.25%" numbers in graph-topologies now apply to the trigger's **direct referrer**, and chain-stuffing math changes: an attacker controlling every ancestor above an honest trigger now captures 100% of a `rewardRoots` payout, not ~59.75%. The trigger's own reward, if any, must come through a separate `rewardLeaf`. Flagged for a follow-up PR to referralTree.

### Split
`RewardCalculator.calculateRewards(total, n)` caps `n` at 10 and uses hard-coded basis-point weights `[10000, 6000, 3600, 2160, 1296, 777, 466, 279, 167, 100]`, i.e. ≈0.6^k rounded down to whole bps (so it is *approximately*, not exactly, proportional to 0.6^k). Each amount is `total * w[i] / sum(w[0..n))`; the integer-division **dust goes to position 0**.

| Recipients (n) | Position 0 | Position 1 | Position 2 | Deepest |
|---|---|---|---|---|
| 1 | 100% | | | |
| 2 | 62.50% | 37.50% | | |
| 3 | 51.02% | 30.61% | 18.37% | |
| 5 | 43.37% | 26.02% | 15.61% | 5.62% |
| 10 | 40.25% | 24.15% | 14.49% | 0.40% |

At n=10, positions 8+9 together get 1.07%; positions 1–9 get 59.75%.

### Settlement, fee and authorization
- `rewardRoots` / `rewardLeaf(groupId, rewardId, user, token, totalAmount, deadline, oracle, signature)` are authorized by an **EIP-712** signature (`RewardRoots` / `RewardLeaf` typehashes) from an oracle authorized for the group. ECDSA (65-byte or EIP-2098) is tried first, then ERC-1271 if the oracle has code; no ERC-6492. The digest binds `groupId, rewardId, user, token, totalAmount, payer = msg.sender, deadline`, plus the domain separator (chain-bound).
- `rewardId` is single-use per group across both functions (the nonce).
- The graph pulls `totalAmount` from `msg.sender` and forwards it in the same call; it keeps no balance between transactions.
- **Protocol fee** comes off the top: `fee = totalAmount * feeBps / 10000` (default 0, capped at `MAX_FEE_BPS = 1000`, i.e. 10%), sent to `feeRecipient`. `distributedAmount = totalAmount - fee` is what gets split.
- Events: `RootsRewarded`, `LeafRewarded`, and `ProtocolFeeCharged` (only when fee > 0). `distributedAmount + fee == totalAmount`. Incentive Exchange indexes these; a backend log is not a reward.

### Architecture summary

| Concern | Where it lives |
|---|---|
| Edges, skiplist, counters (`registeredCount`, `skiplistedCount`) | `ReferralGraph` (on-chain, per group) |
| Who qualifies, who gets registered or skiplisted | App / oracle policy ([abuse-mitigation.md](https://github.com/MagRelo/referralTree/blob/main/docs/abuse-mitigation.md)) |
| Split math | `RewardCalculator` (pure) |
| Funds | Pulled from payer and forwarded in-call; not custodied |
| Trust anchor | Group oracle keys (sign registrations and rewards) |
| Measurement | Incentive Exchange indexing events + graph health scoring |

## Thesis: IC after transaction costs

A referral action happens only if it's incentive-compatible after transaction costs. Those costs are **Coasean**: search (finding who to refer and what's on offer), bargaining (agreeing terms), verification (did the referral and qualifying action really happen), enforcement (will I actually be paid) and coordination (multi-party splits along a chain). Gas is at most one channel.

What lowers them:
- **Agents** cut search and bargaining: they discover opportunities and act on them.
- **Public on-chain receipts** cut verification and enforcement: edges can't be rewritten, payouts are events anyone can audit.
- **Cheap L2 settlement** cuts coordination: a 10-way split in one call is routine.

The flip side: the same falling costs make **abuse** cheaper (spinning up fake paths). So the graph health service has to price farm profit against reward size and the falling cost of fake identities.

**The depth cap of 10 is engineering and optics, not a legal safe harbor.** It bounds gas and keeps tail shares from being dust; it doesn't make anything Sybil-proof (see [papers/incentive-trees-mlm.md](../papers/incentive-trees-mlm.md)) and it doesn't decide pyramid-vs-MLM classification (see [papers/mlm-pyramid-legal.md](../papers/mlm-pyramid-legal.md)).

## Positioning (short)

referralTree is an auditable multilevel **split substrate** plus an agent-readable **signal/health index**. Quest platforms own campaigns; affiliate SaaS owns ops; Deferral owns the academic citation for on-chain referral feasibility; matrix MLM contracts own the legal heat. Detail in [overviews/positioning-and-opportunities.md](../overviews/positioning-and-opportunities.md).

## Known limits
- Geometric splits are not Sybil-proof; protection is oracle policy + skiplist + health scoring.
- The oracle is the main trust point (audit PR #10, informational notes).
- Fee-on-transfer and rebasing tokens aren't specially handled (audit PR #10, lows).
