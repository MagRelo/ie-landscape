# ie-landscape

A living research landscape for **Incentive Exchange** and **[referralTree](https://github.com/MagRelo/referralTree)**: the product, the academic literature it rests on, the competitors around it, and a dated log of what changes week to week.

Live product: <https://exchange.mattlovan.dev/>

## Thesis in one line

**IC after transaction costs.** People don't take referral actions that aren't incentive-compatible once transaction costs are counted. "Transaction costs" here means Coasean friction (search, bargaining, verification, enforcement, coordination), not gas. Agents, cheap L2 settlement and public on-chain receipts lower that friction, which makes designs viable that weren't before. See [product/overview.md](product/overview.md).

## How to navigate

| Folder | What's in it |
|---|---|
| [product/](product/overview.md) | What referralTree / Incentive Exchange is, how the payout math actually works (checked against the contracts), thesis, positioning |
| [papers/](papers/README.md) | Academic literature, one file per category, each entry with a verified citation, summary and "Implication for referralTree" |
| [competitors/](competitors/README.md) | Index table plus one file per segment: web2 affiliate SaaS, quest platforms, on-chain referral infra, agent/x402 attribution, recent signals, vouching/invite accountability |
| [overviews/](overviews/) | Cross-cutting syntheses: [market sizing](overviews/market-sizing.md), [SOTA solved vs open](overviews/sota-solved-vs-open.md), [positioning & opportunities](overviews/positioning-and-opportunities.md), [threat / topology map](overviews/threat-topology-map.md), [referrer accountability design](overviews/referrer-accountability-design.md) |
| [updates/](updates/README.md) | Dated weekly log, newest first |
| [CONTRIBUTING.md](CONTRIBUTING.md) | Templates for adding a paper, a competitor, or a weekly update |

## How weekly updates work

Every Monday a digest runs and:

1. Adds `updates/YYYY-MM-DD.md` (template in [CONTRIBUTING.md](CONTRIBUTING.md)) and links it at the top of [updates/README.md](updates/README.md).
2. Files each durable finding into its home: new papers into the right `papers/*.md` category (and the [papers index](papers/README.md)), new or changed competitors into `competitors/*.md` (and the [competitor index](competitors/README.md)).
3. Opens a PR titled `weekly: YYYY-MM-DD` so changes are reviewable. Quiet weeks still get a short update file saying so.

Rules: every claim has a source link; numbers are public numbers only, with the source; anything not verified is marked **(unverified)**. Never invent citations.

## Status

Seeded 2026-10-12 from the September research briefs, reorganized and corrected against `referralTree` main at commit `800da1d` (2026-10-03).
