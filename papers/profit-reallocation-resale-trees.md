# Profit reallocation and resale trees

Returning part of downstream revenue to upstream contributors in tree-shaped markets. The closest welfare-theoretic support for paying ancestors from descendants' value.

---

### Profit Reallocation Mechanisms in Tree-based Data Trading
- **Citation:** Y. Ma, W. Xin, J. Li, Y. Zheng, X. Deng. *Profit Reallocation Mechanisms in Tree-based Data Trading.* arXiv:2609.33506, 2026 (v1 Sep 27, v2 Sep 29, per weekly digest).
- **Link:** <https://arxiv.org/abs/2609.33506> (abstract and full text fetched and checked 2026-10-12)
- **Summary:** Models replicable data resold down a tree as a sequential game with posted prices and defines budget-feasible profit reallocation mechanisms (PRMs) that route part of each trade's payment to the buyer's ancestors. Gives a polynomial-time exact algorithm and an FPTAS for the equilibria via subtree decomposition. Proves any budget-feasible PRM weakly expands equilibrium trade and any budget-balanced PRM weakly improves welfare versus no reallocation; experiments show the gains grow with depth and branching. Experiments include a geometric baseline (TBDS, α=0.5) and a uniform split, both far better than no reallocation.
- **Implication for referralTree:** Formal welfare backing for upstream payment from downstream value, and therefore for a geometric rule like 0.6/depth-10. Caveats: the tree is value-adding resale, not recruitment; assumptions include positive valuations and homogeneity; Sybil/collusion robustness is listed as an open direction. Treat as support for the *direction*, not the specific constants.

### TBDS: Transaction-Based Data Sharing
- **Citation:** W. Xin, H. Chen, X. Dong, J. Li, X. Deng, Z. Wu, B. Xiao. *TBDS: Transaction-Based Data Sharing.* Frontiers of Algorithmics (IJTCS-FAW 2025), LNCS 15828, pp. 222–237.
- **Link:** cited as ref [39] in arXiv:2609.33506 **(unverified: DOI not independently checked)**
- **Summary:** Blockchain-based mechanism that traces resale transactions and pays upstream contributors a fixed geometric fraction of downstream revenue, with the root absorbing the remainder.
- **Implication for referralTree:** A direct on-chain analogue of geometric upstream payment, in a data market. Worth reading for its fixed-ratio design rationale.
