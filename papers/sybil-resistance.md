# Sybil resistance

Fake identities are the central attack on any per-identity reward. This literature says what's impossible without a trusted authority and how far graph structure can get you.

**Category takeaway:** without some identity authority Sybils can't be prevented (Douceur); graph-based defenses bound the damage *per attack edge* if the honest region is fast-mixing, but they're really community detection and degrade on real graphs with tight communities (Viswanath et al.). For referralTree the "attack edge" is an oracle-approved registration, which is why oracle policy is the real defense.

---

### The Sybil Attack
- **Citation:** J. R. Douceur. *The Sybil Attack.* Peer-to-Peer Systems (IPTPS 2002), LNCS 2429, Springer, 2002.
- **Link:** <https://doi.org/10.1007/3-540-45748-8_24> (verified via Crossref)
- **Summary:** Shows that in a distributed system without a logically centralized identity authority, a single entity can always present multiple identities, and that resource-testing defenses only work under unrealistic assumptions. Coined "Sybil attack".
- **Implication for referralTree:** Justifies the oracle-gated `register`: some authority must vouch for identities. Be explicit that referralTree's Sybil resistance is exactly as good as each group's oracle policy.

### SybilGuard: Defending Against Sybil Attacks via Social Networks
- **Citation:** H. Yu, M. Kaminsky, P. B. Gibbons, A. Flaxman. *SybilGuard.* ACM SIGCOMM 2006 (CCR 36(4)); extended in IEEE/ACM Trans. Networking 16(3), 2008.
- **Links:** <https://doi.org/10.1145/1151659.1159945>; <https://doi.org/10.1109/tnet.2008.923723> (both verified via Crossref)
- **Summary:** Uses the fact that Sybils connect to honest users through relatively few "attack edges". Random routes in the social graph let honest nodes accept others while bounding accepted Sybils to about O(√n log n) per attack edge.
- **Implication for referralTree:** Map the idea directly: a farm's sub-tree hangs off honest nodes through a few edges. Sparse-cut regions are a key graph-health signal.

### SybilLimit: A Near-Optimal Social Network Defense against Sybil Attacks
- **Citation:** H. Yu, P. B. Gibbons, M. Kaminsky, F. Xiao. *SybilLimit.* IEEE Symposium on Security and Privacy 2008; IEEE/ACM ToN 18(3), 2010.
- **Links:** <https://doi.org/10.1109/sp.2008.13>; <https://doi.org/10.1109/tnet.2009.2034047> (both verified via Crossref)
- **Summary:** Improves SybilGuard's bound to O(log n) accepted Sybils per attack edge, near-optimal for this class, using multiple short random routes; validates fast-mixing assumptions on real social graphs.
- **Implication for referralTree:** Sets the realistic ceiling for purely structural detection; extra signals (timing, funding sources) are needed for better.

### SybilInfer: Detecting Sybil Nodes using Social Networks
- **Citation:** G. Danezis, P. Mittal. *SybilInfer.* Network and Distributed System Security Symposium (NDSS) 2009.
- **Link:** <https://www.ndss-symposium.org/ndss2009/sybillnfer-detecting-sybil-nodes-using-social-networks/> (paper page; verified). PDF <https://www.princeton.edu/~pmittal/publications/sybilinfer-ndss09.pdf>
- **Summary:** Bayesian inference over a probabilistic model of honest social graphs (fast-mixing random walks) to label nodes honest or Sybil, with a probability on each label. Reports better accuracy than SybilGuard/SybilLimit.
- **Implication for referralTree:** Probabilistic labels fit a "flag / down-weight / skiplist" ladder better than binary verdicts; graph health scores should carry confidence.

### Aiding the Detection of Fake Accounts in Large Scale Social Online Services (SybilRank)
- **Citation:** Q. Cao, M. Sirivianos, X. Yang, T. Pregueiro. 9th USENIX NSDI '12, 2012, pp. 197–210.
- **Link:** <https://www.usenix.org/conference/nsdi12/technical-sessions/presentation/cao> (verified)
- **Summary:** Ranks users by the landing probability of short, early-terminated random walks from trusted seeds (power iteration, O(n log n)). Deployed at Tuenti: about 90% of the 200K lowest-ranked accounts warranted suspension versus about 5% for the user-report process.
- **Implication for referralTree:** The most deployable algorithm here: seed trust from known-good addresses (e.g., settled, long-lived users), rank the rest, feed low ranks to skiplist review.

