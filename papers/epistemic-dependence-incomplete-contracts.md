# Epistemic dependence and incomplete contracts

Literature for **intentional epistemic asymmetry**: you delegate to an agent *because* it knows or can do more than you, so the terms of that delegation can never be fully written down. Scope covers philosophy of epistemic dependence, credence goods, principal–agent theory, incomplete and relational contracts, trust in automation, AI oversight, and 2024–2026 work on governing AI agents. The topic synthesis is [overviews/intentional-epistemic-asymmetry.md](../overviews/intentional-epistemic-asymmetry.md).

**Category takeaway:** two literatures that rarely cite each other reach the same conclusion. Philosophy (Hardwig, Kitcher) says relying on someone who knows more than you is rational, and that you can't fully check them. Contract theory (Simon, Williamson, Grossman–Hart–Moore, Baker–Gibbons–Murphy) says complete contracts are impossible once rationality is bounded and contingencies can't be foreseen or verified. What fills the gap is residual control rights, relationships that are worth more continued than broken, and reputation. Hadfield-Menell & Hadfield (2019) connect the two for AI. For the agent-delegation landscape this means no principal–agent relationship can rest on a perfect spec. It rests on bounded, revocable authority, on feedback and reputation, and on visibility that keeps trust calibrated without trying to close the knowledge gap.

Links checked 2026-11-13. "Verified via Crossref" means the DOI resolves and the metadata matches. "Verified on arXiv" means the abs page and its metadata match. Summaries are of each work's central argument. Where a summary rests on general knowledge of the work rather than a re-read this session, it says so.

---

## A. Epistemic dependence (philosophy)

### Epistemic Dependence
- **Citation:** John Hardwig. *Epistemic Dependence.* The Journal of Philosophy 82(7), 1985, pp. 335ff.
- **Link:** <https://doi.org/10.2307/2026523> (verified via Crossref)
- **Summary:** Laypeople, and experts outside their own field, often have good reason to believe things they can't check themselves, purely because an expert believes them. Hardwig argues this deference is rational, not a failure of epistemic autonomy. Much of modern knowledge is held by communities rather than individuals, so the rational move is often to depend on someone else rather than think it through yourself. (Summary from general knowledge of the paper; not re-read this session.)
- **Implication:** an agent's knowledge advantage is the reason to use it, not a defect to engineer away. Delegation designs should treat "the principal can't check everything" as the normal case.

### The Division of Cognitive Labor
- **Citation:** Philip Kitcher. *The Division of Cognitive Labor.* The Journal of Philosophy 87(1), 1990, pp. 5ff.
- **Link:** <https://doi.org/10.2307/2026796> (verified via Crossref)
- **Summary:** Models how a scientific community should spread its effort across competing approaches. A community can do better when individuals specialize, sometimes on approaches that look less promising to them, than when everyone pursues the current best bet. Specialization, and the dependence on others that comes with it, is a feature of how collective knowledge is built. (Summary from general knowledge of the paper.)
- **Implication:** many specialized agents deferring to each other's competence is a sound ecosystem shape, provided a reputation layer (section F) steers deference toward agents that have earned it.

---

## B. Information asymmetry, agency and credence goods (economics)

### The Market for "Lemons": Quality Uncertainty and the Market Mechanism
- **Citation:** George A. Akerlof. *The Market for "Lemons": Quality Uncertainty and the Market Mechanism.* Quarterly Journal of Economics 84(3), 1970, pp. 488ff.
- **Link:** <https://doi.org/10.2307/1879431> (verified via Crossref)
- **Summary:** When sellers know quality and buyers don't, average-price buying drives out high quality, and markets can unravel. Guarantees, brands and licensing are institutions that counteract this.
- **Implication:** a market of agents nobody can tell apart unravels the same way. Public track records and attestations are the equivalent of brands and warranties.

### Theory of the Firm: Managerial Behavior, Agency Costs and Ownership Structure
- **Citation:** Michael C. Jensen, William H. Meckling. *Theory of the firm: Managerial behavior, agency costs and ownership structure.* Journal of Financial Economics 3(4), 1976, pp. 305–360.
- **Link:** <https://doi.org/10.1016/0304-405X(76)90026-X> (verified via Crossref)
- **Summary:** Defines the agency relationship as a principal delegating decision authority to an agent. It breaks agency costs into the principal's monitoring costs, the agent's bonding costs, and the residual loss that remains after both.
- **Implication:** spending caps and scoped permissions work as bonding, and activity logs work as monitoring. Some residual loss is expected in any delegation and should be bounded, not assumed to be zero.

