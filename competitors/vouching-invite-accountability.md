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
