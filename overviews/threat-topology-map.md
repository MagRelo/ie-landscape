# Threat / topology map

The canonical catalog is referralTree's [docs/theory/graph-topologies.md](https://github.com/MagRelo/referralTree/blob/main/docs/theory/graph-topologies.md) (PR #9, merged 2026-10-01): 12 shapes, each with payout math, detection signals and an indexer action. This page is the map from those shapes to the literature and to the current contract behavior.

> **Read with the 2026-10-03 change in mind.** graph-topologies.md assumes `rewardRoots` pays the trigger user at position 0. Since commit `1c99267` it pays **ancestors only** (`getPayoutAncestors`), so "position 0" is now the trigger's direct referrer and the trigger is paid only via `rewardLeaf`. Shapes that relied on "the honest trigger keeps 40.25%" (chain stuffing, brooms) are now **worse**: an attacker owning every payable ancestor above a real user captures the whole `rewardRoots` amount. See [product/overview.md](../product/overview.md). A follow-up PR to update graph-topologies is recommended.

| # | Shape (graph-topologies) | What it exploits now | Signals | Suggested action | Literature |
|---|---|---|---|---|---|
| 1 | Long single chains (chain stuffing) | Fake ancestors above real users capture up to 100% of `rewardRoots` | depth ≫ log(size), branching ≈ 1, shared funding | Block / skiplist mid-chain | Emek; Drucker–Fleischer; Kleinberg–Raghavan (branching) |
| 2 | Caterpillars / brooms | Fake spine over a fan of real leaves | spine nodes with 1 child except the bottom | Down-weight spine | Emek; Milo motifs |
| 3 | Star / hub capture | One referrer is position 0 for many triggers (62.5% at n=2) | out-degree outlier, low grandchildren | Flag; cap per-hub pay | Lv–Moscibroda (fairness) |
| 4 | Dense clumps / collusion rings | Cooperating real people | dense blocks of mutual activity | Flag | FRAUDAR; Zhang–Tang (collusion) |
| 5 | Sybil region behind a sparse cut | Many identities via few attack edges | conductance, random-walk rank | Rank + review | SybilGuard; SybilLimit; SybilInfer; SybilRank; Viswanath |
| 6 | Fan-out bursts of leaves | Mass leaf registration | burst size per referrer per window | Rate-limit at oracle | CopyCatch; SynchroTrap |
| 7 | Parked near depth cap | Tail shares (positions 8+9 ≈ 1.07% at n=10) | depth histogram spike at 9–10 | Highlight only | (engineering) |
| 8 | Cycles / self-referral via multiple wallets | Same owner on both ends | funding-source links | Block | Douceur |
| 9 | Lockstep timing | Scripted farms | synchronized registrations/settlements | Flag | CopyCatch; SynchroTrap |
| 10 | Wash settlement | Circular value through `rewardRoots` | payer ↔ recipient overlap | Block listing | FRAUDAR |
| 11 | Early position advantage | First registrants sit above many triggers | payout Gini by generation | Highlight | Lv–Moscibroda; Reingewertz |
| 12 | Pyramid optics | Deep, narrow, recruitment-funded | depth vs. branching; funding source | Disclose / delist | Vander Nat & Keep |

**Defense layers:** (1) oracle registration policy is the attack-edge gate (Douceur); (2) skiplist removes bad lineages from future pay without rewriting history; (3) graph health scoring (shown in each project record on the RichBouquet catalog) ranks/flags (SybilRank, FRAUDAR, CopyCatch); (4) optional Sybil-aware calculator (Drucker–Fleischer / Chen et al.).

**Positioning tie-in (2026-10-19):** the site says principals keep discretion over payment and skiplists exclude addresses, and that these controls belong in the published terms. So each defense layer above should be disclosed in a project's terms, not only run internally.

**Related:** skiplisting a node today *rewards* its referrer by collapsing the chain. Sponsor-liability design options are in [referrer-accountability-design.md](referrer-accountability-design.md).