### Free Competition and the Optimal Amount of Fraud
- **Citation:** Michael R. Darby, Edi Karni. *Free Competition and the Optimal Amount of Fraud.* Journal of Law and Economics 16(1), 1973, pp. 67–88.
- **Link:** <https://doi.org/10.1086/466756> (verified via Crossref)
- **Summary:** Introduces **credence qualities**: attributes a buyer can't evaluate even after buying, because the seller also diagnoses what the buyer needs (the standard example is repairs). Some fraud persists even in competitive equilibrium, and reputation and client relationships limit it.
- **Implication:** an agent that decides *which* options a principal ever sees is selling a credence good. The principal may never learn what was filtered out, so outcomes alone don't reveal quality.

### On Doctors, Mechanics, and Computer Specialists: The Economics of Credence Goods
- **Citation:** Uwe Dulleck, Rudolf Kerschbamer. *On Doctors, Mechanics, and Computer Specialists: The Economics of Credence Goods.* Journal of Economic Literature 44(1), 2006, pp. 5–42.
- **Link:** <https://doi.org/10.1257/002205106776162717> (verified via Crossref)
- **Summary:** A unifying model of credence-goods markets. It classifies the frauds as overtreatment, undertreatment and overcharging, and shows which institutional assumptions remove them: liability for the outcome, verifiability of what was done, commitment to prices, and repeat interaction or reputation. If none of them hold, the inefficiency persists.
- **Implication:** a checklist for agent safeguards: verifiability (logs, receipts), liability (escrow, stake, refunds), price commitment (fees and caps fixed up front), and reputation (repeat interaction).

---

## C. Incomplete contracts and residual control (economics)

### A Formal Theory of the Employment Relationship
- **Citation:** Herbert A. Simon. *A Formal Theory of the Employment Relationship.* Econometrica 19(3), 1951, pp. 293ff.
- **Link:** <https://doi.org/10.2307/1906815> (verified via Crossref)
- **Summary:** An employment contract differs from a sales contract because the worker accepts the employer's *authority* to choose later, within an agreed set of acceptable behaviors, which task they do. This is efficient when the best action can't be known in advance. (Summary from general knowledge of the paper.)
- **Implication:** scoped delegation to an agent has the same shape. The principal fixes the set of acceptable actions (caps, counterparties, expiry), and the agent chooses within it as information arrives.

### Transaction-Cost Economics: The Governance of Contractual Relations
- **Citation:** Oliver E. Williamson. *Transaction-Cost Economics: The Governance of Contractual Relations.* Journal of Law and Economics 22(2), 1979, pp. 233–261.
- **Link:** <https://doi.org/10.1086/466942> (verified via Crossref)
- **Summary:** Matches governance structures (market, bilateral and unified/hierarchical governance) to transactions based on uncertainty, frequency, and how specific the investments are. Builds on Macneil's classical, neoclassical and relational contracting.
- **Implication:** recurring, high-uncertainty delegation is a case for relational and bilateral governance (ongoing authority, feedback, dispute paths), not one-shot spot contracts.

### The Economic Institutions of Capitalism
- **Citation:** Oliver E. Williamson. *The Economic Institutions of Capitalism: Firms, Markets, Relational Contracting.* Free Press, 1985.
- **Link:** <https://papers.ssrn.com/sol3/papers.cfm?abstract_id=1496720> (SSRN listing; publisher and year confirmed in library catalog records)
- **Summary:** Assumes **bounded rationality** (people are "intendedly rational, but only limitedly so") and **opportunism**. It states plainly that "comprehensive contracting is not a realistic organizational alternative when provision for bounded rationality is made" (ch. 2, p. 46 in the reprint we checked). Governance after the contract is signed does the work the contract can't.
- **Implication:** the thesis in one line. Effort spent on governance after the delegation (revocation, feedback, disputes) beats effort spent on a longer spec.

### Contracts: Adjustment of Long-Term Economic Relations under Classical, Neoclassical, and Relational Contract Law
- **Citation:** Ian R. Macneil. *Contracts: Adjustment of Long-Term Economic Relations under Classical, Neoclassical, and Relational Contract Law.* Northwestern University Law Review 72(6), 1978, pp. 854–905.
- **Link:** no DOI. Citation confirmed from the HeinOnline scan header ("72 Nw. U. L. Rev. 854", Vol. 72 No. 6, © 1978) and later citations, e.g. <https://archives.law.nccu.edu/cgi/viewcontent.cgi?article=1361&context=ncclr>
- **Summary:** Contrasts discrete, fully specified ("presentiated") transactions with long-term relations in which planning is necessarily incomplete. In those relations, adjustment happens through processes and norms of the relationship rather than through the original text.
- **Implication:** principal–agent relationships with agents are relational, not discrete. Their terms evolve through use, and systems should expect that.

