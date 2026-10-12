# Positioning and opportunities

## One-line position
referralTree ships the auditable multilevel **split substrate** (on-chain edges, oracle-signed atomic payouts, public receipts) and Incentive Exchange ships the agent-readable **graph health index** on top. Platforms own campaigns, affiliate SaaS owns ops, Deferral owns the academic citation, matrix MLMs own the legal heat.

| Comparator | Their center of gravity | Our stance |
|---|---|---|
| Fuul | Multilevel affiliate SaaS, platform-run attribution | Compete on verifiability and open math; learn from their cross-project codes |
| Layer3 / Galxe | Quests and distribution | Integrate: their verified actions can trigger `rewardRoots` |
| Split402 / AREF / x402 builder codes | Agent attribution plumbing | Be the multilevel payout + health layer that consumes their attribution evidence |
| Pump.fun / SayGM / Xyper | Live incentive programs | Contrast: public rule vs. secret metric; multilevel vs. pro-rata single level; revenue-funded vs. recruit-a-team |
| Deferral / ThunderCore | Research / library contracts | Cite; we're the production-shaped, multi-tenant version |

## Opportunities
1. **Sybil-aware calculator variants.** `setRewardCalculator` already allows swapping. Implement one Drucker–Fleischer-style and one finder-heavy (Chen et al.) rule; compare attack ROI in `simulation/`.
2. **Graph health as a product.** Ship SybilRank-style ranking, FRAUDAR density and CopyCatch lockstep signals as Exchange scores and skiplist recommendations (human/oracle confirms). See [threat-topology-map](threat-topology-map.md).
3. **Outcome-gated settlement with public rules.** The Pump.fun contrast: pay on verifiable downstream outcomes, publish the rule. This is the IC-after-transaction-costs pitch in one sentence.
4. **Agent attribution bridge.** Accept ERC-8021 builder codes / x402 facilitator metadata (PR #3666) or AREF proofs as evidence an oracle signs into `rewardRoots`.
5. **Research instrument.** Publish payout-by-generation, branching and settlement-rate histograms per group; cite Ma et al. 2026 for the welfare framing.
6. **Legal-econ checklist.** Funding-source disclosure per listing; no buy-ins; depth cap described as engineering, not a safe harbor.

## Near-term follow-ups
- Update `docs/theory/graph-topologies.md` for the 2026-10-03 ancestors-only `rewardRoots` change.
- Decide whether `rewardRoots` and `rewardLeaf` should be signed together for the same event, so the trigger's share isn't forgotten.
