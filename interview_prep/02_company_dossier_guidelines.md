# Resume-to-Offer Guideline 02: Company Dossier Sourcing

Governs Chapter 1 — the description of the target company's interview loop. This is the single most dangerous chapter in the archetype, and it gets the strictest rules.

---

## 1. Why This Chapter Needs Its Own Rules

A candidate trusts the dossier more than any other chapter, because it claims to describe reality rather than teach a concept. That trust is precisely what makes fabrication harmful:

- A candidate told to expect **five rounds** who faces **three** has mis-allocated weeks of preparation.
- A candidate taught an **invented internal rubric name** who repeats it in the room sounds like they are guessing about the company — worse than saying nothing.
- Hiring loops **change**. A dossier accurate in 2024 can be wrong in 2026 with no visible signal that it aged.

Language models produce confident, plausible, well-structured descriptions of company interview processes whether or not they know them. That is exactly the failure this guideline exists to prevent.

---

## 1a. Attempt Verification Before Claiming You Cannot

**Fetch the sources. Do not assert a limitation you have not tested.**

Large employers publish more about hiring than authors assume — Amazon, for instance, publishes its Leadership Principles, its interview stages, its Bar Raiser program, and even loop size ranges and feedback timelines. A dossier full of `[COMMON: unverified]` tags when `[OFFICIAL]` sources were one fetch away is a *failure of effort*, not an honest limitation.

### Required order
1. **Try the company's own sources first** — careers site, newsroom, engineering blog.
2. Only after a fetch actually fails may you record the failure — with the URL and what happened.
3. `[COMMON: unverified]` is for facts that **are not published anywhere authoritative**, not for facts you did not look for.

> [!IMPORTANT]
> Declaring "I could not verify this" without having attempted it is worse than an untagged claim: it looks like diligence while delivering none, and it teaches the candidate to distrust sources that were in fact available. If a tool for fetching pages exists in the environment, use it before writing the chapter.

