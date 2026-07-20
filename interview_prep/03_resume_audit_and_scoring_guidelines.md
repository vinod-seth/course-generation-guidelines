# Resume-to-Offer Guideline 03: Resume Audit & Scoring

Governs Chapter 2 — extracting every claim on the resume, scoring it, and reporting two verdicts the candidate can audit and recompute.

---

## 1. The Scoring Contract

A resume score is useful only if the candidate can **reproduce it**. Every point must trace to a stated criterion and an observable fact in the resume.

**The contract, stated to the candidate in the chapter itself:**

> Every point below is computed from a rule you can read. If you disagree with a score, you can point at the rule and the line of your resume it was applied to. Nothing here is a vibe.

### Forbidden
- A score with no visible derivation ("Resume strength: 7.5/10")
- Decimals implying precision the rubric cannot support — **integers only**
- Comparisons to unmeasured populations ("stronger than 80% of applicants") — we have no such data
- Scores that move without a rule changing

### Required
- Per-dimension raw scores with the criterion that produced each
- The arithmetic shown, so the total is checkable
- A **band** alongside the number, because the band is the honest resolution and the number is the trackable one

---

## 2. Two Scores, Never Averaged

| Score | Question it answers | Depends on target? |
|---|---|---|
| **Resume-Intrinsic** | Is this resume defensible on its own terms? | No |
| **Company-Relative** | Does it clear *this* company's bar at *this* level? | Yes |

Reporting one number hides the case that matters most: **a strong resume that misses a specific bar**. A candidate with excellent research projects applying to an infrastructure-heavy team should see high intrinsic and low relative — that gap *is* the finding, and averaging destroys it.

Both are reported as `score/100` plus a band. They are never combined.

---

## 3. Resume-Intrinsic Rubric (100 points)

### A. Evidence & Verifiability — 30 pts
Can each claim be backed by an artifact the candidate can produce?

| Criterion | Pts |
|---|---|
| Every quantitative claim traces to a log, repo, or publication | 12 |
| Projects have inspectable artifacts (repo, notebook, paper, demo) | 10 |
| No claim the candidate cannot demonstrate on request | 8 |

*Deduct the full sub-score for any number the candidate cannot source. An unsourced metric is a liability, not a neutral.*

### B. Specificity — 20 pts
| Criterion | Pts |
|---|---|
| Concrete methods named, not category words ("QLoRA + NF4", not "used LLMs") | 8 |
| Outcomes stated with magnitude and metric, not adjectives | 7 |
| The candidate's *own* contribution is distinguishable from the team's | 5 |

### C. Depth Signals — 20 pts
Does the resume advertise depth the candidate actually has?

| Criterion | Pts |
|---|---|
| Claims reflect design decisions, not tool usage | 8 |
| Trade-offs or limitations acknowledged anywhere | 6 |
| No term the candidate cannot define and defend one level down | 6 |

*This sub-score is computed **against Chapter 3's self-check results**, which is why Chapter 3 precedes the final scoring pass.*

### D. Interrogation Surface Hygiene — 15 pts
| Criterion | Pts |
|---|---|
| No undefendable buzzword padding | 6 |
| Claim density proportionate to what can be defended in 45 minutes | 5 |
| No internal contradictions between sections | 4 |

### E. Communication — 15 pts
| Criterion | Pts |
|---|---|
| Each bullet's first clause carries the result | 6 |
| Consistent tense, person, and formatting | 4 |
| Scannable in 30 seconds — the real screening budget | 5 |

### Bands
| Score | Band | Meaning |
|---|---|---|
| 85–100 | **Gold** | Defensible throughout; interrogation is an opportunity |
| 70–84 | **Silver** | Sound, with identified soft spots |
| 50–69 | **Bronze** | Real content, but exposed claims need work before the loop |
| < 50 | **At Risk** | Overclaiming or unverifiable content likely to be caught |

---

## 4. Company-Relative Rubric (100 points)

Scored **against the Chapter 1 dossier and the JD**. Every criterion must cite the bar it is scored against; an uncited criterion is a defect.

### A. Role Match — 30 pts
Required skills present, at the depth the level demands.

### B. Level Fit — 25 pts
Scope, autonomy, and ambiguity of the candidate's work versus what the level expects. *The most common source of rejection for otherwise strong candidates, and the least visible to them.*

