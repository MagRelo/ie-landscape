# Positioning and opportunities

## One-line position
**LightForest is "Work for Agents": create an opportunity, let agents get to work.** principals publish standing terms (what they value, how contributions are judged, how they pay), agents pursue them independently, and onchain records plus offchain judgment make the relationship accountable without negotiating each task. referralTree supplies the first rail: auditable multilevel edges, oracle-signed payouts and public receipts. Graph health is part of each project's record, not the headline. _(Synced to `MagRelo/ie` @ `e88842e`, 2026-10-19.)_

**Target user:** a principal (business) with margin to share for work it can't cost-effectively commission one task at a time (first case: Play the Cut sharing contest margin for player growth), and the agents deciding whether its terms and payment history are worth working for.

**What changed from the 2026-10-12 framing:** the old line was "split substrate + agent-readable graph health index." The new line leads with the principal–agent arrangement (terms before work, social contract, visible record, autonomous business models). Referral payouts and health scoring are now means, not the product.

| Comparator | Their center of gravity | Our stance (positioning as of 2026-10-19) |
|---|---|---|
| Fuul | Multilevel affiliate SaaS, platform-run attribution | Compete on verifiability and open math; learn from their cross-project codes |
| Layer3 / Galxe | Quests and distribution | Integrate: their verified actions can trigger `rewardRoots` |
| Split402 / AREF / x402 builder codes | Agent attribution plumbing | Be the multilevel payout + health layer that consumes their attribution evidence |
| Pump.fun / SayGM / Xyper | Live incentive programs | Contrast: public rule vs. secret metric; multilevel vs. pro-rata single level; revenue-funded vs. recruit-a-team |
| Deferral / ThunderCore | Research / library contracts | Cite; we're the production-shaped, multi-tenant version |

## Opportunities
1. **Sybil-aware calculator variants.** `setRewardCalculator` already allows swapping. Implement one Drucker–Fleischer-style and one finder-heavy (Chen et al.) rule; compare attack ROI in `simulation/`.
2. **Graph health as evidence in the project record.** Ship SybilRank-style ranking, FRAUDAR density and CopyCatch lockstep signals as Exchange scores and skiplist recommendations (human/oracle confirms). See [threat-topology-map](threat-topology-map.md).
3. **Outcome-gated settlement with public rules.** The Pump.fun contrast: pay on verifiable downstream outcomes, publish the rule. In the new language this is "terms before commitment": the published terms *are* the product.
4. **Agent attribution bridge.** Accept ERC-8021 builder codes / x402 facilitator metadata (PR #3666) or AREF proofs as evidence an oracle signs into `rewardRoots`.
5. **Two-way track record.** The site promises agents can inspect a principal's payment behavior (and vice versa). Per-project settlement rate, skiplist rate, missed/late payouts, and agent leaderboard history are the concrete form of that.
6. **Research instrument.** Publish payout-by-generation, branching and settlement-rate histograms per group; cite Ma et al. 2026 for the welfare framing.
7. **Legal-econ checklist.** Funding-source disclosure per listing; no buy-ins; depth cap described as engineering, not a safe harbor.
8. **Sponsor liability / vouching.** Fix the skiplist perverse incentive; adopt PoH/Ethos patterns (fractional parent penalty, bond window, self-police credit). See [referrer-accountability-design](referrer-accountability-design.md).

## Near-term follow-ups
- Update `docs/theory/graph-topologies.md` for the 2026-10-03 ancestors-only `rewardRoots` change.
- Decide whether `rewardRoots` and `rewardLeaf` should be signed together for the same event, so the trigger's share isn't forgotten.
