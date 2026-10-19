# Referrer accountability: design takeaways for referralTree

How to make sponsors answer for the people they bring in, grounded in the literature and live systems in [papers/referrer-accountability-social-collateral.md](../papers/referrer-accountability-social-collateral.md) and [competitors/vouching-invite-accountability.md](../competitors/vouching-invite-accountability.md). Frame as **vouching / sponsorship integrity**, not downline management.

## Current mechanics this interacts with

`rewardRoots` pays only ancestors above the trigger user, up to 10, with weights `[10000, 6000, 3600, …]` (~0.6^k) renormalized over whoever is present. `REFERRAL_ROOT` is never paid. The oracle handles register and skiplist per `groupId`. Skiplisting is per address; skipped addresses don't use up a level.

**Skiplisting someone today moves their ancestors one step closer, so those ancestors get larger shares.** That is the core problem: skiplisting a bad node *rewards its referrer*. The parent can move into the closest position and take up to 100% when only one ancestor remains. Sponsor accountability is needed just to remove this perverse incentive.

At minimum, when X is skiplisted for cause, X's referrer should not receive X's redistributed share. Options:

- (a) skip X's slot instead of collapsing it: leave a "dead" weight that goes to the trigger user or the treasury;
- (b) penalize the parent (one hop);
- (c) **decayed ancestor penalty on skiplist**, modeled on RepuLink's Backward Endorsement Penalty Propagation (Wu & Konstantinidis, KDD '26; [papers entry](../papers/referrer-accountability-social-collateral.md)). When X is skiplisted for cause, each ancestor at hop k is charged in proportion to γ^k, from a bond or from `rewardRoots` it already earned through X. Reuse the existing `[10000, 6000, 3600, …]` weights as γ^k and the 10-level cap as the hop bound K. RepuLink is reputation-only, uses synthetic endorsement data, and doesn't analyze Sybil attacks, so treat it as a model, not a validation.

## Who gets penalized, and how far it spreads

Every production system surveyed (Proof of Humanity, Ethos, Lobsters, Polkadot, EigenLayer) punishes the **direct sponsor only**. Recommended default:

| Who | Penalty |
|---|---|
| **Parent (1 hop)** | Fractional penalty (Ethos docks vouchers 20% of a successful slash; Lobsters disables invites) |
| **Grandparents (2–3 hops)** | Optional decayed penalty (e.g. reuse 0.6^k, capped at 2–3 hops). Academic model: RepuLink's BEPP (Wu & Konstantinidis, KDD '26) penalizes endorsers by γ^k per hop. No production precedent |
| **Siblings** | **Never** |
| **Descendants of the fraudulent node** | **Quarantine, not slash**: reparent to the grandparent or freeze pending review. Honest people invited by a fraud are victims (cf. Lobsters pruning only inactive/no-presence accounts) |

## Penalty steps, mildest first

1. Freeze invite rights.
2. Withhold or claw back `rewardRoots` earned *from that referee's* settles (mirrors Bryan–Karlan–Zinman and fintech clawbacks).
3. Time-limited reduction in the referrer's payout weight.
4. Skiplist the referrer — reserve for repeat offenses or ≥N bad invitees.

Proportionality: a referrer shouldn't lose more than they earned from the subtree plus a bounded stake.

## Bond window (~180 days), not lifetime liability

Ethos bonds the inviter to the invitee's score for about 180 days (their invite page also says "90 days" in one place — an internal inconsistency). Proof of Humanity ends voucher exposure at registration. Lifetime liability chills onboarding and lets attackers set traps. Prefer a per-group bonding period on the order of 180 days.

## Credit for self-policing

As in PoH (withdraw the vouch before Pending Registration) and Ethos (archive before resolution), let a referrer flag or skiplist their own invitee *before* an oracle ruling and escape the penalty. "Trust by Association" shows this creates an incentive to expel bad nodes.

## Protection against framing

An attacker can get invited by an honest user and then misbehave on purpose to hurt them. Mitigations:

- Cap liability at what the referrer earned from that referee.
- Penalties only for *categories the referrer could detect*. PoH penalizes Duplicate / DoesNotExist but not Incorrect Submission — a good model: Sybil/fake = sponsor liable; later conduct = mostly not.
- An appeal / dispute path (PoH uses Kleros; Ethos uses votes with accuser bonds).

## Sybil-farm limit, and a staked bond as the alternative

Penalties work only if referrers have something to lose. A Sybil farm owns the whole chain, so punishing the parent just hits another Sybil. Accountability helps where an *honest* node sits on the attack edge: it raises the cost of attack edges (good for SybilRank-style signals) but does nothing inside an all-attacker chain.

Combine with stake: a small invite bond per referee, released after the bonding period, slashed pro rata on cause; keep skiplist for the offender. Watch Cheng–Friedman: per-account penalties can be escaped by spreading invites across many fresh referrer accounts, so cap invites per address and make new referrers' invites inherit scrutiny.

Skiplisting is binary, free to the attacker, and (today) *pays* the ancestors. Slashing a bonded stake is graded, can compensate victims or the challenger, and is proven at scale (Polkadot and EigenLayer pro-rata delegator slashing).

## MLM optics

Upline liability for downline conduct *looks* like MLM commission chargebacks and can make the network seem like a hierarchy where you "manage your downline." FTC MLM analysis focuses on whether pay comes from recruitment versus real sales. Penalties don't change that line, but publishing "your recruits' conduct affects your earnings" invites the comparison.

Frame it as **vouching / sponsorship integrity** (PoH / Ethos language). Keep penalties tied to *fraud* (Sybil / duplicate) rather than *performance*. Never require referrers to "manage" referees. Not legal advice; needs counsel. See [mlm-pyramid-legal.md](../papers/mlm-pyramid-legal.md).

## Open questions

1. Should skiplisting X send X's share to the parent (current behavior), to the trigger user, or to the treasury? Needs a contract change either way.
2. One hop vs decaying k hops: is there data (testnet / sim) on how much extra deterrence the grandparent penalty buys compared with the chilling it causes?
3. What does the oracle count as "cause" (Sybil / duplicate only, or conduct), and who can appeal?
4. Bond size and duration per group: is it a per-group parameter?
5. Is "strictly required referral" compatible with permissionless onboarding? Who seeds the first generation, given `REFERRAL_ROOT` children are maximally powerful (up to 100% share)?
6. Can penalties be enforced on-chain (stake) or only via oracle-side skiplist / accounting?
7. Verify the remaining **(unverified)** items in the papers file before external use. RepuLink is now verified (KDD '26).
