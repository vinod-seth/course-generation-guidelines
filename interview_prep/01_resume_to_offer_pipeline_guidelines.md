# Resume-to-Offer Guideline 01: The Chapter Pipeline

Governs the structure and generation order of Resume-to-Offer courses. Read alongside [the archetype context](file:///c:/Autonomous-course-generation/course-creation-context/RESUME_TO_OFFER_ARCHETYPE.md), which explains *why* this archetype differs from a technical course.

**Applies in addition to** the generic guidelines (01 originality, 02 structural taxonomy, 03 pedagogical clarity, 04 glossary hover definitions, 05 quizzes). Where a rule here conflicts with a generic one, this file wins — but only inside a Resume-to-Offer course.

---

## 1. Generation Order Is Not Negotiable

Each chapter consumes the previous chapter's output. Generating out of order produces plausible-looking guesses.

```
0 Target Lock ──► 1 Company Dossier ──► 2 Resume Audit ──┐
                                                          ├──► 5 Gap Map ──► 6..N Round Prep ──► Final
                        3 Tech Stack Defined ─────────────┤
                        4 The Introduction ───────────────┘
```

| If generated too early | The failure it produces |
|---|---|
| Study plan before gap map | A generic syllabus that ignores this candidate's actual weaknesses |
| Round prep before dossier | Preparation for the wrong loop shape |
| Introduction before dossier | A pitch tuned to no particular company's values |
| Resume audit before target lock | Scoring against an imagined bar |

**Delivery may still be incremental** (one chapter per request). Order of *generation* is what is fixed.

---

## 2. Chapter 0 — Target Lock

### Required fields

```markdown
| Field | Value | Source |
|---|---|---|
| Company | | |
| Role title | | |
| Level | | ⚠️ drives the entire bar |
| Team / org | | `[UNKNOWN]` if not assigned |
| Geography | | affects process and comp bands |
| JD captured | yes/no | resolves JD-DEPENDENT branches |
| Interview date / timeline | | drives study-plan pacing |
| Recruiter process notes | | highest-authority source |
```

### Rules
- Every unknown is written `[UNKNOWN: …]`. Never fill a gap with a plausible default.
- **Level is mandatory-or-flagged.** If level is unknown, every downstream bar statement carries a visible warning, because the same resume clears one level and fails the next.
- If the JD is absent, list which chapters carry unresolved `⚠️ JD-DEPENDENT` branches so the candidate knows what to ask the recruiter.

---

## 3. Chapter 1 — Company Dossier

Full sourcing rules in [02_company_dossier_guidelines](02_company_dossier_guidelines.md). Structural requirements here:

- One section per round, in the order the candidate will face them.
- Each round documents: format, duration, **what it scores**, who conducts it, and how it can be failed.
- A "what changes by level" subsection — the same round is scored differently at L3 and L5.
- A closing **"Confirm with your recruiter"** checklist of every `[COMMON: unverified]` and `[UNKNOWN]` item.

> [!IMPORTANT]
> This chapter is the most trusted and the most fabricable in the course. A candidate who prepares for a five-round loop that is actually three rounds has been actively harmed. Every process claim is tagged or omitted.

---

## 4. Chapter 2 — Resume Audit & Score

Full rubric in [03_resume_audit_and_scoring_guidelines](03_resume_audit_and_scoring_guidelines.md). Structural requirements:

- **Claim extraction table** — every substantive resume assertion as its own row. Not a summary; an inventory.
- Two scores, reported separately and never averaged into one: **resume-intrinsic** and **company-relative**.
- Each finding pairs with a concrete remedy, and remedies are the seed of Chapter 5.
- A **Claim Vault**: every number on the resume, with the artifact that backs it or `[FILL: metric]` if unbacked.

---

## 5. Chapter 3 — Your Own Tech Stack, Defined

The course's entry point, and its most distinctive chapter.

### Purpose
The candidate sees the complete surface area they volunteered for interrogation — often for the first time. The intended reaction is productive alarm: *"I wrote that, and I could not define it right now."*

### Rules
1. **Sourced strictly from the resume.** If a term is not on the resume, it does not belong here. This is a mirror, not a textbook.
2. **Ordered by interrogation risk**, never alphabetically:

   `risk = P(interviewer opens here) × depth they can reach × centrality to the candidate's claims`

   Highest-risk terms first, because they are what the candidate must study first.
3. **Every term gets a hover definition** per [guideline 04](file:///c:/Autonomous-course-generation/course-generation-guidelines/generic/04_technical_term_glossary_guidelines.md) — `<abbr title="...">term</abbr>`, ≤25 words, no tautology, no `Term:` prefix stutter.
4. **Every term gets a self-check**: *"Can you define this in one sentence, then survive one follow-up?"* with a Yes/Partly/No box. The No column becomes a study queue.
5. **Grouped by resume section** (Projects / Skills / Education), so the candidate can see which line of their resume is the exposed one.
6. **Density exception:** the per-lesson spacing ceiling in guideline 04 does not apply to *this chapter*, because it is a glossary by design. All other chapters obey it normally.

### What this chapter must not become
- A general domain glossary (terms the candidate never claimed)
- A tutorial (depth belongs in round-prep chapters)
- A reassurance exercise — an honest "No" column is the chapter working correctly

---

## 6. Chapter 4 — The Introduction

The only question guaranteed in every round, and the only answer fully under the candidate's control.

### Required output
1. **Base narrative** — 60–90 seconds spoken. Present → relevant past → why this company/role.
2. **Per-round variants** — the technical-round opener differs from the behavioural one.
3. **The menu principle.** Every term volunteered in the introduction is a dish the interviewer may order. Each hook is labelled with the depth the candidate can currently defend; anything below "can survive follow-ups" is cut, not kept.
4. **Company-conditioned framing** — tuned to the target's published values or principles, cited per the dossier's provenance tags.
5. **Timed rehearsal instruction**, with the failure modes named (over-length, chronology drift, undefendable hooks).

### Rules
- Written in the candidate's voice, in first person, using their real history. Never invent experience.
- Every metric quoted traces to the Claim Vault or is cut.
- Include an explicit **omissions list** — what was deliberately left out and why. This is the chapter's highest-value content and the part candidates skip.

---

## 7. Chapter 5 — Gap Map → Study Plan

### The ordering rule
Order by **risk-weighted gap**, not by comfort:

```
priority = (bar_required − candidate_current) × P(this is tested) × round_weight
```

Strong candidates over-prepare their strengths. The plan must actively resist that, and should say so out loud where the ordering will feel counter-intuitive.

### Requirements
- Every gap traces to a specific Chapter 2 finding or Chapter 1 bar statement. No free-floating advice.
- Time-boxed against the Chapter 0 timeline. If the timeline cannot fit the gaps, say so plainly and propose what to sacrifice — a plan that silently assumes infinite time is a lie.
- Distinguish **closable** gaps (learnable before the interview) from **structural** ones (missing experience). Structural gaps get a *framing* strategy, not a study task.

---

## 8. Chapters 6…N — Round Prep

One module per round in the dossier. Standard technical-course guidelines apply in full here.

**Keep the format simple — no game mechanics.** No points/XP, no medal tiers, no boss fights, no streaks, no progress gating. The course is drills, model answers, mock rounds, and honest self-assessment; nothing is locked and nothing is scored for its own sake.

Reference implementation: `local-courses-repo/Applied-Scientist-Interview-Gauntlet` — note it predates this rule and still carries game mechanics; reuse its *content* patterns, not its scoring. Reusable patterns:
- Mastery stated plainly per topic: knows it / can derive it / **can defend it against five follow-ups**
- Mock-round simulations with honest written feedback
- A record of where depth ran out, reframed as the next study map
- Interactive companion notebooks that produce evidence rather than assurances

---

## 9. Final — Mock Loop & Readiness Call

- Full simulated loop in the dossier's real order.
- **Re-score** against the Chapter 2 baseline; show the delta.
- **An honest go/no-go.** The readiness call must be permitted to conclude *not ready*, with what would change that. A course that always ends in "you're ready" carries no information.

---

## 10. Reviewer Checklist

```markdown
- [ ] Chapters generated in pipeline order; no chapter depends on a later one.
- [ ] Chapter 0 records every unknown explicitly; level is captured or flagged everywhere.
- [ ] Every company process claim carries a provenance tag; a "confirm with recruiter" list exists.
- [ ] Resume audit reports intrinsic and company-relative scores separately.
- [ ] Chapter 3 contains only terms present on the resume, ordered by interrogation risk, each with a hover definition and a self-check.
- [ ] Introduction includes per-round variants and an explicit omissions list.
- [ ] Gap map is risk-weighted, time-boxed, and separates closable from structural gaps.
- [ ] Readiness call is capable of returning "not ready".
- [ ] No fabricated candidate metrics; unbacked numbers appear as [FILL: metric].
- [ ] No PII in any published artifact.
```
