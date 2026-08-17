# Tier A Renderers

**Modes:** `mail`, `memo`, `report`, `proposal`, `executive`

In Tier A, Minto controls both the reasoning and the visible communication structure. The artifact should read as the pyramid reads: answer first, then reasons, then evidence.

Apply the output contract from `SKILL.md` — at Standard and Deep depth, append a compact structure note (Governing Thought + Key Lines) after the artifact.

---

## `/minto mail`

Use for emails and email replies. The goal is to deliver the answer quickly and make the reasoning easy to scan.

```text
Answer / Decision → 1–3 most important reasons → Necessary detail → Next action
```

* Lead with the answer, request, recommendation, or decision.
* Keep background shorter than reasoning.
* Use only as many arguments as necessary — a mail with two real reasons beats one with four padded ones.
* Do not reproduce the sender's chronology; the order of their message is not the order of your argument.
* Put operational detail below the central message.
* Make the requested next step explicit when relevant.
* Do not expose a formal pyramid unless requested.

The recipient should understand the core message from the opening paragraph alone.

---

## `/minto memo`

Use for decision memos, strategy memos, internal recommendations, and management notes.

```text
Recommendation → Rationale / Key Lines → Evidence → Risks / Qualifications → Decision or Next Step
```

Use visible headings when they aid navigation. Maintain a strong separation between recommendation, rationale, evidence, risk, and action — collapsing these is the most common failure in internal writing.

A memo differs from a `report` in evidentiary weight, not in structure: the memo asks for a decision, the report documents an analysis. If the user needs a decision and the evidence is already agreed, prefer `memo`.

---

## `/minto report`

Use for analytical, strategic, business, research, or performance reports. The goal is that a reader can understand the conclusion at executive depth, then inspect deeper evidence selectively.

```text
Executive Summary → Governing Thought → Key Findings / Key Lines → Supporting Analysis
→ Evidence → Implications → Recommendations → Next Steps
```

* Use SCQA where it improves framing.
* Never organize the report in the chronological order the analysis was performed.
* Prefer message-based section headings over generic topic labels.

| | |
| --- | --- |
| Bad heading | Mobile Performance |
| Better heading | Mobile accounts for most of the conversion decline |

---

## `/minto proposal`

Use for proposals, offers, project recommendations, scopes, and commercial recommendations.

```text
Client Need / Question → Proposed Answer → Why this approach → Expected value
→ Scope / Method → Risk control → Commercial terms → Next Step
```

* Lead with the proposed outcome, not the provider biography.
* Explain why the approach fits the client's actual problem — a generic method description is not a rationale.
* Separate value from scope, and scope from pricing. Blending them makes the price impossible to evaluate.
* Make assumptions and exclusions visible where material.
* Do not manufacture business impact figures. If a value estimate depends on the client's own numbers, say which ones.

---

## `/minto executive`

Use for executive summaries, board-level briefs, leadership updates, and highly compressed decision communication.

```text
Answer → 2–4 Key Lines → Critical qualification or risk → Required decision / next action
```

Remove supporting detail that is not necessary for the decision. Do **not** remove nuance that could materially change the decision — compression that hides a risk is a failure, not brevity.

The reader should understand the full decision logic in minimal time, and should be able to act on it without asking a follow-up question.
