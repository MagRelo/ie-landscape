# Papers index

Each entry lives in a category file with a verified citation, link, 2–4 sentence summary and an **Implication for referralTree** line. Anything not independently verified is marked **(unverified)**. In-flight builds (hackathon projects, prototypes, open-source repos) live in [current-work/](../current-work/README.md), not here.

| Category | File | Papers |
|---|---|---|
| Incentive trees & MLM mechanisms | [incentive-trees-mlm.md](incentive-trees-mlm.md) | Emek et al. 2011; Drucker & Fleischer 2012; Lv & Moscibroda 2013/2016; Boner et al. (Deferral) 2023; Reingewertz 2021; Feng et al. 2026 (HSSC, e-referral) |
| Query incentive networks & branching | [query-incentive-networks.md](query-incentive-networks.md) | Kleinberg & Raghavan 2005; Pickard et al. 2011; Babaioff et al. 2012; Chen et al. 2013; Zhang & Tang 2023 |
| Sybil resistance | [sybil-resistance.md](sybil-resistance.md) | Douceur 2002; SybilGuard 2006/08; SybilLimit 2008/10; SybilInfer 2009; SybilRank 2012; Viswanath et al. 2010; AgentValve 2026 (arXiv:2610.12948); Javarone–Leonardos–Ventre 2026 (arXiv:2609.13064); Gatta–Naviglio–Tarantelli 2026 (arXiv:2609.02992); Zhang–Li–Shi et al. 2026 Sybil-proof adaptive clinching (arXiv:2610.36629); Ramji et al. 2026 Anduin x402 payment-graph reputation (arXiv:2611.05586); Maleki et al. 2026 bilinear Sybil cost (arXiv:2611.06268) |
| Fraud & graph anomaly detection | [fraud-graph-anomaly.md](fraud-graph-anomaly.md) | CopyCatch 2013; FRAUDAR 2016; SynchroTrap 2014; Milo et al. 2002 |
| Profit reallocation & resale trees | [profit-reallocation-resale-trees.md](profit-reallocation-resale-trees.md) | Ma, Xin, Li, Zheng & Deng 2026 (arXiv:2609.33506); Xin et al. TBDS 2025 |
| Attribution & Shapley-style credit | [attribution-shapley.md](attribution-shapley.md) | Shapley 1953; Shao & Li 2011; Dalessandro et al. 2012; marketing-science referral papers; Mobius et al. 2026 (arXiv:2610.30324); Goyal–Doshi–Nath 2026 temporal cooperative games (NeurIPS, arXiv:2510.11255) |
| MLM, pyramid & legal | [mlm-pyramid-legal.md](mlm-pyramid-legal.md) | Vander Nat & Keep 2002; Keep & Vander Nat 2014; FTC v. Amway stipulated order 2026 |
| Referrer accountability & social collateral | [referrer-accountability-social-collateral.md](referrer-accountability-social-collateral.md) | Karlan et al. 2009; Besley & Coate 1995; Bryan–Karlan–Zinman; Beaman & Magruder 2012; Kellett–Tran–Li 2010; Wu & Konstantinidis 2026 (RepuLink, KDD); Cheng & Friedman 2005 |

## Backlog (carried over from earlier briefs, not yet verified or filed)
- Liu & Zhu 2022, airdrop Sybil behavior, arXiv:2209.04603 **(unverified)**
- Liu et al. 2025, airdrop Sybil detection, arXiv:2505.09313 **(unverified)**
- Rahwan et al., fair allocation in diffusion, arXiv:1404.0542 **(unverified)**
- Zhang & Chaintreau 2021, strategic referral, arXiv:2112.00269 **(unverified)**
- Kandhway & Kotnis, arXiv:1601.07505 **(unverified)**

## Most important for the current design
1. Emek et al. + Drucker & Fleischer: why the geometric split isn't Sybil-proof and what a fix looks like.
2. Chen et al. / Zhang & Tang: the "finder-heavy" alternative.
3. SybilRank + CopyCatch + FRAUDAR: the graph health service's detector stack.
4. Ma et al. 2026: welfare case for upstream payment.
5. Vander Nat & Keep: funding source, not depth, is the legal line. FTC v. Amway (2026) makes it concrete: upline credit cut pro rata when downline volume isn't real customer sales.
6. AgentValve + Javarone et al. 2026: bounded sponsor exposure and cluster forfeiture with vesting/audits, the math behind a referrer-liability ladder.
7. Bryan–Karlan–Zinman + Kellett–Tran–Li + PoH/Ethos: sponsor liability — skiplisting today rewards the referrer; see [referrer-accountability-design](../overviews/referrer-accountability-design.md).
8. Goyal–Doshi–Nath 2026: order-dependent reward sharing, where Shapley-style fairness and arrival incentives can't both hold. The frame for the early-mover premium and issue #12 Option D.
9. Anduin (Ramji et al. 2026): payment-anchored, personalized trust on real x402 data; the template for a graph health score that Sybils can only move by spending money.
