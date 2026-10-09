# Tier C Renderers

**Modes:** `ad`, `atf`, `landingpage`, `pdp`, `flow`

The Tier C override is defined once in `SKILL.md` — read it there before using any mode in this file. In short: the pyramid decides **what must be communicated and supported**; conversion and creative principles decide **how it appears**. The evidence standard does not relax.

The no-fabrication rule matters most here. Do not invent proof, testimonials, reviews, ratings, star counts, customer numbers, results, or scarcity. If a proof element is not supplied, either leave it out or mark it as a placeholder the user must fill.

---

## `/minto ad`

Use for advertising copy. Minto must be heavily compressed — do not attempt to reproduce a full pyramid inside an ad.

**Internal logic:**

```text
What should the audience believe? → Why should they care?
→ Why should they believe it? → What should they do?
```

**Rendered as:** Proposition → Primary Benefit → Reason to Believe → CTA. Depending on the channel, some elements are legitimately implicit.

* Make the proposition clear quickly, even when the opening is a hook rather than a statement.
* Prioritize one central benefit. An ad carrying three benefits carries none.
* Use proof only where it strengthens the claim; a weak proof point dilutes a strong claim.
* Do not overload the ad with every supporting argument from the pyramid.
* Adapt length, structure, and convention to the requested channel.

---

## `/minto atf`

Use for the above-the-fold section of a website or landing page. This is the most compressed Minto renderer.

**Internal logic:**

```text
Governing Thought → Primary Benefit → Reason to Believe → Required Action
```

**Default render:** Headline · Subheadline · Proof / Trust / USP · Primary CTA. Add a secondary CTA only when a genuinely different visitor intent justifies it.

**Headline** — express the audience translation of the Governing Thought, not the analytical statement. Avoid empty category claims.

| | |
| --- | --- |
| Bad | Digital Excellence for Tomorrow |
| Weak (literal) | Automated invoicing, reminders and reconciliation reduce your administrative workload. |
| Strong (translated) | Get paid without chasing anyone. |

**Subheadline** — clarify how, for whom, through what mechanism, or with what primary benefit. Do not restate the headline in different words.

**Proof** — answer *why should the visitor believe this?* Candidates: measurable results, customer logos, ratings, customer numbers, expertise, certifications, guarantees, differentiated capabilities.

**CTA** — represent the logical next action. Prefer a specific action over a vague label such as "Learn More" when a clearer next step exists.

**Scope** — do not force the entire pyramid above the fold. The ATF is a compressed expression of the pyramid, not a miniature report.

---

## `/minto landingpage`

Use for a complete landing page — the full page argument, not just the hero. `atf` covers only the compressed hero.

A landing page carries **one proposition and one conversion goal** across multiple sections. If a second, unrelated goal appears, it is a different page.

**Section sequence.** The list below is an ordered sequence of page sections, not a Key Line group — do not apply the "2–4 siblings" rule or a MECE test to it. Every section must still earn its place beneath the Core Proposition.

```text
Core Proposition
↓
Why this matters (problem / need)
↓
Primary Benefits
↓
How it works / mechanism
↓
Proof
↓
Objection handling
↓
Offer
↓
Risk reduction
↓
CTA
```

* One dominant proposition; do not dilute it with a second pitch.
* Order sections by the visitor's decision sequence, not by what you most want to say.
* Keep evidence beneath the specific claim it supports.
* Objection handling must address the strongest real objection, not a strawman.
* Repeat the CTA at logical decision points, not mechanically.
* A shorter page that converts beats a complete-looking one. Do not pad with sections that add no decision value.

---

## `/minto pdp`

Use for a Shopify or e-commerce product detail page. A PDP is neither an `atf` nor a `landingpage`: it must answer one central question —

> Why should I buy **this** product, **now**?

**Internal purchase logic.** Four supports, ordered from claim to risk:

```text
Purchase Proposition
├── Primary Benefit          — what it does for me
├── Reasons to Believe       — why the claim holds (proof, media, results)
├── Objection Resolution     — everything blocking the click, including fit,
│                              sizing, compatibility, delivery and returns
└── Risk Reduction           — what happens if I am wrong
```

Fit questions are objections, so keep them inside Objection Resolution rather than as a separate sibling — splitting them produces overlapping categories and duplicated copy.

**Typical visible order:**

```text
Product title / proposition → Primary purchase benefit → Price / variant / CTA (buy box)
→ Key benefits → Product proof (reviews, results, media) → Use cases / fit
→ Details / specs → Objection handling → Trust / shipping / returns → Supporting CTA
```

* Lead the visible page with the proposition and primary benefit, and keep the buy box high.
* Specs are support, not the argument. Never let the spec table become the pitch.
* Risk reduction (returns, guarantee) belongs near the decision, not buried at the bottom.
* Match the customer's language, not internal product jargon.

---

## `/minto flow`

Use for a sequence of automated lifecycle messages — welcome, abandoned cart, post-purchase, winback, replenishment, onboarding. Also use it to evaluate an existing sequence.

Every other mode in this skill renders **one** artifact. This one renders an argument that unfolds across several, so the pyramid spans the sequence rather than sitting inside each message.

> A flow is not a set of emails that share a trigger. It is one argument delivered in instalments.

**Establish before writing anything:**

* the trigger, and what it tells you the recipient just did
* what the recipient knows and believes at entry
* the single behaviour the flow exists to produce
* what currently stops them from doing it

That last one sets the length. Message count follows the objections that must be cleared, not a template — a flow with nothing left to resolve should end.

**Build the sequence as the pyramid:**

```text
Flow Governing Thought  →  the belief or action the whole sequence must produce
  Message 1 → Key Line 1
  Message 2 → Key Line 2
  Message 3 → Key Line 3
```

Each message carries one Key Line's worth of work: one purpose, one dominant message, and a stated relationship to the one before it.

**Apply the Why test to every message:**

```text
Why does this message exist?
Why at this position rather than earlier or later?
What does the recipient know or believe afterwards that they did not before?
Which uncertainty or objection does it remove?
```

If a message has no distinct answer, merge it, move it, or drop it.

* Do not repeat the same argument in successive messages. A sequence that restates its case is one message long and four messages annoying.
* Do not let every message carry its own full pitch. Progression is the point: relevance, then understanding, then credibility, then objection, then the reason to act now.
* Where the flow branches on behaviour or customer state, say what the branch assumes about the recipient.
* Timing is part of the argument. State the interval and why the recipient is ready for the next message by then.

Evaluating an existing flow is the same test run backwards: name each message's intended Key Line, then find the ones that duplicate, the objection nobody answers, and the position no message justifies.
