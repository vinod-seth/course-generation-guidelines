# Course Generation Guideline: Technical Term Glossary & Hover Definitions

This guideline governs how technical terms are surfaced to learners. Its purpose is retention support: a learner meeting a term they half-remember must be able to recover the meaning **without leaving the lesson**, because a trip to Google is where a study session dies.

---

## 1. The Core Rule

Every technical term that carries meaning the learner may not hold in working memory must be wrapped in an inline definition. The term renders **highlighted**, and its definition appears **on hover** (and on tap, and on keyboard focus).

### Required Syntax

```markdown
<abbr title="Definition text goes here.">term</abbr>
```

Chosen because it is semantic HTML that degrades well everywhere:

| Surface | Behavior |
|---|---|
| Course portal | Highlighted term (amber tint, dotted underline) + styled tooltip on hover/tap/focus |
| GitHub web view | Native browser tooltip, dotted underline |
| Plain text / grep | The term still reads normally; nothing is lost |

> [!IMPORTANT]
> Do not invent custom syntaxes such as `[[term|definition]]` or `{term}(definition)`. They render as literal noise on GitHub and in any renderer that has not been taught the convention. `<abbr>` is the only approved form.

---

## 2. What Gets a Definition

Annotate a term when a learner could plausibly be unable to define it cold:

- **Domain jargon**: `<abbr title="...">quantile quantization</abbr>`, `<abbr title="...">exchangeability</abbr>`
- **Acronyms on first use per lesson**: ECE, NF4, PEFT, MHA, NLL
- **Overloaded words with a precise local meaning**: "temperature", "support", "coverage", "signal"
- **Metrics and their units**: what it measures, and which direction is good
- **Named techniques**: one clause on what it does, not its history

### What Does NOT Get a Definition

Over-annotation is its own failure: if every third word is highlighted, the page becomes unreadable and the highlight stops meaning anything.

- Terms the course's stated prerequisites already assume (do not define "gradient" in an advanced ML course)
- Terms defined in the surrounding prose in the same breath
- The same term repeatedly — **annotate first use per lesson only**
- Words inside code blocks or headings (the syntax does not render there)

**Density ceiling — measure it against prose length, not per lesson.** The failure mode is *visual*: a page where every third word glows stops being readable and the highlight stops signalling anything. That risk scales with how close the highlights sit, so the rule is a spacing rule:

> **No denser than ~1 annotated term per 150 words of prose, and never more than 20 in one lesson.**

A 600-word primer therefore gets ~4; a 3,500-word deep-dive can carry ~15–20 without ever looking crowded. A flat per-lesson cap is the wrong instrument — it would either strangle a long lesson or wave through a dense short one.

If a lesson breaches the spacing rule, the cause is usually one of: prerequisites set too low (you are defining things the audience already knows), jargon padding, or a lesson that should be split.

---

## 3. Writing the Definition

The definition is read in a small tooltip by someone mid-sentence. It is not a paragraph.

### Rules

- **Length**: 1 sentence, ≤ 25 words. Two only if the second states the trade-off or the failure case.
- **Never explain a term with itself.** If the term's own words appear in the definition as *explanation* rather than as a label, the definition teaches nothing. This is the most common failure and it hides in plain sight — "Low-**Rank** Adaptation: learns a small **low-rank** update" leaves a reader who does not know "low-rank" exactly where they started. Replace the jargon with the thing it denotes: "learns each update as the product of two thin matrices."
- **Self-contained**: never define a term using another undefined term from the same lesson.
- **Do not repeat the term as a prefix.** The renderer already shows the term as the tooltip's heading, so "Coverage: the fraction of inputs…" renders as *Coverage* / "Coverage: the fraction of inputs…" — stuttering, and wasted space in a small box. Start with the definition itself.
  - **Exception:** expanding an acronym is content, not repetition. `<abbr title="Expected Calibration Error: the average gap between…">ECE</abbr>` is correct — the expansion is precisely what the reader wants.
- **Load-bearing content**: state what it *is* and why it matters, not a dictionary tautology.
- **No markdown inside `title`**: it renders literally. Plain prose only.
- **Escape carefully**: the attribute is delimited by double quotes, so use single quotes inside, or none.

### Examples

