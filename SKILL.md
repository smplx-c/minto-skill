---
name: minto
description: Apply Barbara Minto's Pyramid Principle to structure thinking and render it as mails, memos, reports, blog posts, slides, proposals, ads, landing pages, PDPs or executive summaries. Use only when the user explicitly invokes minto or /minto (optionally with a mode such as mail, memo, report, blogpost, slides, proposal, ad, atf, landingpage, pdp, executive, analysis, critique, rewrite), or explicitly asks to apply the Minto or Pyramid Principle, or explicitly asks for a governing thought, key line, or SCQA structure. Never trigger implicitly.
---

# Minto

Use this skill to **discover, structure, validate, and communicate thinking** using the Minto Pyramid Principle.

Minto is not primarily a writing style. It is a structured-thinking method. The purpose of the pyramid is to work out the thinking **before** drafting the communication.

> Think first. Structure second. Write third.

Do not begin drafting the requested artifact until the argument structure is sufficiently clear.

## How this skill is organised

This file contains everything needed to **think**: the logic rules, the construction process, the validation, and the mode-selection logic.

The **renderers** — the format-specific instructions for turning a validated pyramid into an artifact — live in separate reference files. Read the one file matching the selected mode before you begin drafting, and only that one:

| Reference file | Modes |
| --- | --- |
| `references/tier-a.md` | `mail`, `memo`, `report`, `proposal`, `executive` |
| `references/tier-b.md` | `blogpost`, `slides` |
| `references/tier-c.md` | `ad`, `atf`, `landingpage`, `pdp` |
| `references/meta-modes.md` | `analysis`, `critique`, `rewrite` |

Reading the renderer is not optional. The thinking standard in this file is constant; the renderer decides what the output actually looks like, and skipping it produces generically-structured output that ignores the format's real constraints.

## Language

Match the user's language unless the user explicitly requests another language.

When the artifact's audience differs from the conversation language — for example a German-speaking user drafting an English landing page — write the artifact in the **audience's** language and state that choice in one short line. Do not guess silently.

Internal framework terms such as "Governing Thought" or "Key Line" may remain in English when useful, but user-facing output must follow the language rule above. The framework terminology and examples in this skill must never cause the final artifact to switch languages.

---

## Core Philosophy

The Minto process has two engines.

**Thinking Engine** — discover what the material actually says, group related ideas, derive higher-order insights, build the argument pyramid, test the logic.

**Communication Engine** — render the validated pyramid into the requested format.

The communication format must never weaken the underlying reasoning standard. `/minto` is therefore not a formatting command. It is a structured-thinking command with format-specific renderers.

---

## Invocation and Mode Selection

Preferred syntax: `/minto [mode] [optional modifier]` or `minto [mode]`.

Explicit mode selection always overrides inferred context — treat the slash syntax as an API.

* `/minto mail` → produce a mail even if the source material is a report.
* `/minto atf` → produce an above-the-fold structure even if the source is a strategy memo.
* `/minto critique` → critique only; do not rewrite unless explicitly requested.

### Inferring the mode

If `/minto` is invoked without a mode, infer it from the task and active material. Do not ask the user to choose when the signal is clear.

| Signal in the task or material | Mode |
| --- | --- |
| An email or thread, a reply is wanted | `mail` |
| Internal decision, recommendation to a colleague or lead | `memo` |
| Substantial analysis with evidence to be documented | `report` |
| Client-facing offer, scope, or commercial recommendation | `proposal` |
| Board, leadership, or an explicit request for brevity | `executive` |
| Article, editorial, SEO or thought-leadership piece | `blogpost` |
| Deck, presentation, slide storyline | `slides` |
| Hero section, above-the-fold copy | `atf` |
| A full page with one conversion goal | `landingpage` |
| Shopify or e-commerce product detail page | `pdp` |
| Advertising copy for a specific channel | `ad` |
| Raw data, notes, or research with no settled answer | `analysis` |
| Existing text, evaluation wanted | `critique` |
| Existing text, restructuring wanted | `rewrite` |

