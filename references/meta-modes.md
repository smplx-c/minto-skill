# Meta Modes

**Modes:** `analysis`, `critique`, `rewrite`

These three modes use Minto on material rather than producing a communication artifact from scratch. In all three, the structure is visible output — the user asked for the thinking, not for prose that hides it.

---

## `/minto analysis`

Use Minto primarily as a thinking tool. The goal is to determine what the available evidence actually means.

```text
Evidence → Observations → Logical Groups → Insights → Core Finding → Decision Implication
```

**Default output**, where each element is warranted:

* Core finding
* Supporting findings
* Evidence
* Assumptions
* Unresolved questions
* Decision implication
* Highest-value next analysis

Do not force a recommendation when the task is diagnostic. "Here is what the data supports, and here is what it does not yet settle" is a complete answer.

Apply the epistemic labels from `SKILL.md` explicitly here — separating fact from inference from assumption is most of this mode's value.

---

## `/minto critique`

Use to evaluate an existing argument, document, email, report, page, presentation, or piece of copy. **Do not rewrite unless the user asks.** Critique is reversible; an unrequested rewrite discards the user's version.

Evaluate:

* What is the apparent Core Question?
* Is there a clear Governing Thought, and does it answer that question?
* Does the answer come early enough?
* Does every Key Line support the Governing Thought?
* Does every parent summarize its children?
* Are siblings logically the same kind, at the same level of abstraction?
* Is each group logically ordered?
* Are groups reasonably MECE?
* Are findings, conclusions, and recommendations separated?
* Are claims supported by evidence, and do observations pass the So-What test?
* Is anything redundant, or repeated across levels?
* Are assumptions presented as facts?
* What single change would strengthen it most?

Prioritize structural problems over stylistic preferences, and lead with the most consequential finding rather than working through the document top to bottom.

---

## `/minto rewrite`

Use when existing material should be reorganized according to Minto. Construct the new pyramid internally **before** rewriting a single sentence.

* Preserve factual meaning and tone unless the user requests a change.
* Do not invent missing evidence — a gap in the source is a gap in the rewrite, and worth naming.
* Do not preserve source order when a better logical order exists.
* Promote hidden conclusions, group related arguments, demote supporting detail.
* Remove unnecessary repetition.
* Separate findings, conclusions, and recommendations.
* Keep useful nuance; concision that removes a qualification changes the meaning.

When the rewrite substantially reorders the material, add one short line naming what moved and why, so the user can check the change rather than diff two documents.
