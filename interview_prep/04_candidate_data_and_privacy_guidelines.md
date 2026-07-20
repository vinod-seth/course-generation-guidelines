# Resume-to-Offer Guideline 04: Candidate Data & Privacy

Governs the handling of a real person's resume, work history, and interview performance. Unique to this archetype: technical courses have no data subject; a Resume-to-Offer course is **built entirely out of one**.

---

## 1. Why This Guideline Exists

Every other course in this system is about a subject. This one is about a **person** — their employment history, their weaknesses, their scores, their failures in mock rounds. That changes the obligations:

- The source document contains **direct identifiers**: phone, email, postal address, sometimes date of birth or national ID.
- The generated course contains **judgements about a named individual**: "cannot defend this claim", "wrong level for this role".
- Courses are stored in **git repositories**, which are trivially made public and effectively permanent once pushed.

A leaked technical course is an inconvenience. A leaked Resume-to-Offer course publishes a named person's contact details alongside an assessment of their weaknesses.

---

## 2. Direct Identifiers — Never Committed

Strip from every generated artifact, without exception:

| Never include | Use instead |
|---|---|
| Phone number | omit entirely |
| Email address | omit entirely |
| Postal address | city/country only if genuinely needed (e.g. loop geography) |
| Date of birth, age, national ID, passport | omit entirely |
| Photograph | omit entirely |
| Marital status, gender, religion, health | omit entirely |
| Personal URLs *not* already public and professional | omit |

**Permitted** when professionally relevant and already public: name, university, degree, employer names, public GitHub/LinkedIn handles, publications.

> [!IMPORTANT]
> The candidate's resume PDF itself is a source input — it is **never committed to the course repository**. Read it, extract what the course needs, leave the file outside the repo.

---

## 3. Default Visibility: Private

A course built on a real person's resume defaults to a **private repository**.

```json
{ "archetype": "resume-to-offer", "visibility": "private" }
```

Publishing publicly requires the candidate's **explicit, informed** consent — informed meaning they know the repo contains an assessment of their weaknesses, that git history is effectively permanent, and that public repos are indexed and scraped.

### Before any push to a public remote
```markdown
- [ ] No phone, email, address, or ID anywhere in the repo.
- [ ] The source resume file is not committed.
- [ ] The candidate has seen what will be public.
- [ ] The candidate consented to this specific repository being public.
- [ ] Git history checked — secrets and PII survive in history after deletion.
```

**On history:** deleting PII in a later commit does not remove it. If PII was ever committed and pushed, the history must be rewritten (or the repository deleted and recreated) — deleting the file is not sufficient.

---

## 4. Assessment Data Is Sensitive Too

Scores, gap maps, floor-hit logs, and mock-round transcripts are candid records of someone's weaknesses. Treat them with the same care as identifiers:

- Keep them inside the private course repository.
- Never quote a named candidate's scores or failures into a shared template, example, or another course.
- When using a real course as a **reference implementation**, cite structure and patterns — never the person's actual scores, gaps, or claim-vault contents.

---

## 5. Writing About a Real Person

- **Assess the claim, not the person.** "This bullet has no backing artifact" — not "you are careless."
- **Second person, present tense**, addressed to the candidate. The course is written *for* them, not *about* them to an audience.
- **No speculation about protected characteristics**, and no inference about them from a name, university, or location.
- **No comparison to other named candidates**, ever.
- Bad news is delivered directly and with a remedy (see guideline 03 §7). Directness is respect; it is not licence for contempt.

---

## 6. Anonymising for Reuse

To reuse a real course as a template or example:

1. Replace the name with a role descriptor ("the candidate").
2. Replace employers/universities with generic equivalents ("a large e-commerce company").
3. Replace every metric with `[FILL: metric]` — never carry a real person's numbers into a template.
4. Strip scores, gap maps, and floor-hit logs entirely.
5. Retain only **structure**: chapter shapes, rubrics, question patterns.

---

## 7. Multi-Candidate Hygiene

When several candidates have courses in this system:

- **One repository per candidate.** Never a shared repo with per-person folders — a single access grant then exposes everyone.
- Never cross-reference one candidate's course from another's.
- Never use one candidate's resume, scores, or stories as an example inside another's course.

---

## 8. Reviewer Checklist

```markdown
- [ ] No phone, email, postal address, DOB, or government ID anywhere in the repo.
- [ ] The source resume file is not committed.
- [ ] Repository visibility is private, or documented consent exists for public.
- [ ] Git history is free of PII (not merely the current tree).
- [ ] Scores, gap maps, and mock transcripts stay inside the private repo.
- [ ] No real candidate's metrics, scores, or stories appear in templates or other courses.
- [ ] Prose assesses claims, not character; addressed to the candidate in second person.
- [ ] No speculation about or inference of protected characteristics.
- [ ] One repository per candidate; no cross-references between candidates.
```

---

## 9. Known Issue in the Reference Implementation

`local-courses-repo/Applied-Scientist-Interview-Gauntlet` is a **public** repository built from a real candidate's resume.

It does **not** contain phone, email, or address — those were never committed. It does contain the candidate's name context, university, and detailed project portfolio, and it is public.

Under this guideline the correct default would have been **private**. Recorded here as the worked example of why §3 exists: the decision to publish was never explicitly made, it was simply never questioned. Any future Resume-to-Offer course starts private unless the candidate says otherwise.
