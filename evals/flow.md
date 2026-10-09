# Evals — `flow`

Two prompts for checking that `flow` does the thing it was added for: treat a sequence as one argument, not a batch of emails. Run each, then score against the criteria. No framework — read the output and judge it.

Baseline for comparison: run the same prompt with the skill disabled.

---

## 1. Build — welcome sequence

```
/minto flow

Welcome flow for a Shopify shop selling refillable cleaning products.
Trigger: newsletter signup via a 10% popup.
Most signups take the discount on a first order and never come back.
Average order 32 EUR, refill packs 9 EUR.
Goal: first purchase, and ideally the first refill.
```

**Should:**

- State a Flow Governing Thought covering the whole sequence before listing any message.
- Derive the message count from the objections it names, and say what those are.
- Give each message a distinct job, with its relationship to the previous one stated.
- Treat "most signups take the discount and never come back" as the central problem to solve, not as background.
- Name the timing between messages and why.

**Should not:**

- Produce five interchangeable promotional emails each pitching the full offer.
- Default to a fixed template length without justifying it.
- Invent open rates, benchmarks, or revenue figures. Nothing in the prompt supports any.
- Treat the refill as a separate campaign — it is in the stated goal.

**Failure that matters most:** a sequence where messages 2–5 could be reordered without loss. That means no argument was built.

---

## 2. Evaluate — existing sequence

```
/minto flow

Review this abandoned-cart flow.

1h: "You left something behind" — product image, Complete checkout.
24h: "Still thinking?" — same product, same button, 10% code.
72h: "Last chance" — same product, same code, expires tonight.
```

**Should:**

- Name each message's intended Key Line, then find that all three carry the same one.
- Identify the unanswered objection: nothing addresses *why* the cart was abandoned — price, shipping cost, trust, or a stalled decision.
- Flag the discount at 24h as uncovered by evidence: nothing here shows price was the blocker.
- Recommend a change in the argument, not just the copy.

**Should not:**

- Rewrite the three emails. `/minto flow` on existing material evaluates; rewriting needs to be asked for.
- Judge the flow by message count or send timing alone.
- Claim a performance problem without data. The sequence has a structural defect; that is a separate claim from "it converts badly."

**Failure that matters most:** feedback on subject lines and CTA wording while leaving "all three messages make the same argument" unsaid.

---

## Open

No eval for mode inference yet — specifically whether `flow` is picked over `mail` when the material is an email sequence without an explicit mode. That is the likeliest inference collision.
