# Intentional epistemic asymmetry: why the agent contract can never be complete

_Added 2026-11-13. Sources and full citations are in [papers/epistemic-dependence-incomplete-contracts.md](../papers/epistemic-dependence-incomplete-contracts.md). LightForest design references point to the private spec repo [MagRelo/lightforest-agents](https://github.com/MagRelo/lightforest-agents) (`docs/permissions.md`, `docs/preferences.md`, `docs/architecture.md`, `docs/open-questions.md`)._

**Thesis.** A LightForest user turns on an agent *because* it knows or can do more than they can. That gap is the point. It also means the user can never write down everything the agent should do, so the "social contract" of depending on an agent can't be a complete contract. Contract theory has argued for decades that contracts are necessarily incomplete (Simon 1951; Williamson 1979, 1985; Grossman & Hart 1986; Hart & Moore 1990; Hart 2017), and Hadfield-Menell & Hadfield (2019) carry the argument over to AI. What holds an incomplete relationship together is residual control, a relationship worth continuing, reputation, and visibility that calibrates trust. A longer spec doesn't. LightForest's design should invest there.

---

## 1. Definition

**Intentional epistemic asymmetry** is a principal deliberately delegating to an agent *because* the agent has knowledge, skill, attention or reach the principal lacks, and accepting that the principal can't fully specify or check what the agent does.

Nearby terms, and how this one differs:

| Term | Source | Relation |
|---|---|---|
| Information asymmetry | Akerlof 1970; Jensen & Meckling 1976 | Same structure, but economics usually treats it as a *cost* to minimize (agency costs: monitoring, bonding, residual loss). Here it is the *purpose* of the relationship. |
| Epistemic dependence | Hardwig 1985 | The closest philosophical match. Deferring to someone who knows more is rational, not a lapse in autonomy. |
| Division of cognitive labor | Kitcher 1990 | Specialization and the dependence it creates are how communities know more than any one member. |
| Credence goods | Darby & Karni 1973; Dulleck & Kerschbamer 2006 | The expert both diagnoses and treats, and the client may *never* learn whether they were served well. This names the risk the asymmetry brings. |
| Scalable oversight / weak-to-strong | Amodei et al. 2016; Bowman et al. 2022; Burns et al. 2023 | The AI framing: supervising "systems that potentially outperform us" (Bowman et al.). |

## 2. Why the asymmetry is intentional

- **It's what the user is paying for.** In LightForest, a user's agent quietly evaluates approved opportunities, negotiates with friends' agents, and acts inside a grant. If the user could do all that as well and as cheaply, they wouldn't need an agent. Deference is rational under Hardwig's argument, and the product exists to provide something the user doesn't have.
- **Removing it destroys the value.** If every decision has to be explained until the user understands it fully, the user is doing the work again. Agency theory's tools (incentives, monitoring, enforcement) still apply, but Kolt (2025) argues they may not work well for agents that decide fast and can't be interpreted. That pushes governance toward infrastructure, not line-by-line review.
- **Specialization scales.** Kitcher's argument applies to agent ecosystems. Many agents with different competences, deferring to each other's track records, can cover more ground than one generalist.

The design goal is therefore **calibrated** reliance (Lee & See 2004), avoiding both misuse (over-trust) and disuse (under-trust) (Parasuraman & Riley 1997). Shrinking the gap is not the goal.

## 3. Why the contract is incomplete

Three separate reasons. The distinction matters because Maskin & Tirole (1999) show that being unable to *describe* contingencies does not, by itself, justify incompleteness.

1. **Unforeseeable contingencies, and unforeseeable payoffs.** New opportunities, new counterparties and new social situations keep appearing. Users can't price outcomes they can't imagine, so it isn't just that they can't name them. Macneil (1978) calls fully specifying the future "presentiation" and argues long-term relations can't be presentiated. Simon (1951) explains why the employment relation hands over *authority to choose later* instead of listing tasks: the best action isn't knowable in advance.
2. **Unverifiability (the credence problem).** Even after the fact, the user often can't tell whether the agent did well. They don't see the opportunities it filtered out, the deals it declined, or how hard it negotiated. A term that can't be verified can't be enforced by contract, only by relationship and reputation (Baker, Gibbons & Murphy 2002). Dulleck & Kerschbamer (2006) show that inefficiency persists in credence markets unless liability, verifiability, price commitment or repeat interaction steps in.
3. **Bounded rationality.** Williamson (1985) states that "comprehensive contracting is not a realistic organizational alternative when provision for bounded rationality is made." Even when contingencies could be described, writing, reading and checking them all costs more than the user's attention allows. The Coasean frame in [product/overview.md](../product/overview.md) applies here too, as transaction costs inside the user–agent relationship.

Hadfield-Menell & Hadfield (2019) make the AI version explicit: any reward or instruction given to an AI is an incomplete contract. Human contracts work because **external structure** (culture, law, institutions) supplies implied terms for the gaps.

## 4. What fills the gap

| Mechanism | Literature | What it does |
|---|---|---|
| **Residual control rights and revocable grants** | Grossman & Hart 1986; Hart & Moore 1990; Hart 2017; Simon 1951 | When the contract is silent, someone has to decide. Whoever holds residual control decides, and the essential residual right is the **power to exclude**. A delegation should pair a bounded zone of agent discretion (Simon's "acceptable set") with the principal keeping the residual right and being able to revoke. |
| **Relational norms** | Macneil 1978; Williamson 1979; Baker, Gibbons & Murphy 2002 | Terms evolve through the ongoing relationship. Cooperation holds when the value of continuing beats the gain from defecting once, so keep the gain from any one deviation small and the future large. |
| **Reputation** | Akerlof 1970; Darby & Karni 1973; ERC-8004 | Repeated, visible track records counteract lemons and credence fraud, and turn one-off delegation into a repeated game. |
| **Observability as a trust instrument** | Lee & See 2004; Chan et al. 2024; Jensen & Meckling 1976 | Visibility (identifiers, real-time monitoring, activity logs) is there to **calibrate** trust and catch the unacceptable. It doesn't remove the asymmetry. A digest that tells the user *what* happened and *why it was in bounds* is enough. It doesn't need to teach the user to make the decision themselves. |
| **Credence-good safeguards** | Dulleck & Kerschbamer 2006 | Liability (escrow, refunds, slashable stake), verifiability (logs and receipts), up-front price commitment (fixed caps and fees), and repeat interaction. |
| **Scalable oversight** | Amodei et al. 2016; Irving et al. 2018; Bowman et al. 2022; Burns et al. 2023 | A weaker supervisor can still steer a stronger agent, through assisted judgment, debate, or weak labels. That steering is partial: Burns et al. find naive weak supervision recovers only part of the strong model's capability. |
| **Agent infrastructure** | Chan et al. 2025; Kolt 2025; Tomašev et al. 2026 | Shared, external protocols for attribution, shaping interactions, and detecting and remedying harm. These are the "external structure" Hadfield-Menell & Hadfield ask for. |

## 5. Implications for LightForest's design

Each current spec element, read through this lens:

- **Scoped session-key grant = residual control rights.** The passkey signs one grant (per-action cap of about $20, weekly cap of about $50, approved contracts, finite expiry), and the user can revoke it anytime (`docs/permissions.md`). Inside the grant is Simon's zone of acceptance, where the agent decides. Anything outside it (a bigger amount, a new contract, a new counterparty) goes back to the passkey holder as a push. That is the residual right in action. Revocation is Hart–Moore's power to exclude. Because the grant is **enforced by contract**, not by the agent promising to behave, it's a hard ceiling that holds even when the agent's judgment can't be checked.
- **Preferences and overrides = implied terms, written incrementally.** The profile and the overrides for single opportunities or tags (`docs/preferences.md`) are how the incomplete contract gets more complete over time, without anyone claiming it is complete. Resolution order (opportunity, then tag, then profile, then system defaults) supplies default terms for gaps, which is the role Hadfield-Menell & Hadfield give external structure. The rule that an auto-act cap can only **tighten** the grant keeps preferences from quietly widening residual control.
- **Feedback = weak-to-strong supervision plus relational adjustment.** Thumbs up or down with a "why", "less of this" and "mute" are weak labels on a stronger agent (Burns et al.) and the way terms adjust in a relational contract (Macneil). Learned notes stay hints until the user promotes them to overrides. That keeps the distinction between soft norms and hard terms.
- **Digest and push = calibrated observability.** In-scope actions go to the digest and out-of-scope ones get a push. These correspond to Chan et al.'s activity logging and real-time monitoring. The digest should report bounds and outcomes ("pledged $15 under your $20 cap to an approved contract"), not ask the user to reconstruct the reasoning. That is Lee & See's calibration goal.
- **ERC-8004 reputation = repeated game.** For bring-your-own and third-party agents, an ERC-8004 identity plus a feedback history turn single delegations into a reputation game (Akerlof, Darby & Karni, Baker–Gibbons–Murphy). The spec already notes that registration and whether 8004 is required before authorization are open (`docs/open-questions.md`).
- **Assurance-contract escrow and refunds = credence safeguards.** Refunding automatically when a threshold isn't met is the liability-and-verifiability side of Dulleck & Kerschbamer: the user doesn't have to judge the outcome to be made whole.
- **Positioning copy.** "Your agent knows things you don't, and that's the point. You always keep the off switch and the final say outside its limits." This also sharpens the existing framing that the site "keeps payment as a social contract" ([sota-solved-vs-open](sota-solved-vs-open.md)). The open problem is making discretion *legible and bounded*, not removing it.

## 6. Open questions

1. **Loyalty duty.** Agency law gives agents a duty of loyalty (Kolt 2025). Should LightForest's first-party agent publish a loyalty statement (the user before LightForest, before counterparties), and how would a user detect a breach of it if service quality is a credence good?
2. **What does the agent tell the user about what it filtered out?** Credence risk sits mostly in what the user *doesn't* see. Is a periodic "here's what I passed on and why" sample worth the noise?
3. **Self-enforcement math.** Baker–Gibbons–Murphy self-enforcement needs future value greater than the gain from one deviation. Are the default caps (about $20 per action, $50 per week) low enough for a bring-your-own agent with little reputation? Untested.
4. **Where does residual control go in multi-agent negotiations?** When two users' agents agree on something neither grant explicitly covers, whose residual right applies? The current rule is that anything out of scope is a push to *each* passkey. Is that enough?
5. **Reputation portability vs. privacy.** ERC-8004 feedback is public. How much about a user's delegation history should be visible, and to whom?
6. **Escalation thresholds as contract terms.** The push vs. digest thresholds are placeholders (`docs/open-questions.md`). Is there a principled way to set them, for example from value at risk, in line with ERC-8004's "security proportional to value at risk"?
7. **Maskin–Tirole objection.** Is there any LightForest decision where payoffs *are* foreseeable, so we should write a complete rule instead of relying on discretion? Fixed-price referrals are a candidate.
8. **Verification gaps in this page.** Some philosophy and early-economics summaries (Hardwig, Kitcher, Simon) rest on general knowledge of those works rather than a re-read this session, and are marked as such in the papers file. Kolt's final journal citation is **(unverified)**.
