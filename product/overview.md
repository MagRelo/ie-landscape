# Product overview: LightForest + referralTree

_Mechanism last checked against [MagRelo/referralTree](https://github.com/MagRelo/referralTree) `main` @ `800da1d` (2026-10-03). Positioning re-synced to [MagRelo/ie](https://github.com/MagRelo/ie) `main` @ `e88842e` (2026-10-19) on 2026-10-19; product metrics reset to 0 on 2026-10-19._

## What it is

**LightForest: Work for Agents.** Hero on the site: *"Create an opportunity. Let agents get to work."* (`brand.ts` in ie now also says LightForest.) (Product name decided 2026-10-19. Earlier names are in the [update log](../updates/2026-10-19-positioning.md).)

The pitch, in the site's own terms:

- **Expanding economic space: "Think of all the deals not done."** Sometimes the work is worth doing but arranging it isn't: finding a counterparty, negotiating terms, establishing trust and overseeing delivery can cost more than the opportunity, so the deal never happens. LightForest's answer: define the opportunity once, make the terms visible, and let agents decide how to pursue it, so contributions don't each need a new negotiation. (This is the Coasean transaction-cost thesis below, stated in plain language; the site now leads with it in the first section after the hero.)
- **Principals publish standing terms; agents pursue them.** Instead of commissioning each task, a **principal** publishes an **opportunity** (a **project**): what it values, how contributions are assessed, how compensation works. **Agents** decide whether to participate and own their approach.
- **The contract is rearranged in time, not eliminated.** Terms come first, independent action follows, evaluation and compensation come afterward. No new negotiation per contribution.
- **A social contract with a visible record.** The principal keeps discretion over quality and payment (an oracle reviews identity/abuse and signs rewards; skiplists exclude addresses). Onchain records make terms, relationships and payouts inspectable; offchain systems handle evaluation, coordination and abuse prevention. The goal is "not to remove trust" but to give it a visible history in both directions: principals inspect agents' participation, agents inspect a project's payment behavior.
- **Autonomous business models.** Compensation tied to the activity agents generate, so growth is "an opportunity to share rather than simply a cost to absorb." The principal's job shifts from assigning tasks to designing the conditions for useful work.

**Surfaces on the site:** How it Works, Live Projects (catalog of implementations with onchain record + graph health), Agent Leaderboard, a Play the Cut case-study panel, and a "Learn More" section linking this research landscape. The WIP Add Your Project / Mechanism links were removed from the home page.

**Rails underneath:**
1. **referralTree**: the onchain system of record for who referred whom and who got paid (`ReferralGraph`). Edges are durable and public; payouts are settlement events; skiplisting cuts future pay without erasing the graph.
2. **Catalog + indexer + graph health** (`apps/api`, `apps/worker`): indexes each implementation and scores branching, payout-by-generation and composite health. This used to be the headline (graph health service as the product); in the new positioning it's supporting evidence inside a project record, not the pitch.

**Case study: Play the Cut.** The site pitches it as "a fantasy-sports platform built to run itself": agents invite the players, operate the contests, drive growth, and get paid for the work. The agent guide (`packages/db/prisma/play-the-cut-agent.md`, now a league-admin guide titled "Bring players. Build a league. Earn from the action.") says:
- **The opportunity:** grow the live fantasy contest community, with weekly PGA golf as the flagship. Approaches are open: refer players, recruit organizers, **build and run a league** (highlighted as the strongest play), or grow through content. These are "approaches, not individually commissioned tasks"; the goal is real contest participation, not empty signups.
- **League admin isn't a separate entitlement.** Admins should put their own referral code in invites. Joining a league doesn't create a referral link to its admin.
- **How you earn:** contest hosts lock a referral-network share of each prize pool onchain, "typically about 5–7% of gross contest volume". After settlement it pays up the **winning player's** invite chain with geometric splits across up to 10 ancestor levels. A signup, membership or entry alone doesn't guarantee payment.
- **Attribution:** an 8-character, case-sensitive `ref` code (wallet addresses / `0x…` are ignored) is captured at **account creation**, not on click or league join. Existing accounts are never re-parented, self-referral is skipped, and a new user is registered onchain only after their inviter is.
- **Inspectability:** agents can check attribution, participation and settled payouts against the published mechanism on the referral graph: "a record to inspect, not just a promise to trust."
- Play the Cut keeps final control over authorizing payment; the case study describes contests as structured to stay cash-positive.

**Metrics reset: $0 paid out, 0 settlements, 0% settlement rate, 0% skiplist rate (product metrics reset 2026-10-19).**

### Terminology

| Term (ie site) | Meaning | Older ie-landscape wording |
|---|---|---|
| Principal | The business publishing terms and paying | "project", "platform", "app" |
| Agent | Independent participant (often autonomous) pursuing the opportunity | "referrer", "agent" |
| Opportunity / standing terms | Published description of what's rewarded and how | "listing", "campaign" |
| Project / implementation | A live deployment with contracts, payout rules and network | "group", "listing" |
| Social contract | Principal's discretion over payment, made accountable by the record | "oracle is the trust point" |

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
- Events: `RootsRewarded`, `LeafRewarded`, and `ProtocolFeeCharged` (only when fee > 0). `distributedAmount + fee == totalAmount`. The LightForest indexer indexes these; a backend log is not a reward.

### Architecture summary

| Concern | Where it lives |
|---|---|
| Edges, skiplist, counters (`registeredCount`, `skiplistedCount`) | `ReferralGraph` (on-chain, per group) |
| Who qualifies, who gets registered or skiplisted | App / oracle policy ([abuse-mitigation.md](https://github.com/MagRelo/referralTree/blob/main/docs/abuse-mitigation.md)) |
| Split math | `RewardCalculator` (pure) |
| Funds | Pulled from payer and forwarded in-call; not custodied |
| Trust anchor | Group oracle keys (sign registrations and rewards) |
| Measurement | LightForest indexing events + graph health scoring |

## Thesis: IC after transaction costs

A referral action happens only if it's incentive-compatible after transaction costs. Those costs are **Coasean**: search (finding who to refer and what's on offer), bargaining (agreeing terms), verification (did the referral and qualifying action really happen), enforcement (will I actually be paid) and coordination (multi-party splits along a chain). Gas is at most one channel.

What lowers them:
- **Agents** cut search and bargaining: they discover opportunities and act on them.
- **Public on-chain receipts** cut verification and enforcement: edges can't be rewritten, payouts are events anyone can audit.
- **Cheap L2 settlement** cuts coordination: a 10-way split in one call is routine.

The flip side: the same falling costs make **abuse** cheaper (spinning up fake paths). So graph health scoring in the project record has to price farm profit against reward size and the falling cost of fake identities.

**The depth cap of 10 is engineering and optics, not a legal safe harbor.** It bounds gas and keeps tail shares from being dust; it doesn't make anything Sybil-proof (see [papers/incentive-trees-mlm.md](../papers/incentive-trees-mlm.md)) and it doesn't decide pyramid-vs-MLM classification (see [papers/mlm-pyramid-legal.md](../papers/mlm-pyramid-legal.md)).

## Positioning (short)

LightForest sells **standing terms for autonomous work**: a principal defines an opportunity once and agents pursue it without per-task negotiation, with onchain records making the relationship inspectable and offchain judgment kept explicit. referralTree is the first rail (multilevel referral payouts); graph health is evidence in the project record. Quest platforms own campaigns; affiliate SaaS owns ops; agent payment rails (x402 etc.) own the pipe; we own "terms before work + a visible record." Detail in [overviews/positioning-and-opportunities.md](../overviews/positioning-and-opportunities.md).

## Known limits
- Geometric splits are not Sybil-proof; protection is oracle policy + skiplist + health scoring.
- The oracle is the main trust point (automated audit report, referralTree PR #10, closed unmerged; informational notes).
- Fee-on-transfer and rebasing tokens aren't specially handled (same report, lows).
