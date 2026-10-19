# Referrer accountability and social collateral

Making a referrer answer for the people they bring in: joint liability in economics, invitation-based meta-reputation in CS, and production systems that penalize sponsors. Scope is *vouching / sponsorship integrity* (fraud, Sybil, duplicate), not performance management of a downline.

**Category takeaway:** the idea is established. Economics shows that tying a referrer's payoff to referee conduct cuts default mainly through *enforcement*, not screening (Bryan–Karlan–Zinman). CS has a direct blueprint in "Trust by Association." Nearly every live system punishes **only the direct sponsor**, uses a **smaller penalty** than the offender gets, and lets the sponsor **disavow before resolution**. Recursive, decaying penalties up the tree have almost no production precedent. For referralTree today, skiplisting a bad node *rewards* its referrer by moving ancestors closer — sponsor accountability is needed just to remove that perverse incentive. See [overviews/referrer-accountability-design.md](../overviews/referrer-accountability-design.md).

---

## A. Social collateral and joint liability (economics)

### Trust and Social Collateral
- **Citation:** D. Karlan, M. Mobius, T. Rosenblat, A. Szeidl. *Trust and Social Collateral.* Quarterly Journal of Economics 124(3), 2009, pp. 1307–1361.
- **Link:** <https://ideas.repec.org/a/oup/qjecon/v124y2009i3p1307-1361..html> (verified via RePEc)
- **Summary:** Network links act as collateral: A can borrow from B up to the value of the paths between them that an intermediary would lose. Their job-referral application shows trusted recommenders reduce information asymmetry about candidates.
- **Implication for referralTree:** the referrer edge is collateral. What a referrer can lose should scale with what their referees can extract, so a cap on invites or exposure per referrer matters.

### Group Lending, Repayment Incentives and Social Collateral
- **Citation:** T. Besley, S. Coate. *Group Lending, Repayment Incentives and Social Collateral.* Journal of Development Economics 46(1), 1995, pp. 1–18.
- **Link:** <https://doi.org/10.1016/0304-3878(94)00045-e> (verified; citation confirmed via references)
- **Summary:** Joint liability can raise repayment through social sanctions. It can also lower repayment when the whole group defaults together ("if one defaults, why should I pay?").
- **Implication for referralTree:** group-wide penalties can trigger collective defection. Keep the penalty narrow.

### Group lending, local information and peer selection
- **Citation:** M. Ghatak. *Group lending, local information and peer selection.* Journal of Development Economics 60(1), 1999.
- **Link:** (unverified — citation from memory; check before quoting)
- **Summary:** Joint liability makes borrowers sort by risk, because safe types match with safe types. **(unverified)**
- **Implication for referralTree:** sponsor liability selects *who refers whom*. Expect honest users to refer fewer, closer contacts. Good for quality, bad for growth.

### Peer Monitoring and Credit Markets
- **Citation:** J. E. Stiglitz. *Peer Monitoring and Credit Markets.* World Bank Economic Review 4(3), 1990.
- **Link:** (unverified — citation from memory; check before quoting)
- **Summary:** Joint liability shifts monitoring from the lender to peers, at the cost of putting risk on them. **(unverified)**
- **Implication for referralTree:** the oracle can outsource monitoring to referrers, but referrers carry risk they can't diversify. Bound it.

### Referrals: Peer Screening and Enforcement in a Consumer Credit Field Experiment
- **Citation:** G. Bryan, D. Karlan, J. Zinman. *Referrals: Peer Screening and Enforcement in a Consumer Credit Field Experiment.* NBER Working Paper w17883; published AEJ: Micro 2015 **(journal details unverified)**.
- **Link:** <https://www.nber.org/system/files/working_papers/w17883/w17883.pdf> (verified via NBER)
- **Summary:** A South African lender's randomized experiment paid an R100 (~$12) referral bonus contingent on repayment. Default fell roughly from 20% to 10% through *enforcement*. They found no evidence that referrers *screened* better.
- **Implication for referralTree:** the strongest effect comes when the referrer's payoff stays at risk *after* onboarding (ongoing liability). Liability only at join time does much less. That supports a bonding period.

---

## B. Referral hiring