### C. Round Readiness — 25 pts
Distributed across the dossier's actual rounds, weighted as the dossier weights them. A loop with a heavy behavioural round scores it heavily here.

### D. Signal Alignment — 20 pts
Match to the company's **published** values or principles, cited with `[OFFICIAL]` tags per the dossier guideline. Never invented values.

### Bands
| Score | Band | Meaning |
|---|---|---|
| 80–100 | **Clears the bar** | Prepare to defend, not to acquire |
| 60–79 | **Borderline** | Outcome depends on execution in the room |
| 40–59 | **Gap** | Identifiable, possibly closable before the interview |
| < 40 | **Mismatch** | Wrong level or wrong role — say so plainly |

---

## 5. The Claim Extraction Table

Not a summary — an **inventory**. Every substantive assertion gets a row.

```markdown
| # | Claim (verbatim) | Type | Backing artifact | Defensible to | Risk | Action |
|---|---|---|---|---|---|---|
| 1 | "reached 0.71 macro-F1" | metric | [FILL: run log] | — | HIGH | Locate log or remove number |
| 2 | "QLoRA (4-bit NF4)" | method | repo/config | 5 follow-ups | LOW | — |
| 3 | "improved search relevance" | outcome | none | 1 follow-up | HIGH | Quantify or reframe |
```

- **Defensible to** — depth in follow-ups, taken from Chapter 3's self-check, not guessed.
- **Risk** — probability an interviewer opens here × damage if the candidate stalls.
- Every HIGH row must appear in the Chapter 5 gap map. No exceptions.

---

## 6. The Claim Vault

Every number on the resume, with its backing artifact:

```markdown
| Resume number | Value | Source artifact | Status |
|---|---|---|---|
| macro-F1 | [FILL: metric] | runs/esci/eval.json | UNVERIFIED |
| trainable params <2% | [FILL: metric] | training config | UNVERIFIED |
```

**The rule that governs the whole archetype:** a number the candidate cannot source is either located in their logs or **removed from the resume**. It is never left standing and never invented by the course. An honest qualitative claim outscores an unsupported figure, because the figure invites an interrogation the candidate loses.

---

## 7. Delivering Bad News

The audit's value is entirely in its willingness to be unwelcome. A course that scores every resume 80+ is decorative.

### Rules
- **Lead with the finding, not a compliment sandwich.** "This number has no backing artifact" is respectful; burying it is not.
- **Every finding carries a remedy.** Criticism without a next step is just discouragement.
- **Separate the fixable from the structural.** Missing a metric is fixable this week. Missing three years of experience is not — that gets a *framing* strategy, never a study task pretending it can be closed.
- **Never inflate to motivate.** The candidate's competitor is not this course; it is an interviewer who will find the same weakness with less kindness.
- **Say "wrong level" or "wrong role" when true.** A `Mismatch` band that is honestly delivered saves a candidate months.

---

## 8. Re-Scoring

The final chapter re-scores against this baseline and shows the delta. Requirements:
- Identical rubric, identical criteria — a score that improved because the rubric softened is meaningless.
- Show per-dimension movement, not just the total.
- Where the score did **not** move, say so; silent omission of a stalled dimension is the numeric equivalent of inflation.

---

## 9. Reviewer Checklist

```markdown
- [ ] Both scores reported separately; never averaged into one figure.
- [ ] Every point traces to a stated criterion and an observable resume fact.
- [ ] Arithmetic is shown; totals are checkable by the candidate.
- [ ] Integer scores only; no false-precision decimals.
- [ ] No comparisons to unmeasured applicant populations.
- [ ] Company-relative criteria each cite the dossier bar or JD line they score against.
- [ ] Claim extraction table inventories every substantive claim, not a summary.
- [ ] Every HIGH-risk claim appears in the Chapter 5 gap map.
- [ ] Claim Vault lists every resume number with artifact or [FILL: metric].
- [ ] Findings pair with remedies; structural gaps get framing, not busywork.
- [ ] The rubric is capable of producing "At Risk" / "Mismatch" and the course says so plainly when true.
- [ ] Re-score uses the identical rubric and reports per-dimension deltas.
```