**Tiebreakers.** Pasted text with an ambiguous request defaults to `critique`, not `rewrite` — critique is reversible and rewriting unasked destroys the user's version. If no signal dominates and the context is internal, default to `memo`. Otherwise ask one short question rather than guessing across tiers, because a Tier A and a Tier C artifact are not recoverable from one another.

### Optional modifiers

The user may add a modifier: `/minto mail short`, `/minto report deep`, `/minto blogpost seo`, `/minto slides board`, `/minto atf ecommerce`, `/minto ad meta`, `/minto critique strict`.

Interpret modifiers naturally; do not require a fixed vocabulary when intent is clear. Modifiers may alter depth, audience, channel, tone, length, level of evidence, or number of sections or slides. They must not alter the underlying logic standard.

### Triaging the input before you start

Check what you actually have before building anything:

* **Sufficient material** → proceed.
* **Thin or one-sided material** → proceed, but mark the resulting Governing Thought as provisional and name the missing evidence.
* **Essentially no material for an evidence-dependent mode** (`report`, `analysis`, `proposal`) → ask for the material or state plainly what you can and cannot conclude. Do not manufacture a pyramid to fill the requested shape.
* **Far more material than the artifact needs** → compress first (see Compression below), then render. Do not let the volume of input set the length of the output.

---

## The Three Fundamental Logic Rules

Every pyramid must obey these three rules.

### Rule 1 — The parent must summarize the children

Every statement above a group must be a genuine summary, synthesis, implication, or logical conclusion derived from the statements immediately below it.

Ask: *Can this parent statement genuinely be derived from all of its children?* If not, regroup or rewrite.

**Good:**

```text
Mobile UX is the primary conversion problem
├── Mobile conversion declined
├── Mobile bounce rate increased
└── Mobile PDP exits increased
```

**Bad:**

```text
Mobile UX is the primary conversion problem
├── Mobile conversion declined
├── Google Ads
└── New checkout
```

Do not create a parent merely because the child ideas are vaguely related.

### Rule 2 — Ideas in a group must be logically the same kind

Sibling statements must answer the same question, serve the same logical function, and sit at approximately the same level of abstraction.

Valid sibling groups are things of one kind: reasons, causes, effects, actions, options, steps, findings, risks, components, or criteria. Do not mix logical types within one group.

**Bad** — this mixes an effect, a technology, a date, and an observation:

```text
Why should we launch?
1. Revenue could increase.
2. Shopify.
3. September.
4. The current checkout is weak.
```

**Better:**

```text
Why should we launch?
1. It should increase revenue.
2. It should reduce operating complexity.
3. It should reduce technical risk.
```

### Rule 3 — Ideas in a group must follow a logical order

Every sibling group must have an identifiable ordering principle:

* **Chronological** — Research → Build → Launch → Optimize
* **Structural** — Acquisition → Conversion → Retention
* **Cause and effect** — Cause → Mechanism → Consequence
* **Priority** — Critical → Important → Secondary
* **Process** — Input → Transformation → Output
* **Deductive** — Premise → Application → Conclusion

Ask: *Why does B come after A?* If no meaningful answer exists, the ordering is arbitrary and the group is probably not yet properly understood.

### MECE

Aim for groups that are as Mutually Exclusive and Collectively Exhaustive as practical. Sibling categories should not materially overlap, and together they should cover the relevant whole sufficiently for the decision or argument.

```text
Revenue
├── Traffic
├── Conversion Rate
└── Average Order Value
```

Do not force artificial completeness. A useful, decision-relevant structure beats invented categories created only to make a framework look MECE.

---

## Building the Pyramid

Do not discover the argument while writing paragraphs. Identify the relevant ideas, determine their relationships, group them logically, derive summaries, establish the pyramid, test the logic — and only then render.

### Top-down mode

Use when the central answer is already reasonably known.

```text
Question → Provisional Answer → Key Lines → Supporting Arguments → Evidence
```

Treat the initial answer as a hypothesis until the support has been tested. Do not preserve a preferred conclusion the evidence does not support.

### Bottom-up mode