### Social Networks and Labor-Market Outcomes
- **Citation:** J. D. Montgomery. *Social Networks and Labor-Market Outcomes: Toward an Economic Analysis.* American Economic Review 81(5), 1991.
- **Link:** (unverified — citation from memory; check before quoting)
- **Summary:** Employers use referrals because people refer people like themselves. **(unverified)**
- **Implication for referralTree:** homophily is what makes accountability informative. It is also how cliques form, the "dense clump" topology in graph-topologies.md.

### Who Gets the Job Referral?
- **Citation:** L. Beaman, J. Magruder. *Who Gets the Job Referral? Evidence from a Social Networks Experiment.* American Economic Review 102(7), 2012.
- **Link:** <https://doi.org/10.1257/aer.102.7.3574> (verified; citation confirmed)
- **Summary:** In a Kolkata experiment, referrers chose more able referees when *their own pay depended on the referee's performance*, and chose friends or relatives when it didn't.
- **Implication for referralTree:** tie referrer upside (`rewardRoots` share) to referee conduct, or referrals will follow friendship rather than quality.

---

## C. Invitation-based reputation and Sybil defense (CS)

### Trust by Association: A Meta-Reputation System for P2P Networks
- **Citation:** M. Kellett, T. Tran, M. Li. *Trust by Association: A Meta-Reputation System for Trustworthy Collaborative Computing.* Computational Intelligence, 2010 **(venue details unverified)**.
- **Link:** <https://www.site.uottawa.ca/~nelkadri/CSI5389/Papers/104-MKellett_TTran_MLi_CI2010.pdf> (verified PDF)
- **Summary:** Closest academic match to sponsor liability in invite trees. In invite-only networks, a peer's trust depends on its own behaviour and its invitees', which gives inviters an incentive to *expel* bad invitees. Simulations show it works alongside a base trust metric.
- **Implication for referralTree:** a direct blueprint. Make the inviter's standing a function of the subtree, and let inviters skiplist their own invitees. Self-policing earns credit.

### Enforcing Trust Accountability with Backward Propagation (RepuLink)
- **Citation:** Wenbo Wu, George Konstantinidis (University of Southampton). *Enforcing Trust Accountability with Backward Propagation.* KDD '26 (32nd ACM SIGKDD), Jeju, Aug 9–13, 2026, Vol. 2, pp. 5476–5487. Published online Aug 8, 2026. DOI 10.1145/3770855.3817611. CC-BY 4.0. Metadata verified via Crossref; full text read from arXiv.
- **Link:** <https://dl.acm.org/doi/10.1145/3770855.3817611> (ACM, behind Cloudflare for scripted fetch) · <https://arxiv.org/abs/2606.08851> (open copy, verified)
- **Mechanism:** Two layers: an endorsement network E (weighted vouches) and an interaction-feedback network T (ratings −10..10). Reputation is R(t+1) = (αTᵀ + (1−α)Eᵀ)R(t), clipped at zero and normalized (EigenTrust-like).
  - **Cold start:** a new node starts at (1−α)·Σ E_ij·R_i over its endorsers.
  - **BEPP (penalty):** each node gets a penalty signal g(N_j) = e^(−βN_j) from its negative feedback. The penalty flows upstream to endorsers, π = Σ_k γ^k E^k (1−g(N)) = γE(I−γE)⁻¹(1−g(N)), with γ ∈ (0,1). Direct endorsers get the most. It stops at tolerance δ or a max hop bound K.
  - **BERP (reward):** the mirror image, with r(P_j) = 2 − e^(−λP_j); ρ = Σ_k γ^k E^k (r(P)−1).
  - **Update:** R ← R − π + ρ. Each edge is rescaled, E_ij ← E_ij·g(N_j)·r(P_j), then renormalized, so a vouch for a bad node weakens automatically.
  - **Departure:** the identity is deactivated, not deleted, and its endorsements are revoked. Rejoining relinks the old identity, which blocks whitewashing.
