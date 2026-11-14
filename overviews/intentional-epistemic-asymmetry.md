# Intentional epistemic asymmetry: why the agent contract can never be complete

_Added 2026-11-13. Sources and full citations are in [papers/epistemic-dependence-incomplete-contracts.md](../papers/epistemic-dependence-incomplete-contracts.md)._

**Thesis.** A principal delegates to an agent, human or AI, *because* it knows or can do more than they can. That gap is the point. It also means the principal can never write down everything the agent should do, so the "social contract" of depending on an agent can't be a complete contract. Contract theory has argued for decades that contracts are necessarily incomplete (Simon 1951; Williamson 1979, 1985; Grossman & Hart 1986; Hart & Moore 1990; Hart 2017), and Hadfield-Menell & Hadfield (2019) carry the argument over to AI. What holds an incomplete relationship together is residual control, a relationship worth continuing, reputation, and visibility that calibrates trust. A longer spec doesn't.

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

- **It's what the principal is paying for.** An agent that searches, evaluates, negotiates and acts is worth delegating to only because the principal can't do all that as well or as cheaply. Deference is rational under Hardwig's argument, and the delegation exists to provide something the principal doesn't have.
- **Removing it destroys the value.** If every decision has to be explained until the principal understands it fully, the principal is doing the work again. Agency theory's tools (incentives, monitoring, enforcement) still apply, but Kolt (2025) argues they may not work well for agents that decide fast and can't be interpreted. That pushes governance toward infrastructure, not line-by-line review.
- **Specialization scales.** Kitcher's argument applies to agent ecosystems. Many agents with different competences, deferring to each other's track records, can cover more ground than one generalist.

The design goal is therefore **calibrated** reliance (Lee & See 2004), avoiding both misuse (over-trust) and disuse (under-trust) (Parasuraman & Riley 1997). Shrinking the gap is not the goal.

## 3. Why the contract is incomplete

Three separate reasons. The distinction matters because Maskin & Tirole (1999) show that being unable to *describe* contingencies does not, by itself, justify incompleteness.

1. **Unforeseeable contingencies, and unforeseeable payoffs.** New opportunities, new counterparties and new social situations keep appearing. Principals can't price outcomes they can't imagine, so it isn't just that they can't name them. Macneil (1978) calls fully specifying the future "presentiation" and argues long-term relations can't be presentiated. Simon (1951) explains why the employment relation hands over *authority to choose later* instead of listing tasks: the best action isn't knowable in advance.
2. **Unverifiability (the credence problem).** Even after the fact, the principal often can't tell whether the agent did well. They don't see the opportunities it filtered out, the deals it declined, or how hard it negotiated. A term that can't be verified can't be enforced by contract, only by relationship and reputation (Baker, Gibbons & Murphy 2002). Dulleck & Kerschbamer (2006) show that inefficiency persists in credence markets unless liability, verifiability, price commitment or repeat interaction steps in.
3. **Bounded rationality.** Williamson (1985) states that "comprehensive contracting is not a realistic organizational alternative when provision for bounded rationality is made." Even when contingencies could be described, writing, reading and checking them all costs more than the principal's attention allows. The Coasean frame in [product/overview.md](../product/overview.md) applies here too, as transaction costs inside the principal–agent relationship.

Hadfield-Menell & Hadfield (2019) make the AI version explicit: any reward or instruction given to an AI is an incomplete contract. Human contracts work because **external structure** (culture, law, institutions) supplies implied terms for the gaps.

## 4. What fills the gap

