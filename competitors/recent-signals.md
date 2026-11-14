# Recent signals

Live programs that changed how they pay for referral/recommendation. Newest first. Move items into a segment file once they're clearly durable.

### Binance Sub-Affiliate (launched Nov 9, 2026)
- **What:** Binance added a Sub-Affiliate feature to its affiliate program. Source: Binance announcement, 2026-11-09 (released 01:00 EST / 06:00 UTC), <https://www.binance.com/en/support/announcement/detail/9a4535f2f65149f1a09932fbefa11c7a>.
- **Mechanism:** an Affiliate shares part of its own commission rate with Sub-Affiliates it invites, who can invite further Sub-Affiliates, **up to 7 levels**, with **at most 50 Sub-Affiliates per Top Affiliate in total**. Each level sets its direct invitees' rates (differential, like Orderly), but every invite must pass on **≥20%** of the Spot and Futures rate and the inviter must keep **≥5% of the overall rate** (at setup only). The whole team's payout **never exceeds the Top Affiliate's rate**; Binance pays each participant directly. If the top rate is later cut (e.g. evaluation downgrade), the cut comes out of the Affiliate's retained share first. Commissions "may be adjusted or reduced to zero at any time, including where another participant in your team is restricted for compliance reasons", and paid commissions can be clawed back for breaches. Sub-Affiliates must pass KYC, hold an activated Futures account, and never have been an Affiliate; one team per person. Free to join; commission only on referees' trading, not on recruiting.
- **Traction:** none public for this feature (launched the day of this digest).
- **vs referralTree:** the largest exchange is now running a multilevel program with exactly the guardrails referralTree is weighing: a hard team cap (50 total, vs our ~25 direct children per code), a depth cap (7 vs 10), a conserved budget (team total ≤ top rate, like renormalized weights summing to the root share) and team-wide downside when one member is restricted, i.e. joint liability in production. Differences: rates are set top-down by each upline and the cap is on total team size, whereas referralTree's decay is fixed bottom-up from the trigger and is published on-chain; Binance's rates can change at its discretion.

### edgeX referral commission upgrade (effective Oct 9, 2026)
- **What:** edgeX (perp DEX) upgraded its referral program. Source: edgeX, Oct 10, 2026, <https://pro.edgex.exchange/en-US/news/article/edgex-referral-commission-upgrade-earn-up-to-30-on-friends-trading-fees>.
- **Mechanism:** single-level fee share on referees' trading fees in a published three-tier ladder: Lv.1 5% (≥5 active referrals and ≥500K USDC referee 14-day volume), Lv.2 15% (≥30 and ≥3M), Lv.3 30% (≥100 and ≥10M). A referee counts as active only after ≥100 USDC deposit and ≥50K USDC valid volume. Tiers hold 14 days and auto-downgrade to Lv0; rewards settle daily at 00:00 UTC and are claimed into the trading account.
- **Traction:** none public.
- **vs referralTree:** single-level and volume-gated, but a clean example of a public, rolling "proof of active referees" bar that downgrades automatically. Shows exchanges converging on published rules plus activity thresholds, the transparency referralTree already has, without multilevel path credit.

### Engy (Bittensor SN53) referral program (Oct 12, 2026)
- **What:** Engy, an API service on Bittensor subnet 53, launched a referral program. Source: The TAO Daily via Taosis, Oct 12, 2026, <https://taosis.com/news/16881946> (summary only; terms not independently verified beyond it).
- **Mechanism:** 10% of referred customers' API spend for 12 months, paid in USDC or API credits.
- **Traction:** none public.
- **vs referralTree:** second Bittensor subnet in two weeks (after SayGM SN28) paying single-level, time-boxed revenue share on API spend. Pattern worth noting: AI-API sellers are reaching for referral rails, which is the agent-attribution market referralTree targets.

### Pump.fun Callout Rewards (change effective Oct 10, 2026)
- **What:** Pump.fun pays users daily in USDC for token "callouts" (recommendations). Source: Crypto Briefing, Oct 10, 2026, <https://cryptobriefing.com/pump-fun-callout-rewards-follower-profits/>.
- **Mechanism:** from the Oct 10 payout, rewards track whether **followers who acted on a callout benefited (profited)**, not trading volume generated; low-cap token callouts earn at a reduced rate; Oct 4 change already cut rewards for high-frequency posters. The methodology is **not disclosed** and can change without notice.
- **Traction:** program launched around August 2026 with an approximate **$15M budget** set aside for payouts (per the article). Note: earlier digest said "~$15M paid so far"; the source supports a ~$15M budget, not confirmed payouts.
- **vs referralTree:** moves credit to downstream outcomes (good, aligns with Ma et al.), but with a secret metric: maximal verification/enforcement friction for participants. A clean contrast for the IC-after-transaction-costs argument: referralTree's rule is public and payouts are receipts.

### SayGM affiliate program (Oct 6, 2026)
- **What:** affiliate program for SayGM's AI inference gateway, on Bittensor Subnet 28. <https://saygm.com/blog/get-paid-to-refer-developers-to-saygm-ai-gateway>
- **Mechanism:** a share of SN28 alpha emissions flows into a contract-held pool; each round (≥24h) the pool is split **pro rata by each affiliate's share of referred revenue**, capped at **$1 of alpha per $1** a referred customer paid, for **30 days** from the customer's first top-up. Holds: 7 days (crypto), 120 days (card). Accounts sharing a card or payer coldkey are grouped; only new accounts count; self-referral allowed under the same rules. Allocations recorded on-chain.
- **Traction:** none public yet.
- **vs referralTree:** single-level, revenue-capped, transparent contract math. Good comparator for "proof of customers" eligibility; no multilevel path credit.

### Xyper Points (Oct 1, 2026)
- **What:** points program for Xyper, an on-chain creator marketing marketplace. GlobeNewswire via StreetInsider, <https://www.streetinsider.com/Globe+Newswire/Xyper+Launches+New+Rewards+Model+for+the+Global+Creator+Economy/27130525.html>
- **Mechanism:** points for campaign activity, content, quests and referrals (future XYPER token redemption). Biz Dev **partner tier**: up to **50% of protocol fee revenue** from partner-attributed campaigns (protocol fee = 10% of gross funding; 5% of gross split between partner reward and advertiser discount). Experienced partners can **recruit and train teams of their own**.
- **Traction:** none public.
- **vs referralTree:** recruit-your-own-team structure is the multi-level pattern regulators watch; useful positioning contrast (referralTree pays from app revenue with published math and no buy-in).

### Clicks Protocol
- **What:** per its GitHub, "agent commerce settlement router for AI agents on Base. Split USDC into liquid working capital and routed yield." <https://github.com/clicks-protocol/clicks-protocol>
- **Correction:** earlier briefs described Clicks as click/referral attribution; the current repo describes a settlement/yield router, not a referral system. 0 stars as of 2026-10-12. No material update this week.
- **vs referralTree:** not a direct competitor on current evidence; keep watching only for agent-commerce settlement overlap.
