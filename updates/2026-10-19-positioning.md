# 2026-10-19: positioning sync with MagRelo/ie

Source: [MagRelo/ie](https://github.com/MagRelo/ie) `main` @ `eac2361` (2026-10-18): `apps/web/src/pages/HomePage.tsx`, `HowItWorksPage.tsx`, `PlayTheCutCaseStudyPage.tsx`, `brand.ts`, `README.md`, `spec/`, commits since 2026-09-25.

## New positioning (from the ie site)
- Product name at ie@eac2361 was **RichBouquet** (brand.ts; history: Sabir → Mercataform → Incentive Exchange → RichBouquet). Tagline: "rails for the autonomous economy" / "Set the terms. Let the work happen."
- **Principals** publish standing terms (opportunities/projects); **agents** pursue them independently and own their approach. The contract is "rearranged in time": terms, then work, then evaluation and compensation.
- "Think of all the deals not done": the plain-language form of the Coasean transaction-cost thesis (search, negotiation, trust, oversight), consistent with ie-landscape's thesis (not gas).
- **Social contract with a visible record:** principal keeps payment discretion (oracle, skiplists); onchain records make terms, relationships and payouts inspectable; offchain handles evaluation and abuse. Two-way history: agents judge principals too.
- **Autonomous business models:** pay from the activity agents generate (growth as something to share).
- Play the Cut is the case study (contest margin funds player growth; escrowed prize pools; published referral rules).
- Graph health moves from headline to evidence inside each project record; new surfaces: Agent Leaderboard, Add Your Project (WIP), Mechanism (WIP).

## Changes in this repo
- README: new positioning line, product name, status note.
- product/overview.md: rewrote "What it is" (principal/agent framing, rails, case study, terminology table) and "Positioning (short)". Mechanism section unchanged.
- overviews/positioning-and-opportunities.md: new one-line position, target user, what changed; reframed opportunities 2–3; added "two-way track record".
- overviews/sota-solved-vs-open.md: framing note; new open item "accountable discretion / two-way reputation"; pitfall 1 updated.
- overviews/market-sizing.md: note that "deals not done" has no public size; affiliate figures are proxies, not TAM.
- overviews/threat-topology-map.md: defenses should be disclosed in published terms.
- papers (4 files) and competitors/agent-x402-attribution.md: "Incentive Exchange" relevance lines reworded; research content untouched.

## Not reconciled
- Live URL still recorded as exchange.mattlovan.dev.
- updates/README.md not edited here to avoid conflicting with open PR #3 (landscape/2026-10-19); add this entry after #3 merges.

## Decisions (Matt, 2026-10-19)
1. **Product name is LightForest.** It replaces RichBouquet and the other brand names that appear in ie (AgentOp in the repo README, "ReferralTree catalog" in the spec, and the earlier Incentive Exchange). Name history: Sabir → Mercataform → Incentive Exchange → RichBouquet → LightForest. `referralTree` still means the contracts/repo.
2. **Product metrics reset to zero.** Play the Cut / referralTree stats are now $0 paid out, 0 settlements, 0% settlement rate, 0% skiplist rate in product/overview.md, competitors/README.md and overviews/market-sizing.md (comps line). Market-sizing estimates and third-party research numbers are unchanged. Older update files (2026-10-05/12/13) have no product stats, so they're left as history.

## Re-sync to ie @ e88842e (2026-10-20)
- Hero/tagline: "rails for the autonomous economy / Set the terms. Let the work happen." became **"Work for Agents: Create an opportunity. Let agents get to work."** Updated in the README, product overview, positioning overview and the x402 competitor framing line.
- "Expanding Economic Space / Think of all the deals not done" (the transaction-cost section) is now reflected as the lead argument in the product overview and README.
- Play the Cut summary rewritten from `packages/db/prisma/play-the-cut-agent.md`, which is now a league-admin agent guide: open approaches with leagues highlighted, roughly 5–7% of gross contest volume locked for the referral network, payouts to the winning player's invite chain, and attribution at account creation.
- ie `brand.ts` now says LightForest, matching this repo. (The agent guide in ie still says "RichBouquet" in places.)
- Pins bumped from eac2361 to e88842e. Product metrics stay at 0; third-party and market-sizing figures unchanged.
