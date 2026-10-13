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
- **Citation:** **(unverified)** — surfaced by search at ACM as "Enforcing Trust Accountability with Backward Propagation" (RepuLink), ACM 2025/26.
- **Link:** <https://dl.acm.org/doi/10.1145/3770855.3817611> **(unverified — fetch timed out; authors, venue and content not confirmed)**
- **Summary:** Search describes it as recursive endorser penalties that decay with distance. **(unverified)** Verify before citing.
- **Implication for referralTree:** if confirmed, would be the rare CS precedent for decaying multi-hop sponsor penalties. Do not cite externally until verified.

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