Use when the answer must be discovered from notes, research, data, documents, or unstructured thinking.

```text
Raw Ideas → Logical Groups → Group Summaries → Higher-Order Groups → Governing Thought
```

At every level ask: *What single statement accurately summarizes these points without losing their decision-relevant meaning?* Repeat until one central conclusion remains.

### Step 1 — Identify the core question

Determine what question the communication must resolve. Typical forms: Should we do X? Why is X happening? Which option should we choose? What is the main finding? What should happen next? What should the audience believe? What is preventing the desired outcome?

If the user gives no explicit question, infer the most relevant one. Do not invent a strategic question when the user only needs a narrow factual communication.

### Step 2 — Establish the Governing Thought

The Governing Thought is the highest-level message. It answers the Core Question and expresses the most important conclusion, recommendation, insight, decision, or implication.

| | |
| --- | --- |
| Bad | Mobile performance analysis |
| Bad | There are several opportunities for improvement. |
| Better | Mobile conversion is currently the primary growth constraint. |
| Better | Fix the mobile PDP before increasing paid-media spend. |

A topic is not a conclusion. Where appropriate, include the decision, the qualification, the key implication, and the next action — but never make the Governing Thought more certain than the evidence allows.

### Step 3 — Build the Key Line

Identify the smallest useful set of major statements supporting the Governing Thought. Usually 2–4. Do not force exactly three.

For every proposed Key Line ask: *If these statements are true, does the Governing Thought reasonably follow?* If not, the Key Line is incomplete, irrelevant, or incorrectly grouped.

```text
Governing Thought: Do not increase paid-media spend yet.
Why?
1. Traffic is already growing.
2. Conversion is declining.
3. The decline is concentrated in addressable mobile friction.
```

### Step 4 — Support each Key Line

Under every Key Line place the reasoning and evidence that specifically supports it: findings, facts, calculations, observations, mechanisms, comparisons, assumptions, external evidence.

Keep evidence beneath the claim it supports. Do not place evidence beside recommendations as if they were the same logical type.

### Step 5 — Separate findings, conclusions, and recommendations

These are three different logical types and must not sit at the same level.

* **Finding** — what the evidence shows: *Mobile conversion declined 22%.*
* **Conclusion** — what the finding means: *The conversion decline is concentrated on mobile.*
* **Recommendation** — what should be done: *Prioritize mobile PDP optimization before additional media scaling.*

```text
Recommendation → Conclusion → Findings → Evidence
```

Do not write a "Key Findings" list that contains a recommendation.

### Step 6 — Apply the So-What test

For observations and facts, repeatedly ask *So what?*

```text
Mobile conversion is 1.1%.
↓ So what?  It is materially below desktop.
↓ So what?  Mobile users generate disproportionately less revenue.
↓ So what?  Most traffic is mobile, so this is the largest conversion opportunity.
↓ So what?  Mobile conversion should be the first optimization priority.
```

Do not stop at a data point when a decision-relevant implication can reasonably be derived — and do not force an implication the evidence does not support.

### Step 7 — Apply the Why test

For every higher-level claim ask *Why is this true?* The statements beneath it should answer that question.

```text
Fix the mobile PDP first.
↓ Why?  It is the largest addressable conversion constraint.
↓ Why?  Most deterioration occurs between mobile PDP view and cart.
↓ Evidence: analytics data, funnel data, UX findings.
```

---

## Validating the Pyramid

Run these checks silently before rendering. The first four catch most real failures and are mandatory at every depth; the remainder apply at Standard and Deep.

**Mandatory**

1. **Governing Thought** — does the top statement directly answer the Core Question, and is it a conclusion rather than a topic?
2. **Parent / Why** — can every parent genuinely be derived from its children, and do the children answer *why* the parent is true?
3. **Sibling / Abstraction** — do siblings answer the same question, perform the same logical function, and sit at the same conceptual level?
4. **So-What** — do lower-level observations lead to meaningful higher-level implications?

**At Standard and Deep**

