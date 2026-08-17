# Minto

A skill that applies Barbara Minto's Pyramid Principle: structure the argument first, then render it in the format you asked for — mail, memo, report, blog post, deck, proposal, ad, landing page, PDP, or executive summary.

It is **not a formatter**. The work is the thinking: group the ideas, derive the higher-order statement, test the logic. The format comes last.

---

## What this is

A skill is a folder of instructions. When you invoke it, `SKILL.md` is loaded into Claude's context and changes how Claude approaches that one response — in this case, forcing it to build and validate an argument structure before writing anything. It is not code, it calls no tools, and it does nothing on its own. Once the response is done, its influence ends.

That means the whole skill is plain text you can read and edit. If you disagree with a rule, change the line.

## Where it runs

Anywhere Claude loads skills — Claude Code, Cowork, the Claude apps. There is no environment dependency: the frontmatter declares only `name` and `description` (no `allowed-tools`), and neither `SKILL.md` nor any of the four reference files calls a tool, an MCP server, or a platform API.

What *does* differ per environment is how you install it. That is the only surface-specific part, and it is covered below.

---

## What it gives you

Left alone, a language model writes in a predictable shape: it mirrors the order of the input, builds context before answering, and puts the recommendation at the end. Headings become topics instead of statements, and arguments come in threes even when only two of them carry weight. It reads smoothly and is still hard to check, because what the claim rests on stays unclear.

The same notes, without and with the skill:

> **Without:** "Thanks for the numbers. Traffic has developed nicely at +17%. On closer inspection, however, several factors warrant assessment. Conversion rate is 1.1% on mobile and 2.9% on desktop … Overall, optimisation should be considered before increasing budget."

> **With:** "I'd hold the 40k until the mobile PDP is fixed. Traffic isn't our constraint — we're up 17% year over year. The problem is conversion, and it's almost entirely mobile …"

Four things concretely:

**The answer comes first.** Recommendation, then reasoning, then evidence. Read only the opening paragraph and you have the decision; go deeper and you find each proof point sitting under the claim it actually supports.

**Finding, conclusion and recommendation stay separate.** "Mobile conversion fell 22%", "the decline is concentrated on mobile" and "we should fix the PDP first" are three different things. Blending them is the most common failure in internal writing, because it makes recommendations look like facts.

**Assumptions stay assumptions.** The skill distinguishes internally between fact, inference, assumption and hypothesis, and invents nothing to fill a structure — no figures, no testimonials, no proof points. Given thin material it names what's missing instead of producing a convincing-sounding gap. For proposals and landing pages this is the point that matters most.

**The standard is repeatable.** A mail, a proposal and a product page all pass the same checks, regardless of who asked and how well the prompt happened to be worded that day. Across a team it creates shared vocabulary: "what's the actual core message here?" becomes an answerable question.

### What it doesn't give you

It doesn't make the model smarter, and it doesn't rescue thin material — it only makes the gap visible. For a two-line answer it's overhead. And Claude can do much of this without the skill if you describe it well enough; the gain is not having to describe it every time.

---

## Installing

> Install the **whole `minto/` folder**, never `SKILL.md` on its own. Without `references/`, the skill fails silently rather than visibly: it instructs itself to read the renderer file for the chosen mode, doesn't find it, and produces generically structured output.

### Cowork and the Claude apps

Click the `minto.skill` file card and choose **Save skill**. The archive carries `SKILL.md` and the full `references/` folder, so everything installs together, and the skill is saved to your profile rather than to one surface.

Whether the button appears depends on your organisation's skill settings.

### Claude Code

Copy the folder:

```bash
# Personal — available in every project
cp -R minto ~/.claude/skills/

# Or per project, checked into the repo
cp -R minto .claude/skills/
```

### Verifying the install

Invoke an evidence-dependent mode with nothing to work from:

```
/minto report
```

Installed correctly, the skill asks for material or states plainly what it can and cannot conclude — its input triage refuses to manufacture a pyramid to fill the requested shape. A polished generic report instead means the skill didn't load. No effect at all usually means a wrong path, or folder structure lost while copying.

---

## Using it

### Invocation

The skill runs **only when explicitly invoked**. It will not fire on its own just because some text could use structuring — deliberately, so it doesn't turn every mail into a consulting deliverable.

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

Without a mode, the skill infers one from context. An explicit mode always wins — `/minto mail` on a report gives you a mail, not a shortened report.

### Modes

| Mode | For |
| --- | --- |
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

### Modifiers

Free-form, no fixed vocabulary: `short`, `deep`, `seo`, `board`, `meta`, `ecommerce`, `strict`. They change depth, channel, audience, tone or length — never the logic standard.

### What you get back

- **Default:** the artifact only, no framework commentary.
- **Mail, memo, report, proposal, executive at standard depth or deeper:** the artifact plus a compact structure note (core message and supporting arguments), so the reasoning is checkable without reading a second document.
- **`analysis` and `critique`:** the structure *is* the product and is written out.
- **On request:** the full pyramid including assumptions.

### Good inputs

The skill is only as good as its material. Raw notes, numbers, quotes, a thread — the more real substance, the more load-bearing the argument. Given thin material it marks the core message as provisional and names what's missing. It invents nothing: no figures, no testimonials, no proof points. An incomplete pyramid is acceptable; a fabricated one is not.

---

## How it's built

```
minto/
├── SKILL.md                    # thinking engine: logic rules, construction, validation, mode selection
└── references/
    ├── tier-a.md               # mail, memo, report, proposal, executive
    ├── tier-b.md               # blogpost, slides
    ├── tier-c.md               # ad, atf, landingpage, pdp
    └── meta-modes.md           # analysis, critique, rewrite
```

Each invocation loads `SKILL.md` plus **exactly one** reference file — the one matching the chosen mode. That keeps context cost at roughly half a single-file version without cutting any content. This README is never loaded by Claude; it is for people.

The three tiers differ in how much authority the pyramid has over the visible result. In **Tier A** it governs the visible structure too; in **Tier B** the information architecture; in **Tier C** only *what* has to be communicated and supported — sequence and tone there are decided by conversion logic. The evidence standard is identical in all three.

## Editing and repackaging

Renderer changes belong in the relevant file under `references/`; changes to the thinking standard belong in `SKILL.md`. A rule that applies to several modes belongs in `SKILL.md` exactly once — not repeated per mode.

After editing, repackage:

```bash
cd ~/.claude/skills/synced/skill-creator
python -m scripts.package_skill /path/to/minto
```

This validates the frontmatter and produces `minto.skill`. When updating, leave the name `minto` unchanged — otherwise you get a second skill instead of a new version.

## Open

There are no evals yet. Two or three realistic test prompts with a baseline comparison would be the sensible next step — particularly for mode inference when no mode is given, and for how much structure the skill exposes.