**Worked failure (recorded from this system's own history, 2026-07-20):** an author concluded "no network access" from a single failed `curl` to one host, then wrote a permanent "NOT LIVE-VERIFIED" banner into a dossier — while a working web-fetch tool sat unused in the same session. Every fact in that chapter was in fact publicly published and was recovered on the first attempt once tried. One failed request is evidence about one request.

---

## 2. Provenance Tagging (mandatory)

Every process claim carries exactly one tag. **An untagged process claim is a defect.**

| Tag | Meaning | How it may be phrased |
|---|---|---|
| `[OFFICIAL: <source>, <date>]` | The company's own published material — careers site, engineering blog, official prep guide | Stated as fact |
| `[REPORTED: <source>, <date>]` | Credible secondhand — reputable press, a published interview with a named employee | "X reports that…" — never as company doctrine |
| `[COMMON: unverified]` | Widely circulated in candidate communities, no authoritative source | **Must** carry "commonly reported — confirm with your recruiter" |
| `[RECRUITER: <date>]` | What the candidate's own recruiter told them | Highest authority; **overrides every other tag** |
| `[UNKNOWN]` | Not established | Stated as unknown. Never filled with a plausible guess |

### Worked example

```markdown
The loop typically runs 4–5 rounds `[COMMON: unverified]`, with one round dedicated
to the company's published leadership principles `[OFFICIAL: careers site, 2026-07-14]`.
Your recruiter confirmed 4 rounds on 2026-07-10 `[RECRUITER: 2026-07-10]` — treat that
as authoritative over the range above.
```

Note what the example does: it does not hide the conflict between sources, it *resolves* it by authority and says so.

### The precedence ladder
`[RECRUITER]` > `[OFFICIAL]` > `[REPORTED]` > `[COMMON]` > `[UNKNOWN]`

When sources conflict, present the higher-authority claim as operative and **name the conflict** rather than silently dropping the loser. A candidate who knows sources disagree asks better questions.

---

## 3. What May Never Be Stated

| Never | Why |
|---|---|
| Invented round counts, durations, or names | The core fabrication risk |
| Internal rubric names, scorecard fields, or level codes not publicly published | Sounds like leaked knowledge; usually wrong |
| Named individuals as the candidate's interviewers | Unknowable and creepy |
| "Pass rates", "acceptance rates", or quotas | Almost never published; invites false confidence or despair |
| Reproduced real interview questions from leak sites | Originality/attribution violation; often stale; encourages memorisation over defence |
| Anything presented as the company's own internal document | Impersonation (see §6) |

> [!IMPORTANT]
> If a fact cannot be tagged, it does not go in the course. "Probably" is not a provenance tag.

---

## 4. Required Structure

```markdown
# Chapter 1 — The <Company> Loop: <Role>, <Level>

| | |
|---|---|
| **Last verified** | YYYY-MM-DD |
| **Volatility** | High — hiring processes change without notice |
| **Level assumed** | <level> (⚠️ if unknown, every bar below is unreliable) |

## The Loop at a Glance
<table: round | format | duration | what it scores | provenance tag>

## Round-by-Round
### Round N — <name>
- **Format / duration** …
- **What it scores** …
- **Who conducts it** …
- **How candidates fail it** …
- **What changes by level** …

## What Changes By Level
## Confirm With Your Recruiter
<checklist of every [COMMON: unverified] and [UNKNOWN] item>
```

### The "Confirm With Your Recruiter" checklist
Mandatory. It converts the dossier's weakest claims into a concrete action, and it is the honest counterpart to the tagging system:

```markdown
- [ ] How many rounds, and in what order?
- [ ] Which level am I being interviewed at?
- [ ] Is there a system-design round for this level? ⚠️ JD-DEPENDENT
- [ ] Language/tooling constraints for coding rounds?
- [ ] Who conducts the behavioural round?
```

---

## 5. Volatility & Maintenance

- The dossier header carries a **`Last verified` date**, and every tag carries its own date.
- Any dossier older than **6 months** is flagged stale on sight, with a banner instructing re-verification before use.
- Re-verification is a *chapter-level* action: re-check sources, update dates, and record what changed.
- Where a process is known to have changed recently, say so — a candidate coached on last year's loop by a confident-sounding document is worse off than one who knows the ground is moving.

---

## 6. No Impersonation of the Company

The dossier is **a candidate's preparation aid**, never a representation of the company.

- Never produce a document that *looks like* the company's internal rubric, scorecard, or interviewer guide.
- Never write in the company's voice ("At <Company>, we look for…") unless quoting published material with an `[OFFICIAL]` tag and visible attribution.
- Never use the company's logo, letterhead, or branding in the course.
- Published values or principles may be **named and cited**; they may not be paraphrased into invented additional principles.

---

## 7. Using Published Company Values Well

Most large employers publish hiring values. Using them correctly is the difference between a tailored course and a generic one:

- **Cite them by their real published names**, with an `[OFFICIAL]` tag and link.
- **Map each to the rounds where it is actually scored** — that mapping is the useful analytical work.
- **Do not invent additional values**, reorder official lists as if authoritative, or claim internal weightings that are not published.
- Where the candidate must produce stories against these values, that work belongs in the behavioural round-prep chapter, not here.

---

## 8. Reviewer Checklist

```markdown
- [ ] The company's own published sources were actually fetched before writing.
- [ ] No [COMMON: unverified] tag covers a fact that is in fact officially published.
- [ ] Any "could not verify" claim names the URL tried and what failed.
- [ ] Every process claim carries exactly one provenance tag.
- [ ] No untagged claims; no "probably/typically" standing in for a tag.
- [ ] Source conflicts are surfaced and resolved by the precedence ladder, not hidden.
- [ ] Header carries Last verified; dossiers older than 6 months are flagged stale.
- [ ] A "Confirm With Your Recruiter" checklist exists and covers every unverified/unknown item.
- [ ] No invented rubric names, level codes, pass rates, or named interviewers.
- [ ] No reproduced leaked interview questions.
- [ ] Company values cited by real published names with [OFFICIAL] tags; none invented.
- [ ] Nothing written in the company's voice or styled as an internal document.
- [ ] Level is stated, or its absence is flagged wherever a bar is described.
```