### The Costs and Benefits of Ownership: A Theory of Vertical and Lateral Integration
- **Citation:** Sanford J. Grossman, Oliver D. Hart. *The Costs and Benefits of Ownership: A Theory of Vertical and Lateral Integration.* Journal of Political Economy 94(4), 1986, pp. 691–719.
- **Link:** <https://doi.org/10.1086/261404> (verified via Crossref)
- **Summary:** When it's too costly to list every specific right over an asset in a contract, ownership means holding the **residual rights of control**: the right to decide anything the contract leaves out. How those rights are allocated shapes each party's incentive to invest.
- **Implication:** in any delegation, the question is who decides when the terms are silent. Default answer: residual control stays with the principal.

### Property Rights and the Nature of the Firm
- **Citation:** Oliver Hart, John Moore. *Property Rights and the Nature of the Firm.* Journal of Political Economy 98(6), 1990, pp. 1119–1158.
- **Link:** <https://doi.org/10.1086/261729> (verified via Crossref)
- **Summary:** Generalizes Grossman–Hart to many agents and assets. The essential residual right is the **power to exclude** others from using an asset.
- **Implication:** revocation is the power to exclude. Being able to cut an agent off from the principal's funds and identity is the core control right.

### Foundations of Incomplete Contracts
- **Citation:** Oliver Hart, John Moore. *Foundations of Incomplete Contracts.* Review of Economic Studies 66(1), 1999, pp. 115–138.
- **Link:** <https://doi.org/10.1111/1467-937X.00080> (verified via Crossref)
- **Summary:** Replies to the critique below and defends incompleteness as a primitive when contingencies are complex and hard to describe.

### Unforeseen Contingencies and Incomplete Contracts
- **Citation:** Eric Maskin, Jean Tirole. *Unforeseen Contingencies and Incomplete Contracts.* Review of Economic Studies 66(1), 1999, pp. 83–114.
- **Link:** <https://doi.org/10.1111/1467-937X.00079> (verified via Crossref)
- **Summary:** **The counterpoint.** If parties can foresee their *payoffs*, even without being able to describe the physical contingencies, mechanism design can in principle reach the complete-contract outcome. Being unable to describe a contingency doesn't by itself justify incomplete contracts.
- **Implication:** be precise about *why* agent contracts are incomplete. It isn't just that cases can't be described. Payoffs aren't foreseeable, outcomes can't be verified (credence), and principals are boundedly rational. Those reasons survive Maskin–Tirole.

### Incomplete Contracts: Where Do We Stand?
- **Citation:** Jean Tirole. *Incomplete Contracts: Where Do We Stand?* Econometrica 67(4), 1999, pp. 741–781.
- **Link:** <https://doi.org/10.1111/1468-0262.00052> (verified via Crossref)
- **Summary:** A survey of the incomplete-contracts debate and its foundations, including bounded rationality as a possible basis.

### Incomplete Contracts and Control (Nobel lecture)
- **Citation:** Oliver Hart. *Incomplete Contracts and Control.* Prize Lecture, Sveriges Riksbank Prize in Economic Sciences, 2016; published in American Economic Review 107(7), 2017, pp. 1731–1752.
- **Link:** <https://doi.org/10.1257/aer.107.7.1731> (verified via Crossref) · lecture page <https://www.nobelprize.org/prizes/economic-sciences/2016/hart/lecture/> (verified; the title matches)
- **Summary:** Hart's own synthesis. Contracts are inevitably incomplete, so the allocation of control (who decides when the contract is silent) is central to organization. He also reviews later work on contracts as reference points.
- **Implication:** the cleanest single citation for "you can never spell out the full contract, so design who decides."

### Relational Contracts and the Theory of the Firm
- **Citation:** George Baker, Robert Gibbons, Kevin J. Murphy. *Relational Contracts and the Theory of the Firm.* Quarterly Journal of Economics 117(1), 2002, pp. 39–84.
- **Link:** <https://doi.org/10.1162/003355302753399445> (verified via Crossref)
- **Summary:** Relational contracts are informal agreements that rest on outcomes too subjective to enforce in court. They are self-enforcing because the value of continuing the relationship beats the one-time gain from reneging. Ownership structure changes those reneging temptations.
- **Implication:** agents and their operators have to value the ongoing relationship more than any single exploit. Keep the gain from any one deviation small (caps) and the future value large (reputation, repeat business).

---

## D. Trust in automation (human factors)

