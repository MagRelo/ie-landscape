# Vouching and invite-tree accountability

Not payout competitors. These are live systems that make an inviter or voucher answer for the people they bring in — the closest production references for referralTree sponsor liability. See [papers/referrer-accountability-social-collateral.md](../papers/referrer-accountability-social-collateral.md) and [overviews/referrer-accountability-design.md](../overviews/referrer-accountability-design.md).

### Proof of Humanity
- **What:** on-chain proof-of-personhood registry with human vouches. Contract: <https://github.com/Proof-Of-Humanity/Proof-Of-Humanity/blob/master/contracts/ProofOfHumanity.sol>; FAQ: <https://proof-of-humanity.gitbook.io/docs/proof-of-humanity-faq>
- **Mechanism:** every voucher of a profile ruled *Duplicate* or *DoesNotExist* is de-registered (loses UBI); optional fine/ban in code. Not applied for "Incorrect submission" or later removal requests. On-chain vouches can be withdrawn before Pending Registration.
- **Traction:** long-running mainnet deployment; UBI-linked.
- **vs referralTree:** strongest on-chain precedent for "voucher pays when the invitee is fake." Category-gated liability (Sybil/duplicate yes; other failures no) and pre-resolution withdraw are the patterns to copy. Not a referral payout system.

### Ethos Network
- **What:** on-chain reputation / credibility network with invites and slashing. [Invite](https://whitepaper.ethos.network/ethos-mechanisms/invite); [Slashing help](https://help.ethos.network/en/articles/9765931-how-does-slashing-work-on-ethos)
- **Mechanism:** inviter is bonded to the invitee's score for a window the docs call both "90 days" and "180 day" (internal inconsistency — treat duration as ~90–180 until clarified). Vouchers and positive reviewers of a slashed user take a "misplaced endorsement" hit: 20% of slash amount (vouch), 10% (review); avoidable by archiving before resolution. Failed slash penalizes the accuser.
- **Traction:** none independently verified here.
- **vs referralTree:** closest product language ("invite bond", "misplaced endorsement"). Fractional sponsor penalty + disavow-before-resolution + accuser bond are the design defaults worth adopting. Frame referralTree penalties the same way, not as MLM chargebacks.

### Lobsters
- **What:** invite-only link aggregator with a public invite tree and mod log. [About](https://lobste.rs/about); [mod log](https://lobste.rs/moderations/page/4?moderator=pushcx&what%5Bdomains%5D=domains&what%5Busers%5D=users)
- **Mechanism:** moderators disable inviters' invites or ban them; public "pruning spam tree" actions. Sometimes the upstream chain is affected. Descendants are pruned when inactive / no presence, not as collective punishment of honest users.
- **Traction:** long-running community; invite tree is public.
- **vs referralTree:** social, off-chain enforcement with transparency. Model for "freeze invites first" and for quarantining fraud descendants rather than slashing them.

### Idena
- **What:** proof-of-personhood network with invitation rewards. [Economics](https://docs.idena.io/docs/wp/economics); [IIP-6](https://docs.idena.io/docs/iip/iip-6)
- **Mechanism:** invitation rewards withheld if the inviter is penalized for a reported flip; inviter could "kill" an invitee early (disabled 2022).
- **Traction:** live network.
- **vs referralTree:** another "inviter upside tied to invitee conduct" example; the retired kill-invitee power is a caution about over-empowering sponsors.

### Polkadot NPoS (delegator slashing)
- **What:** nominated proof-of-stake; nominators back validators. [Docs](https://docs.polkadot.com/node-infrastructure/run-a-validator/staking-mechanics/offenses-and-slashes/)
- **Mechanism:** active nominators of an offending validator are slashed pro rata with the validator; max-per-span not cumulative; nominations chilled.
- **Traction:** production at scale.
- **vs referralTree:** precedent for *proportional, bounded* loss by people who staked on a bad actor. Maps to a staked invite bond better than to skiplist.

### EigenLayer (delegator slashing)
- **What:** restaking; stakers delegate to operators. [Slashing concept](https://docs.eigencloud.xyz/eigenlayer/concepts/slashing/slashing-concept)
- **Mechanism:** stakers delegated to a slashed operator lose delegated shares proportionally, bounded to "unique stake" allocated to that operator set.
- **Traction:** production.
- **vs referralTree:** same lesson as Polkadot — graded, stake-backed, bounded liability beats binary free-to-the-attacker skiplist.

### Private torrent trackers
- **What:** invite-only BitTorrent communities with tree bans.
- **Mechanism:** inviter and sometimes the whole invite tree lose invite rights / get tree-banned, especially for selling or trading invites. **(community sources only — e.g. [r/trackers](https://www.reddit.com/r/trackers/comments/1hpu3m0/is_there_any_risk_for_getting_invited_from_the/); tracker rules are private, treat as anecdotal)**
- **Traction:** n/a
- **vs referralTree:** anecdotal evidence that tree-wide bans exist in the wild; also a caution that whole-tree bans look coercive.

### Not accountability examples (do not cite as such)
- **Freemasonry** sponsor (proposer/seconder): reputational only; no formal penalty documented **(unverified)**.
- **Hacker/carding forums** vouch systems: voucher rep loss when vouched seller scams — known from security research but **(unverified)** this pass.
- **Fintech referral bonuses** (bank/broker/ride-hail ToS): bonus clawback if referee is fraudulent — common ToS clause **(unverified)**; cite a specific ToS before using.
- **MLM** upline commission chargebacks on refunded downline orders — standard comp-plan clause **(unverified)**; check specific plans. Optics warning only.
- **Gmail (2004), Clubhouse, Dribbble:** invite-only for scarcity/growth; no evidence of inviter penalties **(unverified)**. Don't cite as accountability examples.

## Usage, launch era & penalty frequency (as of 2026-10-13)

Never-invent rule: "unknown" means no source we could verify. Third-party counts are labeled as such.

| Project | Mainnet launch | Era | Peak usage | Current usage | Alive? | How often penalties fired | Sources |
|---|---|---|---|---|---|---|---|
| Proof of Humanity v1 (Ethereum) | 2021 | 2021 bull | ~19k registered (Kleros); 20,740 lifetime submissions (third-party scan) | 2 addresses still registered (third-party on-chain scan) | Frozen. Recognized by v2 through Fork Module | Challenge/removal counts: unknown | [Kleros docs](https://github.com/kleros/kleros-docs/blob/master/products/proof-of-humanity/README.md), [poh-aggregator](https://github.com/andrevalenm/poh-aggregator) |
| Proof of Humanity v2 (Gnosis) | 2024 (exact date unverified) | 2024-25 | ~1,364 lifetime registrations; ~1,299 came during a PNK airdrop window | Not independently verified | Yes, maintained by Kleros | `HumanityRevoked` fired **once** (third-party) | [Kleros docs](https://docs.kleros.io/developers/products/poh/overview), [poh-aggregator](https://github.com/andrevalenm/poh-aggregator) |
| Ethos Network (Base) | 2025-01-22 | 2024-25 | 15k vouches, 110k reviews by 2025-05-13 | unknown | Yes. Switched vouch asset from ETH to $WHUF | Slash count: unknown | [launch](https://www.ethos.network/post/ethos-is-live-on-base-mainnet), [May 2025](https://www.ethos.network/post/hello-ethos-validators) |
| Idena | Effectively Feb 2020 (v1.0 activated later) | 2019-20 post-ICO bear | 8,283 validated identities (Jun 2021) | Epoch 231. 120 online identities (total validated unknown), api.idena.io 2026-10-13 | Yes, small | Invitation/validation failures: unknown | [2020 report](https://medium.com/idena/idena-community-report-current-state-and-next-steps-dce97a0e3034), [2021 report](https://medium.com/idena/idena-2021-community-report-c7b2b1b262dc) |
| Polkadot / Kusama NPoS | Polkadot May 2020; Kusama 2019 (both unverified) | 2019-20 ICO hangover | n/a (chain-level) | n/a | Yes | Kusama: 394 `staking.Slashed` events (latest 2025-04-04). Big ones (KSM era 2249, 115 validators; era 4543, ~334 validators) were **reversed by governance**. Polkadot: a few (era 774; ~2021-10 KILT-onboarding incident) | [Subscan](https://kusama.subscan.io/event?event_id=Slashed&module=staking), [docs](https://docs.polkadot.com/node-infrastructure/run-a-validator/staking-mechanics/offenses-and-slashes/), [forum](https://forum.polkadot.network/t/kusama-era-4543-slashing/1410), [P2P](https://p2p.org/economy/kusama-slashing-post-mortem/) |
| EigenLayer | Restaking Apr 2024; slashing 2025-04-17 | 2024-25 | TVL ~$22.1B (DefiLlama peak, 2025-08-13); 80k+ staking addresses, 2,000+ operators (Apr 2025) | TVL ~$6.4B (DefiLlama, 2026-10-13) | Yes | No verified mainnet slashing event. Slashing is opt-in per AVS | [DefiLlama](https://defillama.com/protocol/eigenlayer), [Eigen blog](https://www.eigenlabs.org/blog/slashing-goes-live/) |

**Takeaways:** the penalty mechanisms exist but are almost never applied. Mass slashes were reversed by governance. Usage spikes track token incentives (PoH v2 airdrop, EigenLayer points, Ethos XP) and decays afterward.