5. **Order** — does each group follow a clear ordering principle?
6. **MECE** — are there material overlaps or important gaps?
7. **Evidence and necessity** — are material claims supported by actual evidence rather than plausible-sounding assertions, and would removing any point materially weaken the argument? If not, remove, combine, or demote it.
8. **Contradiction** — does any supporting point materially undermine another part of the pyramid? Resolve it rather than hiding it.

### Epistemic discipline

Never make the pyramid appear stronger than its evidence. Distinguish internally between:

* **Fact** — directly supported by supplied or verified evidence.
* **Inference** — reasonably derived from evidence.
* **Assumption** — required for the argument but not yet established.
* **Recommendation** — a judgment about what should be done.
* **Hypothesis** — a provisional explanation that still requires testing.

Do not convert assumptions or hypotheses into facts for the sake of a cleaner structure. If pivotal evidence is missing, say so when it is material to the user's decision.

**Never fabricate to fill a structure.** No invented facts, categories, evidence, proof points, quotes, testimonials, reviews, ratings, figures, or scarcity. If something is not supported, label it as an assumption or leave it out. An incomplete pyramid is acceptable; a fabricated one is not. This rule governs every renderer, and the conversion modes in `references/tier-c.md` are where it is most often at risk.

### When no strong answer exists

If the evidence does not support a clear Governing Thought: do not manufacture certainty. State the strongest conclusion currently supported, identify the unresolved question and the critical missing evidence, structure competing hypotheses if useful, and recommend the highest-information next step. A qualified answer is better than false clarity.

---

## Framing and Reasoning Patterns

### SCQA

Use when context is needed to establish why the issue matters.

* **Situation** — the accepted starting context.
* **Complication** — what changed, failed, conflicts, or creates urgency.
* **Question** — the issue that logically follows.
* **Answer** — the Governing Thought.

Do not print the labels unless the user asks for the structure or the artifact clearly benefits from visible SCQA. SCQA is primarily a framing and reasoning mechanism.

### Inductive and deductive support

**Inductive** — comparable observations support a broader conclusion:

```text
Mobile conversion declined. Mobile bounce increased. Mobile PDP exits increased.
↓
Mobile UX is the primary conversion problem.
```

**Deductive** — a rule combines with a statement to produce a necessary conclusion: *A; A implies B; therefore B.*

Keep deductive chains complete. Do not mix an unfinished deductive argument with an unrelated list of inductive observations.

---

## Renderer Control Tiers

The renderers do not all give Minto the same authority over the final artifact. Know which tier you are in before rendering.

* **Tier A** — Minto controls reasoning *and* visible communication structure: `mail`, `memo`, `report`, `proposal`, `executive`.
* **Tier B** — Minto controls information architecture and structure: `blogpost`, `slides`.
* **Tier C** — Minto controls message architecture only; persuasion and conversion control the visible expression: `ad`, `atf`, `landingpage`, `pdp`.

### The Tier C override

This applies to every Tier C mode; the reference file states only each mode's specific deltas.

In Tier C the pyramid decides **what must be communicated and supported** — it does not dictate the visible sequence of the copy. The artifact may open with curiosity, tension, a problem, a narrative hook, or a channel-native convention when that is more effective than answer-first communication.

```text
Governing Thought → Audience translation → Visible headline or hook
```

Translate the Governing Thought into the strongest customer-facing value proposition rather than stating it analytically. Prioritize, in order: immediate relevance, comprehension, differentiation, credibility, motivation to act.

The same substructure that yields *"Your mobile product page is suppressing conversion"* in Tier A may correctly surface as *"Why do 72% of your visitors cost you money?"* in Tier C. Do not sacrifice persuasive performance to make the visible copy look like a pyramid — and do not let the creative freedom weaken the evidence standard behind it.

---

## What the User Actually Sees

Deciding how much structure to expose is the single most consequential rendering choice. Apply this contract unless the user asks for something else:

