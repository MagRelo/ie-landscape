# On-chain referral infrastructure

Projects that put referral relationships and/or payouts on-chain. The nearest technical peers.

### Fuul
- **What:** web3 affiliate/referral/incentive SaaS with on-chain payouts. <https://www.fuul.xyz/> · docs <https://docs.fuul.xyz/>
- **Mechanism:** tracking links (`?af=code`) and project referral codes; attribution rules; rewards paid from project budgets. Supports a **multi-level referral tree (R1–R4)** via `GET /v1/affiliate-portal/referral-tree` (<https://docs.fuul.xyz/developer-guide/creating-affiliate-links-or-codes>). **Affiliate codes are global**: one custom code per affiliate works across all Fuul projects, and a project can activate it as its own referral code with per-project max uses and rebate rate (<https://docs.fuul.xyz/core-concepts/referral-codes-vs-invite-codes>).
- **Traction:** "$2M+ paid through programs" (site claim) and ~$500K disclosed raise (Caplight) per earlier brief **(unverified this pass)**.
- **vs referralTree:** closest commercial peer and already multilevel (4 levels). Differences: Fuul attribution is off-chain/platform-run; referralTree's edges and split are on-chain and verifiable, with oracle-signed settlement. Fuul's cross-project codes are a step toward portable referrer identity, which referralTree lacks (graphs are siloed per `groupId`).

### ShareMint
- **What:** web3 affiliate marketing platform. <https://sharemint.xyz/>
- **Mechanism:** affiliate links for mints/token actions, on-chain conversion tracking, commission payouts.
- **Traction:** ~$450K funding (Caplight) per earlier brief **(unverified)**.
- **vs referralTree:** single-level affiliate commissions; platform-run.

### Attrace
- **What:** referral/affiliate protocol positioning as on-chain attribution infrastructure. <https://attrace.com/about/>
- **Mechanism:** referral links and on-chain reward settlement for partner programs (per site; details not verified this pass).
- **Traction:** none verified.
- **vs referralTree:** similar "attribution protocol" pitch; single-level by default as far as public material shows **(unverified)**.

### ThunderCore `referral-solidity`
- **What:** inheritable Solidity library (~0.5) for games/dapps. <https://github.com/thundercore/referral-solidity>
- **Mechanism:** referee self-calls `addReferrer`; up to **3** levels with per-level rates; reward = amount × level rate × referee-count tier × active flag; pays native token inside `payReferral`.
- **Traction:** open-source library; no usage numbers.
- **vs referralTree:** self-registered edges (Sybil free-for-all) vs. oracle-gated; one tree per contract vs. many `groupId`s; native-only vs. any ERC-20; 3 levels vs. 10.

### BULK two-level referral with invite slots (Oct 20, 2026)
- **What:** BULK, a Solana perpetuals DEX, replaced access codes with a two-level referral program on Oct 20, 2026. Docs: <https://docs.bulk.trade/bulk-exchange/referral-rewards>; announcement thread (via mirror): <https://teapawt.org/bulktrade/status/2112530437256142926>. Missed by the 2026-10-26 digest.
- **Mechanism:** Base referrers earn **10% of net fees from direct referrals and 1% from indirect referrals** (people who joined through a direct referral's link); Top Partners (≥$1B lifetime personal + direct-referral volume) earn **15% / 2%**. Rates depend only on the referrer's own tier. Net fees exclude market-maker / maker-reward accounts and **trades executed through builder codes**. Each trader has one link with a finite number of **invite slots**: each sign-up uses one, and you earn **1 slot per $100,000 of personal trading volume**; with no slots left, nobody else can join through your link. Paid weekly in USDC (Saturday 12:00 UTC weeks); amounts under $1 roll over; wash trading and self-referral can forfeit pending rewards. Referred traders get a +5% / +10% boost in AURA points.
- **Traction:** invite-only mainnet beta launched Sep 5, 2026 after a pre-deposit campaign from Jun 1 ($25.9M USDC in 10 days) and an $8M seed (Sep 2025) ([Crypto Briefing](https://cryptobriefing.com/bulktrade-launches-solana-perps-exchange/)); testnet since March 2026, ~15,000 wallets eligible at launch and >$22M day-one volume per the CEO ([SolanaFloor](https://solanafloor.com/news/bulk-trade-outpaces-hyperliquid-lighter-in-first-day-volume-as-mainnet-beta-goes-live)). DefiLlama as of 2026-11-02: TVL $7.11M (peak $40.61M on Jun 20 in pre-deposits), 30-day perp volume $819.67M, cumulative $1.668B, cumulative fees $683,992 ([DefiLlama](https://defillama.com/protocol/bulk)). Active; volume partly points-farming ahead of an expected airdrop.
- **vs referralTree:** two levels with a steep 10:1 decay (vs referralTree's ~0.6 over up to 10 levels), paid weekly off-chain from fees, not settled on-chain per event. The interesting part is **invite slots**: a hard per-link cap that refills only with the referrer's *own* real activity. That's a live version of the per-code child cap being explored for issue #12, with a refill rule (earn capacity through your own outcomes) that also works as a Sybil brake. Excluding builder-code trades from referral fees shows exchanges already treat referral and builder (app) attribution as separate claims on the same fee, which matters if referralTree consumes ERC-8021 builder codes as evidence.

### Deferral (academic)
- **What:** research implementation from UZH (Boner et al., BRAINS 2023). <https://github.com/dydent/Deferral> · paper <https://doi.org/10.1109/brains59668.2023.10316807>
- **Mechanism:** ladder of contracts from a payment transmitter (direct referrer reward) to quantity/value evaluators with multilevel payout (typically equal split up to a max level); the contract holds funds until a referral process completes.
- **Traction:** research code.
- **vs referralTree:** Deferral couples eligibility + custody + split in one contract; referralTree factors eligibility into oracle policy, uses geometric split, and doesn't hold funds between transactions.

### Other patterns seen (for reference)
- **Safwa** (<https://github.com/SafwaNetwork/contract.safwa.network>): matrix/forced-fill MLM contract; the legal-risk end of the spectrum.
- **LooksRare AffiliateManager** (<https://docs.looksrare.org/developers/protocol-contracts/AffiliateManager>): fee-share affiliates, single hop.

### Orderly multilevel affiliate program
- **What:** multilevel referral system that perp DEXs built on Orderly can switch on; announced on Orderly's LinkedIn (post dated 2026-08-14, <https://www.linkedin.com/posts/orderly-network_all-perp-dex-builders-on-orderly-have-access-activity-7494086933007106048-p6jC>). Docs: <https://orderly.network/docs/introduction/be-a-broker/orderly-dex-affiliate-program-affiliates-quick-guide>. Missed by earlier digests.
- **Mechanism:** up to **15 affiliate levels**. The DEX builder assigns each top-level affiliate a total commission rate (paid from builder fees on every trade); each affiliate assigns rates to their direct referees (never above their own, never below an optional builder-set minimum pass-down rate) and keeps the **difference** on trades below them. Docs example: rates 50% / 35% / 25% pay 15% / 10% / 25%. Upline rate cuts come out of the direct referee's earnings first; settled commissions are never recalculated. One referral code per affiliate. Upgrading from the legacy single-level program is irreversible.
- **Traction:** none public.
- **vs referralTree:** the first live, on-chain-adjacent multilevel program in the landscape that goes deeper than referralTree's cap (15 vs 10). It is a top-down differential ("breakaway") model where each upline sets the downline's share, so position in the tree directly decides earnings and uplines can squeeze their referees: the opposite of referralTree's fixed, bottom-up geometric decay aimed at revenue equivalency. Useful contrast for positioning and for the MLM/legal framing; its one-code-per-affiliate rule is a nearby precedent for capping codes.