- **Results:** Bitcoin-OTC (5,881 nodes / 35,592 edges) and Bitcoin-Alpha (3,783 / 24,186).
  - **Interaction layer only:** AUC 0.83/0.84, Precision@K 0.75/0.77, Kendall τ 0.46/0.47, Spearman 0.56/0.58.
  - **Full two-layer model:** AUC 0.81/0.85, Kendall τ 0.44/0.49, Spearman 0.53/0.60.
  - Beats 5 baselines, by about 7.8–8.5 points in peak AUC over the strongest. Converges in ~45 iterations to 1e-6.
  - Ablation: BEPP makes targeted corrections to a few nodes; BERP drives broad rank reordering. In a 7-node toy case, the endorser of a bad node falls to ≈0.60.
- **Caveats:**
  - The endorsement layer is **synthetic**: it maps users onto the Epinions trust graph, with every edge set to weight 1.
  - Ranking quality only. Nothing is staked and no money moves.
  - Assumes many endorsers per node, whereas referralTree gives each node a single parent.
  - Sybil and collusion resistance is not analyzed; the authors list it as future work.
  - Its anti-whitewashing relies on linking identities, which permissionless chains can't enforce.
- **Implication for referralTree:**
  - The closest academic model of **decayed multi-hop sponsor penalties**. γ^k per hop has the same shape as `RewardCalculator`'s 0.6^k weights, and K matches the 10-level cap.
  - BEPP is the missing mirror image of `rewardRoots`.
  - Suggests charging a skiplisted node's ancestors with the existing decayed weights, instead of moving them up (see [design note](../overviews/referrer-accountability-design.md)).
  - Doesn't address chain-stuffing.

### SybilGuard / SybilLimit / SybilRank
- **Citation:** Yu et al. 2006/2008; Cao et al. 2012. Already filed in [sybil-resistance.md](sybil-resistance.md).
- **Link:** see that file (verified there)
- **Summary:** Graph Sybil defenses depend on attack edges being few.
- **Implication for referralTree:** sponsor liability makes attack edges *expensive* because each honest referrer who admits a Sybil pays for it. That strengthens the sparse-cut assumption.

### Advogato trust metric and PGP web of trust
- **Citation:** R. Levien, Advogato trust metric (network-flow certification, ~2000); PGP web of trust.
- **Link:** (unverified — citations from memory; check before quoting)
- **Summary:** Certification flows from seeds with capacity that shrinks with distance, and bad certifiers' capacity bounds the damage. Neither *punishes* certifiers; they limit how far trust spreads. **(unverified)**
- **Implication for referralTree:** capacity limits (invites per node, decaying with depth) are a non-punitive complement to sponsor penalties.

### Sybilproof reputation mechanisms
- **Citation:** A. Cheng, E. Friedman. *Sybilproof reputation mechanisms.* Proc. 3rd Workshop on Economics of Peer-to-Peer Systems (P2PEcon), 2005.
- **Link:** <https://dl.acm.org/doi/10.1145/1080192.1080202> (verified title/venue via ACM listing)
- **Summary:** Shows symmetric reputation functions can't be Sybil-proof. Asymmetric, flow-based ones can.
- **Implication for referralTree:** any subtree-based penalty must not be gameable by splitting into more accounts (cap invites per address; new referrers inherit scrutiny).

---

## D. Collective punishment (history and law) — cautionary only

### Frankpledge and baojia
- **Citation:** Frankpledge (Anglo-Saxon/Norman tithings of ~10 households jointly liable); baojia (Song–Qing China mutual-surety household groups).
- **Link:** (unverified — citations from memory)
- **Summary:** Collective liability enforced order where the state couldn't monitor directly. Both are cited as cautionary tales about coercion. **(unverified)**
- **Implication for referralTree:** good optics argument *against* penalizing siblings or unrelated descendants.

### Collective punishment under IHL
- **Citation:** Geneva Convention IV, art. 33 (collective punishment prohibited for persons).
- **Link:** (unverified — citation from memory)
- **Summary:** Not legally relevant to a crypto referral tree, but it frames why "ban the whole subtree" reads badly. **(unverified)**
- **Implication for referralTree:** quarantine or reparent descendants of a fraudulent node; do not slash them as a group.

> **Out of scope:** China social credit — no credible evidence of a neighbor joint-guarantee scoring system was found; Western reporting conflates blacklists with a unified score. Joint-guarantee *loans* do exist in Chinese SME lending **(unverified)**. Leave out of product framing.