* **Default** — deliver the artifact only. No pyramid, no framework commentary.
* **Tier A at Standard or Deep depth** — deliver the artifact, then a compact structure note of at most a few lines: the Governing Thought and the Key Lines. This lets the user check the reasoning without reading a second document.
* **`analysis` and `critique`** — the structure *is* the product; render it explicitly.
* **On request** — show the full pyramid, the assumptions, and the validation reasoning.
* **Never** — expose private chain-of-thought or narrate the steps of this skill while working.

### Depth

Use the minimum depth necessary to solve the user's task. Do not turn every simple task into a consulting report.

| Depth | Contains | The reader can stop at |
| --- | --- | --- |
| Compact | Governing Thought + Key Lines | the main message and its reasons |
| Standard | + supporting reasoning | the argument in full |
| Deep | + framing, evidence, assumptions, implications, recommendations | any level of detail |

A strong Minto output lets readers stop at different levels and still receive a coherent argument: an executive reads the Governing Thought and Key Lines; a specialist inspects the evidence. The structure must remain coherent if only the top two levels are read.

### Compression

At every level ask: *What single statement summarizes the points below without losing their decision-relevant meaning?*

```text
Analysis:      12 facts → 5 observations → 3 insights → 1 Governing Thought
Communication: Governing Thought → Insights → Observations → Evidence
```

The order in which you analysed and the order in which you communicate do not need to match — and usually should not.

---

## Worked Example

**Input (raw notes from the user):**

> Mobile conversion June 1.1%, desktop 2.9%. Traffic +17% YoY. Mobile is 72% of sessions. Mobile PDP bounce 61%, was 48% in May. New ads budget planned for Q4, +40k. Checkout relaunch went live last month. Desktop unremarkable.

**Bottom-up grouping (internal):**

```text
Group A — traffic is not the problem:  +17% YoY; desktop unremarkable
Group B — the loss is on mobile:       1.1% vs 2.9%; 72% of sessions
Group C — it is located and recent:    PDP bounce 48% → 61% since May; checkout relaunch timing
```

**Governing Thought:** Delay the Q4 media increase until the mobile PDP is fixed.

**Key Lines:** 1. Traffic is already growing, so more of it is not the constraint. 2. The conversion loss is concentrated on mobile, which carries most of the traffic. 3. The loss is recent and located at the mobile PDP, which makes it addressable.

**Assumption flagged, not asserted:** the checkout relaunch is temporally correlated with the bounce increase; causation is not established.

**Rendered as `/minto mail`:**

> Subject: Q4 media budget — recommend we wait
>
> I'd hold the +40k until we've fixed the mobile PDP.
>
> Traffic isn't our constraint — we're up 17% year over year. The problem is conversion, and it's almost entirely mobile: 1.1% against 2.9% on desktop, on 72% of our sessions. It's also recent and specific — mobile PDP bounce went from 48% to 61% in May, which is roughly when the checkout relaunch shipped. I haven't confirmed that link yet.
>
> Spending more on traffic now sends it into the leak. Can we get a fix scoped this week, and revisit the budget once bounce is back near 48%?

Note what happened: the analysis order (data → groups → conclusion) was inverted for communication, the assumption stayed an assumption, the evidence stayed beneath its claim, and no pyramid was exposed.

---

## Anti-Patterns

Beyond the rules already stated, avoid these specifically:

* Mistaking a topic for a conclusion, or beginning to write before the thinking is structured.
* Burying the answer at the end without a reason to.
* Reproducing research chronology, source order, or the sender's chronology as the communication structure.
* Defaulting to exactly three arguments, or creating categories only for symmetry.
* Printing SCQA labels mechanically, or treating evidence as if it were an argument.
* Oversimplifying uncertainty to produce a stronger-sounding Governing Thought, or hiding contradictory evidence.
* Confusing concise writing with structured thinking — and turning Minto into a superficial template.

## Final Quality Standard

A successful Minto output lets the reader understand the central conclusion quickly, grasp the main reasons without reading every detail, inspect supporting evidence only where necessary, see how each detail connects to the central argument, and distinguish facts from conclusions and recommendations.

Prioritize argument quality over visual symmetry, logical clarity over artificial completeness, evidence over rhetoric, and thinking before writing.
