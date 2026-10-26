# Attribution and Shapley-style credit

How to divide credit for an outcome among multiple contributors. Geometric decay is one heuristic; Shapley values and data-driven multi-touch attribution are the principled alternatives.

---

### A Value for n-Person Games
- **Citation:** L. S. Shapley. *A Value for n-Person Games.* In H. W. Kuhn, A. W. Tucker (eds.), Contributions to the Theory of Games II (Annals of Mathematics Studies 28), Princeton University Press, 1953, pp. 307–317.
- **Link:** <https://doi.org/10.1515/9781400881970-018> (verified via Crossref)
- **Summary:** Defines the Shapley value: the unique allocation of a coalition's worth satisfying efficiency, symmetry, null-player and additivity, computed as each player's average marginal contribution over all orderings.
- **Implication for referralTree:** The yardstick for "fair" credit. On a pure chain where each link is necessary, Shapley gives equal shares, not geometric ones, so the 0.6 decay is a deliberate design choice (rewarding proximity) and should be described that way.

### Data-driven Multi-touch Attribution Models
- **Citation:** X. Shao, L. Li. Proc. 17th ACM SIGKDD (KDD '11), 2011.
- **Link:** <https://doi.org/10.1145/2020408.2020453> (verified via Crossref)
- **Summary:** Proposes data-driven models (bagged logistic regression and a probabilistic model) that assign conversion credit across multiple ad touchpoints, replacing last-touch rules, and evaluates stability and accuracy on real ad data.
- **Implication for referralTree:** Web2 attribution already moved past fixed rules to learned credit. A future calculator could learn per-group decay from settlement data; LightForest can publish the observed payout-by-generation curve as a starting point.

### Causally Motivated Attribution for Online Advertising
- **Citation:** B. Dalessandro, C. Perlich, O. Stitelman, F. Provost. Proc. Sixth International Workshop on Data Mining for Online Advertising and Internet Economy (ADKDD '12), 2012.
- **Link:** <https://doi.org/10.1145/2351356.2351363> (verified via Crossref)
- **Summary:** Frames attribution as a causal question (what did each channel cause?) and proposes a Shapley-value-based attribution method grounded in that framing.
- **Implication for referralTree:** Separates "on the path" from "caused the outcome". LightForest's research angle: measure incremental lift per generation instead of assuming it.

### Marketing-science referral program papers (context)
Verified via Crossref; shorter notes because they're about program design, not tree math.
- Biyalogorsky, Gerstner, Libai. *Customer Referral Management: Optimal Reward Programs.* Marketing Science 20(1), 2001. <https://doi.org/10.1287/mksc.20.1.82.10195>: when to reward referrers vs. use price cuts.
- Schmitt, Skiera, Van den Bulte. *Referral Programs and Customer Value.* Journal of Marketing 75(1), 2011. <https://doi.org/10.1509/jm.75.1.46>: referred customers are more valuable and loyal.
- Kumar, Petersen, Leone. *Driving Profitability by Encouraging Customer Referrals: Who, When, and How.* Journal of Marketing 74(5), 2010. <https://doi.org/10.1509/jmkg.74.5.001>: which customers to target for referral.
- Leduc, Jackson, Johari. *Pricing and Referrals in Diffusion on Networks.* Games and Economic Behavior 104, 2017. <https://doi.org/10.1016/j.geb.2017.05.011>: optimal referral incentives vs. pricing in network diffusion.
- **Implication for referralTree:** Guidance on eligibility and two-sided rewards; none of it addresses multilevel Sybil resistance.

## Recent (2026)

### Paying for Information, Not for Clicks: A Block-Level Publisher Content Marketplace for AI Answers
- **Citation:** M. Mobius, L. Braghieri, S. Eichmeyer, D. G. Goldstein, N. Immorlica, O. Kiss, R. Levy, B. Lucier, I. Mahajan, J. Qiu, T. Rosenblat, D. M. Rothschild, A. Sari, A. Slivkins, C. Watson. *Paying for Information, Not for Clicks: A Block-Level Publisher Content Marketplace for AI Answers.* arXiv:2610.30324 (v1, 21 Oct 2026).
- **Link:** <https://arxiv.org/abs/2610.30324> (verified on arXiv)
- **Summary:** Proposes paying publishers for the distinct facts ("lego blocks") used in AI-generated answers. Three payment rules (equal sharing among everyone who reported a block, rewarding whoever reported it first, and rewarding indispensable contributions) are each written as a Shapley-value variant. On answers to 1,974 search queries about one heavily covered news episode, the rules give nearly identical allocations when attribution only sees the articles retrieved for each query, but diverge once a global index of the whole corpus reveals overlap: premium publishers get 42% of value under equal sharing vs 46–50% under first-publication (authors' figures).
- **Implication for referralTree:** "Reward whoever got there first" is a legitimate Shapley-family rule, which is a principled way to describe the early-mover advantage Matt wants to keep. Their key finding is that the choice of rule only matters, and can only be audited, when there is a shared global record of who contributed what and when; referralTree's on-chain edges with timestamps are exactly that record, so say so in positioning.