### Humans and Automation: Use, Misuse, Disuse, Abuse
- **Citation:** Raja Parasuraman, Victor Riley. *Humans and Automation: Use, Misuse, Disuse, Abuse.* Human Factors 39(2), 1997, pp. 230–253.
- **Link:** <https://doi.org/10.1518/001872097778543886> (verified via Crossref)
- **Summary:** Separates *misuse* (over-reliance), *disuse* (under-reliance) and *abuse* (automating without regard for the operator).

### Trust in Automation: Designing for Appropriate Reliance
- **Citation:** John D. Lee, Katrina A. See. *Trust in Automation: Designing for Appropriate Reliance.* Human Factors 46(1), 2004, pp. 50–80.
- **Link:** <https://doi.org/10.1518/hfes.46.1.50.30392> (verified via Crossref)
- **Summary:** Trust guides reliance when people can't fully understand automation. The design goal is **calibrated** trust that matches actual capability, not maximal trust. Displaying the automation's performance, process and purpose helps calibration.
- **Implication:** observability is a calibration tool. Logs and explanations exist so principals trust agents the right amount, not to teach principals to do the agent's job.

---

## E. AI oversight when the agent knows more

### Concrete Problems in AI Safety
- **Citation:** Dario Amodei, Chris Olah, Jacob Steinhardt, Paul Christiano, John Schulman, Dan Mané. *Concrete Problems in AI Safety.* arXiv:1606.06565, 2016.
- **Link:** <https://arxiv.org/abs/1606.06565> (verified on arXiv)
- **Summary:** Lists five practical accident-risk problems. One is the case of an objective "too expensive to evaluate frequently". The abstract calls it "scalable supervision" and the body section uses the now-standard name, **scalable oversight**.

### AI safety via debate
- **Citation:** Geoffrey Irving, Paul Christiano, Dario Amodei. *AI safety via debate.* arXiv:1805.00899, 2018.
- **Link:** <https://arxiv.org/abs/1805.00899> (verified on arXiv)
- **Summary:** Proposes having two agents debate while a less capable human judges, as a way to oversee answers the human couldn't produce alone.

### Measuring Progress on Scalable Oversight for Large Language Models
- **Citation:** Samuel R. Bowman, Jeeyoon Hyun, Ethan Perez, et al. *Measuring Progress on Scalable Oversight for Large Language Models.* arXiv:2211.03540, 2022.
- **Link:** <https://arxiv.org/abs/2211.03540> (verified on arXiv)
- **Summary:** Defines scalable oversight as "the problem of supervising systems that potentially outperform us on most skills relevant to the task at hand." The experimental design uses tasks where specialists succeed but unaided humans and current models fail. On MMLU and time-limited QuALITY, humans chatting with an unreliable LLM assistant "substantially outperform both the model alone and their own unaided performance."
- **Implication:** the principal-plus-agent pair can beat either alone. That supports "approve with context" over both "approve everything" and "never ask."

### Weak-to-Strong Generalization: Eliciting Strong Capabilities With Weak Supervision
- **Citation:** Collin Burns, Pavel Izmailov, Jan Hendrik Kirchner, Bowen Baker, Leo Gao, Leopold Aschenbrenner, Yining Chen, Adrien Ecoffet, Manas Joglekar, Jan Leike, Ilya Sutskever, Jeff Wu. arXiv:2312.09390, 2023.
- **Link:** <https://arxiv.org/abs/2312.09390> (verified on arXiv)
- **Summary:** Asks whether weak supervisors can elicit the capabilities of stronger models. Strong models fine-tuned on weak labels consistently beat their weak supervisors ("weak-to-strong generalization"), but naive fine-tuning is still far from recovering their full capability. With an auxiliary confidence loss, a GPT-2-level supervisor gets GPT-4 to near GPT-3.5-level performance on NLP tasks.
- **Implication:** principal feedback is weak supervision of a stronger agent. It can steer without the principal being as capable, but it shouldn't be treated as complete.

