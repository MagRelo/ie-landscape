# Incentive trees and MLM mechanisms

How to pay people along a recruitment tree, and what properties (Sybil-proofness, fairness, profitability) are achievable. This is the core theory under `RewardCalculator`.

**Category takeaway:** geometric decay along the chain is the natural family, and it is *not* Sybil-proof by itself. The Sybil-proof constructions change the split rule, not just the depth cap.

---

### Mechanisms for Multi-Level Marketing
- **Citation:** Y. Emek, R. Karidi, M. Tennenholtz, A. Zohar. *Mechanisms for Multi-Level Marketing.* Proc. 12th ACM Conference on Electronic Commerce (EC '11), 2011, pp. 209–218.
- **Link:** <https://doi.org/10.1145/1993574.1993606> (verified via Crossref)
- **Summary:** Founding CS treatment of MLM reward schemes as mechanisms on a recruitment tree. Defines desirable properties (e.g., incentive to recruit, budget constraints, resistance to Sybil/fake-identity manipulation) and studies geometric-style mechanisms that pay ancestors a decaying share. Shows tension between these properties and characterizes what simple mechanism families can and cannot satisfy.
- **Implication for referralTree:** `RewardCalculator`'s ≈0.6^k split is squarely in this family. Cite it as the reason the split is "attractive but manipulable", and never market the 0.6/10 rule as Sybil-proof.

### Simpler Sybil-Proof Mechanisms for Multi-Level Marketing
- **Citation:** F. A. Drucker, L. K. Fleischer. *Simpler Sybil-Proof Mechanisms for Multi-Level Marketing.* Proc. 13th ACM EC '12, 2012.
- **Link:** <https://doi.org/10.1145/2229012.2229046> (verified via Crossref)
- **Summary:** Builds on Emek et al. and gives simpler reward mechanisms that are Sybil-proof under their model, i.e., an agent can't gain by splitting into multiple identities in the tree, while keeping other desirable properties. The constructions modify how credit is computed along the chain rather than relying on a pure fixed geometric decay.
- **Implication for referralTree:** The concrete path to a Sybil-aware `RewardCalculator` variant. Prototype one of these rules as an alternative calculator behind `setRewardCalculator` and compare attack ROI in the simulation suite.

### Fair and Resilient Incentive Tree Mechanisms
- **Citation:** Y. Lv, T. Moscibroda. *Fair and Resilient Incentive Tree Mechanisms.* Proc. ACM PODC 2013; extended in *Distributed Computing* 29 (2016, online 2015).
- **Links:** PODC <https://doi.org/10.1145/2484239.2484252>; journal <https://doi.org/10.1007/s00446-015-0250-y> (both verified via Crossref)
- **Summary:** Studies incentive trees (crowdsourcing/referral trees where participants are rewarded for their own contribution and that of people they recruited). Formalizes fairness-type properties (rewards tied to contribution) alongside Sybil- and collusion-resilience, proves which combinations are impossible, and gives mechanisms that achieve the feasible combinations.
- **Implication for referralTree:** Gives the vocabulary for the early-position advantage problem (fairness) and for collusion (multiple real people coordinating), not just single-actor Sybils. Use it to frame which properties referralTree deliberately gives up.

### Deferral: on the Feasibility of High-Volume Blockchain-based Referral Systems
- **Citation:** T. Boner, B. Rodrigues, T. Bocek, B. Stiller. *Deferral: on the Feasibility of High-Volume Blockchain-based Referral Systems.* 5th Conf. on Blockchain Research & Applications for Innovative Networks and Services (BRAINS), IEEE, 2023. Based on Boner's UZH MSc thesis (2023).
- **Links:** <https://doi.org/10.1109/brains59668.2023.10316807> (verified via Crossref); code <https://github.com/dydent/Deferral>. Thesis DOI `10.5167/uzh-255750` carried over from earlier briefs **(unverified: did not resolve in Crossref this pass)**.
- **Summary:** Implements a ladder of on-chain referral contracts (from a simple payment transmitter to quantity/value evaluators with multilevel payout) and measures gas/fiat cost to assess whether high-volume on-chain referral is feasible. Contracts custody funds until a referral process completes; multilevel payout is typically an equal split up to a max level.
- **Implication for referralTree:** The closest published on-chain peer. referralTree differs by factoring out eligibility (oracle policy), using a geometric split, and not custodying funds between transactions. See [competitors/onchain-referral-infra.md](../competitors/onchain-referral-infra.md).

### An economic model of multi-level marketing
- **Citation:** Y. Reingewertz. *An economic model of multi-level marketing.* PLOS ONE 16(7), 2021.
- **Link:** <https://doi.org/10.1371/journal.pone.0253700> (verified via Crossref)
- **Summary:** Economic model of MLM participation and earnings, examining how recruitment-based compensation shapes outcomes for participants at different positions. Useful empirical/theoretical counterweight to purely mechanism-design treatments.
- **Implication for referralTree:** Supports the early-position-advantage concern and the need for payout-by-generation metrics in LightForest project records.