✅ **Good** — states the mechanism and the consequence:
```markdown
<abbr title="Expected Calibration Error: the average gap between a model's confidence and its actual accuracy, measured in confidence bins. Lower is better.">ECE</abbr>
```

✅ **Good** — disambiguates an overloaded word:
```markdown
<abbr title="Here, a single scalar dividing the logits before softmax — not the sampling temperature used in text generation.">temperature</abbr>
```

❌ **Bad** — tautology, teaches nothing:
```markdown
<abbr title="Quantization to 4 bits.">4-bit quantization</abbr>
```

❌ **Bad** — explains the term with the term; "low-rank" is the very thing in question:
```markdown
<abbr title="Low-Rank Adaptation: freezes the pretrained weights and learns a small low-rank update B·A instead.">LoRA</abbr>
```
✅ **Fixed** — same idea, but "low-rank" is cashed out into something a reader can picture:
```markdown
<abbr title="Low-Rank Adaptation. Freezes the pretrained weights and learns each update as the product of two thin matrices — far fewer numbers to train than a full update.">LoRA</abbr>
```

❌ **Bad** — stutters against the tooltip heading:
```markdown
<abbr title="Coverage: the fraction of inputs the model answers rather than abstains on.">coverage</abbr>
```

❌ **Bad** — too long for a tooltip; belongs in prose:
```markdown
<abbr title="LoRA is a parameter-efficient fine-tuning method introduced by Hu et al. in 2021 which freezes the pretrained weights and injects trainable rank decomposition matrices into each layer of the Transformer architecture, greatly reducing the number of trainable parameters for downstream tasks while...">LoRA</abbr>
```

❌ **Bad** — breaks the attribute:
```markdown
<abbr title="The "relevance" label set">ESCI</abbr>
```

---

## 4. Placement

- Annotate at **first substantive use** in the lesson body — the point where the reader must understand it to continue.
- Prefer annotating in prose over tables (tooltips in narrow table cells can overflow on mobile).
- In a metadata/summary table, annotate the term where it is *explained*, not where it is merely listed.
- Never annotate inside a heading: headings feed the table of contents and the raw tag would leak into it.

---

## 5. Interaction With Other Guidelines

- **Prerequisites** ([02_structural_taxonomy](file:///c:/vinod/course-generation-guidelines/generic/02_structural_taxonomy_guidelines.md)): the prerequisite list defines the annotation floor. Anything above the floor is assumed; anything a learner meets *below* it gets annotated.
- **Cognitive load** ([03_pedagogical_clarity](file:///c:/vinod/course-generation-guidelines/generic/03_pedagogical_clarity_guidelines.md)): hover definitions are a load-reduction device — they let a lesson use precise vocabulary without a glossary detour. They do not license jargon padding.
- **Citations** ([01_originality_and_attribution](file:///c:/vinod/course-generation-guidelines/generic/01_originality_and_attribution_guidelines.md)): a tooltip is not a citation. Do not put paper links in `title`; cite in prose as normal.
- **Zero hallucination**: a wrong definition is worse than no definition, because the learner will trust it and never look it up. If unsure, leave it unannotated.

---

## 6. Reviewer Checklist

```markdown
- [ ] Every lesson annotates its load-bearing technical terms with `<abbr title="...">`.
- [ ] Each acronym is annotated on first use per lesson.
- [ ] No definition exceeds ~25 words or contains markdown/links.
- [ ] No definition explains the term using the term's own jargon (the "low-rank ⇒ low-rank" trap).
- [ ] No definition opens by repeating the term as a `Term:` prefix, except to expand an acronym.
- [ ] No term is annotated more than once per lesson.
- [ ] No annotations inside headings or code blocks.
- [ ] Annotation spacing is ≥ ~150 words of prose per annotated term, and ≤ 20 per lesson.
- [ ] Definitions are technically correct and self-contained (no undefined jargon inside a tooltip).
- [ ] Terms covered by the course prerequisites are NOT annotated.
```

---

## 7. Renderer Support Note

The course portal implements this convention in `MarkdownRenderer.tsx` via a `GlossaryTerm` component. This is required because the renderer strips raw HTML from inline text by default — without explicit `<abbr>` handling the definition is silently discarded and the learner sees an unhighlighted word with no tooltip.

If a course is authored for a different renderer, verify `<abbr title>` survives before relying on it. **Last verified:** 2026-07-14.