| Mechanism | Literature | What it does |
|---|---|---|
| **Residual control rights and revocable grants** | Grossman & Hart 1986; Hart & Moore 1990; Hart 2017; Simon 1951 | When the contract is silent, someone has to decide. Whoever holds residual control decides, and the essential residual right is the **power to exclude**. A delegation should pair a bounded zone of agent discretion (Simon's "acceptable set") with the principal keeping the residual right and being able to revoke. |
| **Relational norms** | Macneil 1978; Williamson 1979; Baker, Gibbons & Murphy 2002 | Terms evolve through the ongoing relationship. Cooperation holds when the value of continuing beats the gain from defecting once, so keep the gain from any one deviation small and the future large. |
| **Reputation** | Akerlof 1970; Darby & Karni 1973; ERC-8004 | Repeated, visible track records counteract lemons and credence fraud, and turn one-off delegation into a repeated game. |
| **Observability as a trust instrument** | Lee & See 2004; Chan et al. 2024; Jensen & Meckling 1976 | Visibility (identifiers, real-time monitoring, activity logs) is there to **calibrate** trust and catch the unacceptable. It doesn't remove the asymmetry. A record of *what* happened and *why it was in bounds* is enough. It doesn't need to teach the principal to make the decision themselves. |
| **Credence-good safeguards** | Dulleck & Kerschbamer 2006 | Liability (escrow, refunds, slashable stake), verifiability (logs and receipts), up-front price commitment (fixed caps and fees), and repeat interaction. |
| **Scalable oversight** | Amodei et al. 2016; Irving et al. 2018; Bowman et al. 2022; Burns et al. 2023 | A weaker supervisor can still steer a stronger agent, through assisted judgment, debate, or weak labels. That steering is partial: Burns et al. find naive weak supervision recovers only part of the strong model's capability. |
| **Agent infrastructure** | Chan et al. 2025; Kolt 2025; Tomašev et al. 2026 | Shared, external protocols for attribution, shaping interactions, and detecting and remedying harm. These are the "external structure" Hadfield-Menell & Hadfield ask for. |

## 5. Implications for the agent-delegation landscape

What the literature suggests for anyone building delegation, incentive-exchange or agent-commerce systems:

- **Design who decides, not just what is decided.** Bounded, revocable authority beats an exhaustive spec. Give the agent a zone of discretion (Simon's acceptable set: caps, counterparties, expiry) and leave the residual right, including revocation (Hart–Moore's power to exclude), with the principal. Authority that is enforced mechanically, for example by a permission or spending limit the agent can't exceed, holds even when the agent's judgment can't be checked.
- **Let terms accumulate instead of front-loading them.** Contracts in long relations get filled in through use (Macneil). Defaults, preferences and precedents act as the implied terms Hadfield-Menell & Hadfield attribute to external structure. Additions should only narrow the agent's authority unless the principal explicitly widens it.
- **Treat principal feedback as weak supervision.** Ratings and corrections can steer a stronger agent (Burns et al.; Bowman et al.) and are how relational terms adjust, but they are partial. Don't treat them as a complete specification.
- **Build observability for calibration, not replication.** Logs, receipts and escalation (Chan et al.'s identifiers, monitoring and logging) should show *what happened and that it was in bounds*, so trust matches capability (Lee & See). They don't need to let the principal reconstruct or redo the decision.
- **Use credence-good safeguards.** Liability (escrow, stake, refunds), verifiability (receipts, logs), price commitment (fees and caps fixed up front) and repeat interaction are the institutions that discipline experts whose quality can't be judged (Dulleck & Kerschbamer).
- **Make the relationship worth more than any single defection.** Relational contracts self-enforce only when continuation value beats the one-time gain (Baker, Gibbons & Murphy). Small per-action exposure plus portable reputation (Akerlof; Darby & Karni; open registries like ERC-8004) delivers both halves.
- **Frame it honestly.** "The agent knows things you don't, and that's the point; you keep the off switch and the final say outside its limits." This matches this repo's broader framing that payment stays a social contract ([sota-solved-vs-open](sota-solved-vs-open.md)): the open problem is making discretion *legible and bounded*, not removing it.

## 6. Open questions

1. **Loyalty duty.** Agency law gives agents a duty of loyalty (Kolt 2025). Should agent operators publish a loyalty statement (principal before platform, before counterparties), and how would a principal detect a breach if service quality is a credence good?
2. **Disclosing what was filtered out.** Credence risk sits mostly in what the principal *doesn't* see. Is a periodic "here's what I passed on and why" sample worth the noise?
3. **Self-enforcement math.** Baker–Gibbons–Murphy self-enforcement needs future value greater than the gain from one deviation. How should per-action and per-period exposure caps scale with an agent's reputation? Little empirical work exists for AI agents.
4. **Residual control in multi-agent deals.** When two principals' agents agree on something neither delegation covers, whose residual right applies, and does escalating to both principals scale?
5. **Reputation portability vs. privacy.** Open reputation records (e.g. ERC-8004 feedback) are public. How much of a principal's or agent's delegation history should be visible, and to whom?
6. **Escalation thresholds as contract terms.** Is there a principled way to set when an agent must ask, for example from value at risk, in line with ERC-8004's "security proportional to value at risk"?
7. **Maskin–Tirole objection.** Where *are* payoffs foreseeable enough that a complete rule should replace discretion? Fixed-price, verifiable tasks such as flat referral fees are candidates.
8. **Verification gaps in this page.** Some philosophy and early-economics summaries (Hardwig, Kitcher, Simon) rest on general knowledge of those works rather than a re-read this session, and are marked as such in the papers file. Kolt's final journal citation is **(unverified)**.