### An Analysis of Social Network-Based Sybil Defenses
- **Citation:** B. Viswanath, A. Post, K. P. Gummadi, A. Mislove. ACM SIGCOMM 2010.
- **Link:** <https://doi.org/10.1145/1851182.1851226> (verified via Crossref)
- **Summary:** Shows the leading social-graph Sybil defenses all effectively rank nodes by how well they connect to a trusted node's local community, i.e., they're community detection. Consequence: they mislabel honest users outside the trusted community, and are vulnerable when Sybils embed near the seed.
- **Implication for referralTree:** Referral trees are full of legitimate tight communities (a contest league, a Discord). Don't auto-skiplist on structure alone; combine with timing and economic signals and keep a human/oracle confirm step.

## Recent (2026): Sybil cost bounds for payment and reward systems

### AgentValve: Sybil-Resilient Payment Authorization for Permissionless AI Markets
- **Citation:** J. Zhang, Z. Luo, A. Kate. *AgentValve: Sybil-Resilient Payment Authorization for Permissionless AI Markets.* arXiv:2610.12948 (v1, 9 Oct 2026).
- **Link:** <https://arxiv.org/abs/2610.12948> (verified on arXiv)
- **Summary:** Models reputation as finite *capacity* on a directed trust graph and authorizes an agent payment only along trust paths with enough spare capacity; a smart contract atomically reserves that capacity per admitted payment. An honest agent's loss is bounded by the capacity it extends into the adversarial region, so minting identities inside that region can't raise the bound. Payment-backed capacity creation plus a bounded route length stop attackers from draining honest capacity for free. Prototype on six months of Ethereum data: exposure stays bounded with up to 10,000 synthetic Sybils; witness-commit cuts admission cost by up to 40.8% vs baselines; ~$0.04–$0.21 per common payment (authors' figures).
- **Implication for referralTree:** A concrete on-chain version of "a sponsor's liability is capped by what they extended": give each referrer a finite vouching capacity that their sub-tree's payouts draw on, and a farm hanging under them can only ever cost what that edge holds. Bounded route length is the same lever as the depth-10 cap, here with a security proof attached.

### NFT-Based Reward Mechanisms: Sybil Farming, Vesting, and Stochastic Verification
- **Citation:** M. A. Javarone, S. Leonardos, C. Ventre. *NFT-Based Reward Mechanisms: Sybil Farming, Vesting, and Stochastic Verification.* arXiv:2609.13064 (v1, 11 Sep 2026).
- **Link:** <https://arxiv.org/abs/2609.13064> (verified on arXiv)
- **Summary:** A farmer runs many identities that submit fraudulent reward claims subject to vesting; the issuer randomly audits during vesting, and linked identities form a cluster that is forfeited entirely when any one is caught. Rewards then grow linearly in identities while the chance of escaping detection falls geometrically, giving an optimal farm size and a sufficient deterrence frontier in audit cost, vesting length and penalty. When small audit capacity is cheap, vesting alone is not optimal; the paper also separates the role of penalties from cluster-level auditing.
- **Implication for referralTree:** Formal backing for the claw-back ladder: hold rewards in a vesting window, randomly audit a few settlements, and on a hit forfeit the whole linked cluster (the sub-tree), not just the one node. Use their frontier to size the ~180-day bond against audit cost instead of guessing. Ventre co-authored earlier MLM-mechanism work, so this sits close to the incentive-tree literature.

### Tempting the Agent: The Economics of Reputation without Persistent Identity in AI Agent Markets
- **Citation:** F. Gatta, M. Naviglio, F. Tarantelli. *Tempting the Agent: The Economics of Reputation without Persistent Identity in AI Agent Markets.* arXiv:2609.02992 (v1, 2 Sep 2026; v2, 21 Oct 2026).
- **Link:** <https://arxiv.org/abs/2609.02992> (verified on arXiv)
- **Summary:** Dynamic model in which reputation is capital that attracts future demand; at each point an agent chooses to stay honest, invest in quality, or take a one-shot deviation that cashes out its reputation and restarts under a penalized new identity. Derives how the temptation to deviate depends on identity-reset cost, reputation persistence, demand sensitivity and enforcement design, with comparative statics on optimal quality. Names ERC-8004, ERC-8183 and x402 as the motivating on-chain agent setting.
- **Implication for referralTree:** A skip-list or slash only disciplines a referrer if coming back under a fresh code is expensive. Capping children per code and going effectively invite-only raises exactly that reset cost (a new identity needs a new invite from someone willing to be accountable for it), so the cap and the accountability ladder should be designed together.
