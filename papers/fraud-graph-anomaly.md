# Fraud and graph anomaly detection

Detecting coordinated fake behavior from structure and timing in large graphs. These supply the concrete signals for the graph health service.

**Category takeaway:** coordinated fraud shows up as **dense blocks** (FRAUDAR), **lockstep timing** (CopyCatch, SynchroTrap) and **unusual local subgraph counts** (motifs). Referral farms produce all three.

---

### CopyCatch: Stopping Group Attacks by Spotting Lockstep Behavior in Social Networks
- **Citation:** A. Beutel, W. Xu, V. Guruswami, C. Palow, C. Faloutsos. Proc. 22nd International World Wide Web Conference (WWW '13), 2013.
- **Link:** <https://doi.org/10.1145/2488388.2488400> (verified via Crossref)
- **Summary:** Detects groups of users who act on the same set of objects (Facebook Page likes) within the same narrow time window, i.e., lockstep behavior. Formulates it as finding near-bipartite-cores in a time-annotated graph and deployed it at Facebook.
- **Implication for referralTree:** Registration and settlement timestamps are public. Flag bursts where many new nodes register under related referrers in the same window; that's the "lockstep timing" shape in graph-topologies.

### FRAUDAR: Bounding Graph Fraud in the Face of Camouflage
- **Citation:** B. Hooi, H. A. Song, A. Beutel, N. Shah, K. Shin, C. Faloutsos. Proc. 22nd ACM SIGKDD (KDD '16), 2016.
- **Link:** <https://doi.org/10.1145/2939672.2939747> (verified via Crossref)
- **Summary:** Finds dense subgraphs (e.g., fake followers/reviews) with a greedy algorithm and a density metric that downweights popular objects, giving provable bounds on how much fraud can hide even when fraudsters add camouflage edges to legitimate targets.
- **Implication for referralTree:** Camouflage maps to farms that also refer a few real users. A FRAUDAR-style density score over (referrer, referee, settlement) is robust to that.

### Uncovering Large Groups of Active Malicious Accounts in Online Social Networks (SynchroTrap)
- **Citation:** Q. Cao, X. Yang, J. Yu, C. Palow. Proc. ACM CCS 2014.
- **Link:** <https://doi.org/10.1145/2660267.2660269> (verified via Crossref)
- **Summary:** Clusters accounts by similarity of their timestamped actions, since malicious accounts controlled together act in loosely synchronized ways. Scalable implementation deployed at Facebook and Instagram.
- **Implication for referralTree:** Use action-similarity across wallets (registration times, settlement triggers, funding sources) to catch farms that avoid structural tells.

### Network Motifs: Simple Building Blocks of Complex Networks
- **Citation:** R. Milo, S. Shen-Orr, S. Itzkovitz, N. Kashtan, D. Chklovskii, U. Alon. Science 298(5594), 2002, pp. 824–827.
- **Link:** <https://doi.org/10.1126/science.298.5594.824> (verified via Crossref)
- **Summary:** Defines network motifs, small subgraph patterns that occur far more often than in randomized networks with the same degree sequence, and shows different network types have characteristic motif profiles.
- **Implication for referralTree:** Gives a principled baseline for "unusual shape": compare a group's motif counts (stars, paths, brooms) against degree-preserving random trees, rather than hand-tuned thresholds.