### Incomplete Contracting and AI Alignment (key bridge)
- **Citation:** Dylan Hadfield-Menell, Gillian K. Hadfield. *Incomplete Contracting and AI Alignment.* Proceedings of the 2019 AAAI/ACM Conference on AI, Ethics, and Society (AIES '19), pp. 417–422.
- **Link:** <https://doi.org/10.1145/3306618.3314250> (verified via Crossref) · <https://arxiv.org/abs/1804.04268> (verified on arXiv)
- **Summary:** Treats AI misalignment as an incomplete-contracting problem: the reward or instructions we give an AI are always an incomplete contract. Their core contribution is that human contracts work because of **external structure**, institutions like culture and law that supply implied terms to fill the gaps. They propose research on AI that can connect an incomplete instruction to that supporting structure.
- **Implication:** the bridge citation for the thesis. An agent's instructions are always incomplete, so whoever runs an agent ecosystem has to supply the "external structure" (norms, defaults, reputation, dispute paths) that fills the gaps.

---

## F. Agent governance and delegation (2024–2026)

### Visibility into AI Agents
- **Citation:** Alan Chan, Carson Ezell, Max Kaufmann, Kevin Wei, Lewis Hammond, Herbie Bradley, Emma Bluemke, Nitarshan Rajkumar, David Krueger, Noam Kolt, Lennart Heim, Markus Anderljung. arXiv:2401.13138, 2024; accepted to ACM FAccT 2024 (per arXiv comment).
- **Link:** <https://arxiv.org/abs/2401.13138> (verified on arXiv)
- **Summary:** Defines *visibility* as information about where, why, how and by whom agents are used. It assesses three measures, agent identifiers, real-time monitoring and activity logging, each with versions that range from less to more intrusive and informative.
- **Implication:** a ready taxonomy for agent oversight: identifiers (who is acting), real-time monitoring (escalation), activity logging (after-the-fact review).

### Infrastructure for AI Agents
- **Citation:** Alan Chan, Kevin Wei, Sihao Huang, Nitarshan Rajkumar, Elija Perrier, Seth Lazar, Gillian K. Hadfield, Markus Anderljung. arXiv:2501.10114, 2025; accepted to TMLR (per arXiv comment).
- **Link:** <https://arxiv.org/abs/2501.10114> (verified on arXiv)
- **Summary:** Proposes **agent infrastructure**, shared protocols outside agents, with three functions: attribution (tying actions to agents and users), shaping interactions, and detecting and remedying harm.
- **Implication:** the "external structure" Hadfield-Menell & Hadfield call for, made concrete. Permission grants, escrow and reputation registries are agent infrastructure.

### Governing AI Agents
- **Citation:** Noam Kolt. *Governing AI Agents.* arXiv:2501.07913, 2025; Notre Dame Law Review Vol. 101, forthcoming per arXiv comment (final citation **(unverified)**).
- **Link:** <https://arxiv.org/abs/2501.07913> (verified on arXiv)
- **Summary:** Uses principal–agent theory and the common law of agency to characterize problems with AI agents: information asymmetry, discretionary authority and loyalty. It argues the usual fixes (incentives, monitoring, enforcement) may fail for fast, uninterpretable agents, and calls for infrastructure built on inclusivity, visibility and liability.
- **Implication:** grounds the "agent" in agency law. Loyalty to the principal, as opposed to the platform or counterparties, is a duty agent operators may need to state explicitly.

### Intelligent AI Delegation
- **Citation:** Nenad Tomašev, Matija Franklin, Simon Osindero. *Intelligent AI Delegation.* arXiv:2602.11865, 2026.
- **Link:** <https://arxiv.org/abs/2602.11865> (verified on arXiv; preprint, not peer reviewed)
- **Summary:** Proposes an adaptive delegation framework. Delegation is treated as a sequence of decisions that transfer authority, responsibility and accountability, with clear roles and boundaries, clarity of intent, and mechanisms for building trust, among humans and AI agents.
- **Implication:** a recent framework treating delegation as transfer of authority plus trust mechanisms. Worth tracking as the "agentic web" delegation literature matures.

### ERC-8004: Trustless Agents
- **Citation:** Marco De Rossi, Davide Crapis, Jordan Ellis, Erik Reppel. *ERC-8004: Trustless Agents.* Ethereum ERC, created 2025-08-13, status **Draft** (as of 2026-11-13).
- **Link:** <https://eips.ethereum.org/EIPS/eip-8004> (verified)
- **Summary:** Identity, Reputation and Validation registries for finding agents and establishing trust "without pre-existing trust". Trust models are pluggable and tiered "with security proportional to value at risk": client-feedback reputation, stake-secured re-execution, zkML, or TEE oracles.
- **Implication:** an open reputation and validation layer that turns one-off delegation into a repeated game.

---

## Backlog (not yet verified or filed)
- Kenneth J. Arrow, "Uncertainty and the Welfare Economics of Medical Care," AER 53(5), 1963: physician–patient trust under information asymmetry. **(unverified; DOI not found via Crossref this session)**
- John Hardwig, "The Role of Trust in Knowledge," Journal of Philosophy 88(12), 1991. **(unverified)**
- Gillian K. Hadfield, Barry R. Weingast, work on normative infrastructure and AI. **(unverified; find specific paper)**
