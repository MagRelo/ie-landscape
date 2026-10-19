# State of the art: solved vs open

_Reorganized from the 2026-09-10 brief; architecture claims updated to referralTree main @800da1d._

> **Framing note (2026-10-19).** The product now positions as standing terms for autonomous work (principals publish, agents pursue, onchain record + offchain judgment). The list below is still the referral-mechanism view; the positioning-level open question it adds is **making principal discretion accountable**: the site explicitly keeps payment as a social contract, so the open problem is less "remove the oracle" and more "make discretion legible" (see pitfall 1 and the new open item below).

## Relatively solved
- **Tree storage and bounded ancestor walks.** Parent pointers with a depth cap (referralTree: 10) are commodity.
- **Budget conservation.** Fixed weights with integer dust to position 0 make the split exact and deterministic.
- **Hybrid trust.** Oracle-gated edges on a public graph give apps eligibility control and give everyone auditability.
- **Authorized, replay-safe settlement.** EIP-712 oracle signatures binding payer, amount, deadline and a single-use `rewardId` (referralTree v2; automated audit found no replay issue).
- **Cheap multi-party settlement.** L2s make a 10-way split per event routine.
- **Shallow fee-affiliate programs and web2 referral science.** "Should we run a referral program and whom do we reward" is answered (marketing-science papers in [attribution-shapley](../papers/attribution-shapley.md)).

## Still open
- **Sybil-proof multilevel splits on-chain.** Theory exists (Drucker–Fleischer; Chen et al.; Zhang–Tang) but production contracts, including referralTree, use plain geometric decay.
- **Trust-minimized eligibility.** Oracle policy works until the oracle is wrong or captured. Attestations/ZK for "real user, real qualifying action" are open.
- **Early-position inequality.** Geometric splits favor ancestors who sit above many triggers; few deployable fairness knobs (Lv–Moscibroda).
- **Portable referrer reputation.** Graphs are siloed per `groupId`; Fuul's global affiliate codes and ERC-8021 builder codes are partial steps.
- **Outcome-based credit with public rules.** Pump.fun moved to follower-profit credit but kept the metric secret; nobody has outcome-based credit with a verifiable rule at scale.
- **Legal classification.** Funding source and recruitment emphasis decide it, not depth (Vander Nat & Keep). The depth cap of 10 is not a safe harbor.
- **Accountable discretion / two-way reputation.** The site claims trust develops through a visible history of what was offered, what happened and what was paid, inspectable by both principals and agents. There's no standard yet for a principal's payment-behavior record (missed payouts, skiplist reasons) that agents can rely on; the record shows a missing payment, not whether it was justified.
- **Peer-reviewed on-chain multilevel referral work** remains thin (Deferral is the standout).

## Pitfalls
1. Calling it "decentralized" or "trustless" while the oracle owns edges. The current site avoids this: it says the principal retains discretion and payment is a social contract. Keep it that way.
2. Assuming a depth cap means Sybil-proof.
3. Paying on signups instead of verifiable outcomes.
4. Ignoring payout-by-generation inequality.
5. Omitting reward events, which makes the economy invisible to indexers and agents.
