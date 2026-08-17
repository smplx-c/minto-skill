# Minto

**Minto makes Claude work out the argument before it writes a word — and then renders that argument in the format you actually need.**

A Claude skill: one thinking engine, fourteen format renderers, and a validation pass that refuses to fill a structure with material it doesn't have.

→ [**Download `minto.skill`**](https://github.com/smplx-c/minto-skill/releases/latest/download/minto.skill) for Cowork and the Claude app, or clone the folder for Claude Code — see [Installation](#installation).

---

## The problem it solves

Left alone, a language model writes in a predictable shape. It mirrors the order of your input, builds context before answering, and puts the recommendation at the end. Headings become topics instead of statements, and arguments come in threes even when only two of them carry weight.

It reads smoothly and is still hard to check, because what the claim rests on stays unclear.

The same notes, without and with the skill:

> **Without:** "Thanks for the numbers. Traffic has developed nicely at +17%. On closer inspection, however, several factors warrant assessment. Conversion rate is 1.1% on mobile and 2.9% on desktop … Overall, optimisation should be considered before increasing budget."

> **With:** "I'd hold the 40k until the mobile PDP is fixed. Traffic isn't our constraint — we're up 17% year over year. The problem is conversion, and it's almost entirely mobile …"

Same facts. Only the second one can be acted on, or argued with.

---

## How Minto intervenes

**The answer moves to the front.** Recommendation first, then reasoning, then evidence. Read only the opening paragraph and you have the decision; go deeper and each proof point sits under the claim it actually supports — not beside it.

**Finding, conclusion and recommendation stay separate.** "Mobile conversion fell 22%", "the decline is concentrated on mobile" and "we should fix the PDP first" are three different logical types. Blending them is the most common failure in internal writing, because it makes recommendations look like facts.

**Assumptions stay assumptions.** The skill sorts its own material into fact, inference, assumption and hypothesis, and invents nothing to complete a structure — no figures, no testimonials, no proof points. Given thin material it names what's missing instead of producing a convincing-sounding gap. For proposals and landing pages this is the point that matters most.

**Nothing renders until the structure holds.** Before drafting, four checks run every time: does the top statement answer the actual question, can every parent claim be derived from what sits beneath it, are sibling points the same kind of thing, and does each observation lead somewhere. Four more run at greater depth.

---

## What you get back

**The artifact, not a framework lecture.** By default you get the mail, the memo, the page — no pyramid diagrams, no commentary.

**A structure note where it earns its place.** For mail, memo, report, proposal and executive at standard depth or deeper, the artifact is followed by a few lines naming the core message and its supporting arguments, so the reasoning is checkable without reading a second document.

**The structure itself, when that's the job.** In `analysis` and `critique` the structure *is* the product and is written out in full. The complete pyramid including assumptions is available on request in any mode.

---

## What it costs and what it can't do

It doesn't make the model smarter, and it doesn't rescue thin material — it only makes the gap visible. For a two-line answer it's overhead; skip it. And Claude can do much of this without the skill if you describe what you want well enough. The gain is not having to describe it every time, and getting the same standard on a bad prompting day.

The skill is only as good as its material. Raw notes, numbers, quotes, a thread — the more real substance, the more load-bearing the argument.

---

## Installation

A skill is a folder of instructions, not code. On invocation, `SKILL.md` is loaded into Claude's context and changes how it approaches that one response; when the response ends, so does its influence. It calls no tools and has no environment dependency — the frontmatter declares only `name` and `description`, and nothing in the skill touches a tool, an MCP server, or a platform API. It therefore runs anywhere Claude loads skills. Only the install route differs.

**Claude Code** — clone into your skills directory:

```bash
git clone https://github.com/smplx-c/minto-skill.git ~/.claude/skills/minto
```

The target directory must be `minto`, matching the skill name — the repository is called `minto-skill` to keep it legible on GitHub, but the folder Claude loads should not be.

**Cowork / Claude Desktop** — download `minto.skill` from the [latest release](https://github.com/smplx-c/minto-skill/releases/latest) and drop it into a chat. The file card shows **Save skill**, provided your organization permits skill creation.

Install the whole folder either way, never `SKILL.md` on its own. Without `references/` the skill fails silently rather than visibly: it instructs itself to read the renderer for the chosen mode, doesn't find it, and produces generically structured output.

**Verifying** — invoke an evidence-dependent mode with nothing to work from:

```
/minto report
```

Installed correctly, the skill asks for material or states plainly what it can and cannot conclude. A polished generic report instead means it didn't load.

---

## Invoking it

The skill runs **only when explicitly invoked** — deliberately, so it doesn't turn every mail into a consulting deliverable.

```
/minto [mode] [modifier]
```

All of these work:

```
/minto mail
/minto report deep
/minto critique strict
minto, rebuild this as a proposal
please apply the pyramid principle
```

Without a mode, the skill infers one from the task and the material in front of it. An explicit mode always wins — `/minto mail` on a report gives you a mail, not a shortened report. Treat the slash syntax as an API.

It works best with substance rather than a bare instruction. Instead of "write a mail about the numbers", paste the numbers, say who reads it, and say what you want them to do.

---

## Fourteen modes — by the shape of the output

| Mode | For |
|---|---|
| `mail` | emails and replies |
| `memo` | internal decision memos, recommendations |
| `report` | evidence-backed analysis, documented |
| `proposal` | offers, scopes, commercial recommendations |
| `executive` | board and leadership formats, heavily compressed |
| `blogpost` | articles, thought leadership, SEO content |
| `slides` | decks and presentation storylines |
| `ad` | advertising copy, channel-specific |
| `atf` | above the fold, hero section |
| `landingpage` | full page with one conversion goal |
| `pdp` | product detail page (Shopify, e-commerce) |
| `analysis` | thinking tool: what does the data actually say? |
| `critique` | evaluate existing text, **not** rewrite it |
| `rewrite` | restructure existing text |

`critique` and `rewrite` are deliberately separate. Paste text without a clear instruction and `critique` wins — a critique is reversible, an unrequested rewrite discards your version.

### Three tiers — by how much authority the pyramid has

The renderers do not all give the argument the same control over the visible result, and knowing which tier you're in explains why the same input can look so different.

| Tier | Modes | The pyramid governs |
|---|---|---|
| **A** | `mail`, `memo`, `report`, `proposal`, `executive` | reasoning *and* visible structure |
| **B** | `blogpost`, `slides` | information architecture |
| **C** | `ad`, `atf`, `landingpage`, `pdp` | only *what* must be communicated and supported |

In Tier C, sequence and tone are decided by conversion logic, so the copy may open with a hook, a problem, or tension rather than the answer. The evidence standard is identical in all three — the creative freedom is about expression, never about proof.

### Modifiers — by effort

Free-form, no fixed vocabulary: `short`, `deep`, `seo`, `board`, `meta`, `ecommerce`, `strict`. They change depth, channel, audience, tone or length — never the logic standard. Depth runs Compact (core message and key arguments) through Standard to Deep (framing, evidence, assumptions, implications).

---

## Repository layout

```
minto/
├── SKILL.md                      the thinking engine — applies to every run
├── README.md                     this document
└── references/
    ├── tier-a.md                 mail, memo, report, proposal, executive
    ├── tier-b.md                 blogpost, slides
    ├── tier-c.md                 ad, atf, landingpage, pdp
    └── meta-modes.md             analysis, critique, rewrite
```

`SKILL.md` holds only what applies to every run: the logic rules, pyramid construction, validation, epistemic discipline, and mode selection. Each invocation loads it plus **exactly one** reference file — the renderer for the chosen mode. That keeps context cost at roughly half a single-file version without cutting content. This README is never loaded by Claude; it is for people.

---

## Editing and repackaging

Renderer changes belong in the relevant file under `references/`; changes to the thinking standard belong in `SKILL.md`. A rule that applies to several modes belongs in `SKILL.md` exactly once — not repeated per mode.

After editing, repackage and publish:

```bash
python -m scripts.package_skill /path/to/minto     # from the skill-creator directory
gh release create v1.1.0 minto.skill --title "v1.1.0" --notes "…"
```

Packaging validates the frontmatter. Keep the skill name `minto` unchanged across versions — a new name produces a second skill rather than an update. The built `.skill` is a release asset only and is gitignored, so the download link always points at a tagged, deliberate build rather than whatever last landed on `main`.

## Open

There are no evals yet. Two or three realistic test prompts with a baseline comparison would be the sensible next step — particularly for mode inference when no mode is given, and for how much structure the skill exposes.
