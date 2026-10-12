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

### Deferral (academic)
- **What:** research implementation from UZH (Boner et al., BRAINS 2023). <https://github.com/dydent/Deferral> · paper <https://doi.org/10.1109/brains59668.2023.10316807>
- **Mechanism:** ladder of contracts from a payment transmitter (direct referrer reward) to quantity/value evaluators with multilevel payout (typically equal split up to a max level); the contract holds funds until a referral process completes.
- **Traction:** research code.
- **vs referralTree:** Deferral couples eligibility + custody + split in one contract; referralTree factors eligibility into oracle policy, uses geometric split, and doesn't hold funds between transactions.

### Other patterns seen (for reference)
- **Safwa** (<https://github.com/SafwaNetwork/contract.safwa.network>): matrix/forced-fill MLM contract; the legal-risk end of the spectrum.
- **LooksRare AffiliateManager** (<https://docs.looksrare.org/developers/protocol-contracts/AffiliateManager>): fee-share affiliates, single hop.
