# Query incentive networks and branching

Paying intermediaries to forward a query (or task) until someone with the answer is found. Same DNA as geometric referral (path-shared reward) but the path is built during the search instead of reused from a standing tree.

**Category takeaway:** recursive splits work when the outcome is verifiable and the pot is real; branching factor matters (below ~2 effective offspring, required rewards blow up); Sybil-proof variants push reward toward the finder and their direct parent.

---

### Query Incentive Networks
- **Citation:** J. Kleinberg, P. Raghavan. *Query Incentive Networks.* 46th IEEE Symposium on Foundations of Computer Science (FOCS '05), 2005.
- **Links:** <https://doi.org/10.1109/sfcs.2005.63> (verified via Crossref); PDF <https://www.cs.cornell.edu/home/kleinber/focs05-qin.pdf>
- **Summary:** A root offers a reward for an answer; each node lacking it forwards a smaller offer to its children and keeps the difference. Models this on random branching trees and studies equilibrium reward needed as a function of answer rarity. Finds a threshold in the branching factor: around branching 2 the required reward changes sharply (exponential vs. polynomial/logarithmic behavior in rarity).
- **Implication for referralTree:** The LightForest catalog / graph health should instrument **effective branching** per tree (bushy vs. chainy) because it predicts whether depth-based rewards can propagate at all. Fits the "principal publishes terms, agents pursue" framing: an opportunity propagating through agents is a query incentive network.

### Time-Critical Social Mobilization
- **Citation:** G. Pickard, W. Pan, I. Rahwan, M. Cebrian, R. Crane, A. Madan, A. Pentland. *Time-Critical Social Mobilization.* Science 334(6055), 2011, pp. 509–512.
- **Link:** <https://doi.org/10.1126/science.1205869> (verified via Crossref)
- **Summary:** Analyzes the MIT team's winning strategy in the 2009 DARPA Network Challenge (find 10 red weather balloons across the US). The team used a recursive incentive scheme that paid the finder and, with halving amounts, each person up the recruitment chain, and found all balloons in under nine hours. The paper argues the recursive split rewards both search and recruitment.
- **Implication for referralTree:** Real-world proof that geometric path credit mobilizes recruitment fast when the qualifying event is verifiable. Also the canonical example where Sybils are less of a problem because payout is tied to a hard-to-fake outcome; tie `rewardRoots` to real outcomes, not signups.

### On Bitcoin and Red Balloons
- **Citation:** M. Babaioff, S. Dobzinski, S. Oren, A. Zohar. *On Bitcoin and Red Balloons.* Proc. 13th ACM EC '12, 2012. (Short version: ACM SIGecom Exchanges 10(3), 2011, <https://doi.org/10.1145/2325702.2325704>.)
- **Link:** <https://doi.org/10.1145/2229012.2229022> (verified via Crossref)
- **Summary:** Observes that Bitcoin nodes have an incentive *not* to forward transactions (forwarding creates competitors for the fee). Proposes reward schemes that pay nodes along the propagation path, in the spirit of the red-balloon scheme, and shows such schemes can be made Sybil-proof and incentivize propagation with only a modest reward.
- **Implication for referralTree:** A Sybil-proof path-reward design in an adversarial, pseudonymous setting, closer to on-chain conditions than social-network papers. Worth mining for a calculator variant.

### Sybil-proof Mechanisms in Query Incentive Networks
- **Citation:** W. Chen, Y. Wang, D. Yu, L. Zhang. *Sybil-proof Mechanisms in Query Incentive Networks.* Proc. 14th ACM EC '13, 2013.
- **Link:** <https://doi.org/10.1145/2482540.2482588> (verified via Crossref)
- **Summary:** Shows that in query incentive networks, Sybil-proofness forces strong restrictions on reward rules and characterizes Sybil-proof mechanisms, which concentrate reward near the answer holder (e.g., the finder and the direct referrer) rather than spreading geometrically up the path.
- **Implication for referralTree:** Argues for offering a "finder-heavy / direct-referral" calculator option beside the geometric one for groups that can't police Sybils well.

### Collusion-Proof and Sybil-Proof Reward Mechanisms for Query Incentive Networks
- **Citation:** Y. Zhang, P. Tang. *Collusion-Proof and Sybil-Proof Reward Mechanisms for Query Incentive Networks.* Proc. AAAI Conference on Artificial Intelligence 37(5), 2023.
- **Link:** <https://doi.org/10.1609/aaai.v37i5.25730> (verified via Crossref). arXiv:2302.06061 carried over from earlier briefs **(unverified this pass; arXiv API rate-limited)**.
- **Summary:** Designs reward mechanisms for query incentive networks that are simultaneously Sybil-proof and collusion-proof, under their model, and characterizes the trade-offs. Note: an earlier brief filed this under MLM; it is a QIN paper.
- **Implication for referralTree:** The most recent formal target for a "SP + CP" calculator. Collusion-proofness matters because a real referral farm is often several cooperating people, not one wallet.
