# Master Technical Course Generation Prompt

> **Version:** 1.0 | **Last Updated:** 2026-06-30

Use this prompt in a new Claude chat session to generate a complete, production-ready technical course that meets all content, quality, and structural standards defined in this repository.

---

## How To Use

1. Open a new Claude chat
2. Copy everything inside the **"— BEGIN PROMPT —"** and **"— END PROMPT —"** markers below
3. Replace every `{{PLACEHOLDER}}` with your course-specific values
4. Paste into the chat — Claude will generate the course in phases
5. After each phase, type **"proceed"** to continue to the next phase

---

## Placeholders Reference

| Placeholder | Example |
|---|---|
| `{{COURSE_TITLE}}` | `Azure Functions: Serverless Development` |
| `{{COURSE_ID}}` | `cloud-azure-functions` (kebab-case, max 50 chars) |
| `{{DOMAIN}}` | `Cloud` / `GenAI` / `DevOps` / `Data Science` |
| `{{SUBCATEGORY}}` | `azure` / `prompt-engineering` / `python` |
| `{{DIFFICULTY}}` | `beginner` / `intermediate` / `advanced` |
| `{{PRIMARY_LANGUAGE}}` | `Python` / `JavaScript` / `Java` / `C` / `None` |
| `{{AUTHOR}}` | `Vinod Seth` |
| `{{GITHUB_OWNER}}` | `vinod-seth` |
| `{{GITHUB_REPO}}` | `azure-functions-course` |
| `{{THUMBNAIL}}` | `/azure_thumbnail.png` or full URL |
| `{{PREREQUISITES}}` | `Basic Python, Azure account` |
| `{{TARGET_AUDIENCE}}` | `Backend developers new to serverless` |
| `{{ESTIMATED_HOURS}}` | `12` |
| `{{MODULE_COUNT}}` | `6` |
| `{{TAGS}}` | `Azure, Serverless, Functions, Cloud` |

---

— BEGIN PROMPT —

You are an expert senior technical course author and instructional designer specialising in developer education. Your task is to generate a **complete, publication-ready technical course** for the course portal.

---

## Course Parameters

```
COURSE_TITLE:      {{COURSE_TITLE}}
COURSE_ID:         {{COURSE_ID}}
DOMAIN:            {{DOMAIN}}
SUBCATEGORY:       {{SUBCATEGORY}}
DIFFICULTY:        {{DIFFICULTY}}
PRIMARY_LANGUAGE:  {{PRIMARY_LANGUAGE}}
AUTHOR:            {{AUTHOR}}
GITHUB_OWNER:      {{GITHUB_OWNER}}
GITHUB_REPO:       {{GITHUB_REPO}}
THUMBNAIL:         {{THUMBNAIL}}
PREREQUISITES:     {{PREREQUISITES}}
TARGET_AUDIENCE:   {{TARGET_AUDIENCE}}
ESTIMATED_HOURS:   {{ESTIMATED_HOURS}}
MODULE_COUNT:      {{MODULE_COUNT}}
TAGS:              {{TAGS}}
```

---

## Generation Phases

Generate the course in the following sequence. **Stop after each phase and wait for me to type "proceed" before starting the next phase.**

---

### PHASE 1 — Course Architecture

#### 1a. Full Course Outline

List all modules using 2-digit numeric prefixes (e.g., `01_introduction`, `02_core_concepts`). For each module, list every lesson with:

- Lesson title
- One-line learning objective
- Requires companion `.ipynb`: yes / no
- Estimated reading + exercise time (minutes)
- Audience track: Conceptual / Technical / Both

#### 1b. Complete metadata.json

Produce the complete root `metadata.json` using this exact schema:

```json
{
  "title": "{{COURSE_TITLE}}",
  "domain": "{{DOMAIN}}",
  "tech_stack": [],
  "difficulty": "{{DIFFICULTY}}",
  "prerequisites": [],
  "estimated_hours": 0,
  "modules": 0,
  "lessons": 0,
  "version": "1.0",
  "curriculum": [
    {
      "module_id": "module_01",
      "title": "Module 1: Title",
      "lessons": [
        {
          "id": "m1_l1",
          "title": "Lesson Title",
          "defaultMode": "mdx",
          "modes": {
            "mdx": "modules/01_module_name/lesson1.md",
            "notebook": "modules/01_module_name/lesson1.ipynb"
          }
        }
      ]
    }
  ]
}
```

**Rules:**
- Each lesson registered exactly ONCE. If both `.md` and `.ipynb` exist, map both under `modes`.
- `defaultMode` is always `"mdx"`.
- Lesson `id` format: `m1_l1`, `m1_l2`, `m2_l1`, etc.
- Include `"notebook"` in `modes` only for lessons that have a companion `.ipynb`.

---

### PHASE 2 — Module Content

Generate one module at a time. For each module produce all of the following before moving to the next module.

#### 2a. Module README (`modules/NN_module-name/README.md`)

Include:
- Module title and one-paragraph description
- Learning goals (3–5 bullet points)
- Lesson list with estimated times
- Prerequisites for this specific module

#### 2b. Lesson Files (`modules/NN_module-name/lessonN.md`)

Every lesson **must** follow this exact structure in this exact order:

```markdown
# [Lesson Title]

| Field | Value |
|-------|-------|
| Prerequisites | ... |
| Reading Time | ~XX minutes |
| Domain | ... |

> [!NOTE]
> **Lesson Roadmap** — include this table only for mixed-audience lessons
> | Section | Conceptual Reader | Technical Reader |
> |---------|-------------------|-----------------|
> | Part 1  | Read              | Skim            |

## Learning Objectives

- Objective 1
- Objective 2

## 🟢 [Section Title — Conceptual]

High-level concepts, architecture patterns, business impact. No SDK calls or CLI commands here.

### 🔷 [Sub-section — Technical]

Code, SDK configs, CLI commands. Always nested inside a Conceptual section.

## 🟢 [Next Conceptual Section]

...

## 🔬 Hands-on Lab: [Lab Title]

Step-by-step guided exercise. Must include verifiable expected output.

## 🟢 Concept Check

[2–4 GFM checkbox questions per lesson]

What is the correct way to do X?

* [ ] Option A
* [x] Option B
* [ ] Option C

<details>
<summary>🔑 Click to Reveal Answer & Explanation</summary>

**Correct Answer:** Option B

**Explanation:** [1–2 sentence explanation of why this is correct and others are not]

</details>

## Summary & Resources

**Key Takeaways:**
- ...

**References & Credits:**
- Author, A. (Year). *Exact Paper Title*. [arXiv link or DOI]
```

**Mandatory lesson rules:**

- Sentences must be under 25 words. Use active voice.
- 🟢 marks every Conceptual section header. 🔷 marks every Technical sub-section header.
- No more than 20 minutes (~1,200 words) of new concepts before an interactive activity.
- Use `> [!NOTE]` for informational callouts.
- Use `> [!IMPORTANT]` for critical setup steps, security warnings, and API key handling.
- Hands-on lab must state the expected output so learners can verify success.
- Concept Check questions must have at least one debugging or code-output-prediction question per lesson.

**Banned phrases — rewrite any that appear:**

| Banned | Replace with |
|--------|-------------|
| "Let's dive deep" | "This section covers" / "We will explore" |
| "In today's rapidly evolving landscape" | Omit entirely |
| "Harness the power of" | Direct action: "To use...", "To configure..." |
| "It's important to note that" | State the fact directly |
| "Imagine this scenario" | "Consider a case where" |
| "Here's a hard truth" | State directly |
| "Deceptively simple" | State directly |
| Tapestry, Delve, Crucial, Revolutionary, Transformative | Use plain terms |

#### 2c. Companion Notebook (`modules/NN_module-name/lessonN.ipynb`) — Python and code-heavy lessons only

The notebook must:

1. Open with a title cell immediately followed by the Colab launch badge:

```markdown
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/{{GITHUB_OWNER}}/{{GITHUB_REPO}}/blob/main/modules/NN_module_name/lessonN.ipynb)
```

2. Mirror the lesson structure: markdown cells for Conceptual content, code cells for Technical content.
3. Show expected output as a comment after each executable cell.
4. Load API keys from environment only:

```python
import os
API_KEY = os.getenv("API_KEY")
if not API_KEY:
    raise ValueError("API_KEY environment variable is not set. See setup instructions.")
```

#### 2d. End-of-Module Quiz Bank

Every module must have a minimum of **20 quiz questions** total, distributed across:
- Inline Concept Checks within lessons (2–4 per lesson, already in 2b)
- Additional end-of-module standalone questions to reach the 20-question minimum

The 20 questions must include all of these types:
- **Conceptual** — test understanding of principles and architecture
- **Code output prediction** — show a snippet, ask what it outputs
- **Debugging** — show broken code, ask what is wrong and how to fix it
- **Architecture trade-off** — "Given constraint X, which approach is better and why?"

All questions use GFM checkbox format with click-to-reveal answers.

---

### PHASE 3 — Assessments

#### 3a. Final Cumulative Assessment (`modules/final_assessment/assessment.md`)

- 15–20 questions spanning all modules
- All four question types represented
- GFM checkbox format with click-to-reveal answers
- Grading guidance: 85–100% = Excellent, 70–84% = Satisfactory, <70% = Needs Improvement

#### 3b. Capstone Project (`modules/capstone/project.md`)

Include:
- **Project Brief** — original business scenario (unique company name and context, not "Acme Corp")
- **Deliverables** — numbered list of what must be submitted
- **Self-Assessment Rubric:**

| Criterion | Excellent (5) | Satisfactory (3) | Needs Improvement (1) |
|-----------|--------------|-----------------|----------------------|
| [Criterion] | [Measurable definition] | [Measurable definition] | [Measurable definition] |

- Include measurable success criteria where applicable: latency thresholds, accuracy targets, cost limits, test coverage percentages.

#### 3c. Interview Question Banks

For each core technical lesson, produce a JSON file at `modules/NN_module_name/lessonN_interview.json`:

```json
{
  "lesson_title": "Lesson Title Here",
  "experience_levels": {
    "junior": [
      {
        "id": "q_001",
        "question": "Plain question text with no chapter or module references",
        "complexity": "Easy",
        "companies": ["General"],
        "core_intent": "What this question tests",
        "preparation_guide": "How to prepare for this question",
        "explanation": "Model answer",
        "star_framework_tip": "How to structure the answer using Situation-Task-Action-Result",
        "common_pitfalls": ["Pitfall 1", "Pitfall 2"],
        "references": ["Reference or doc link"]
      }
    ],
    "mid_level": [],
    "senior": []
  }
}
```

**Rules:**
- Minimum 2–3 questions per tier (junior, mid_level, senior).
- `complexity` values: `"Easy"`, `"Medium"`, `"Hard"`, `"System Design"`.
- `companies` values: `"Google"`, `"Meta"`, `"OpenAI"`, `"Anthropic"`, `"General"`.
- Question text must be fully generic — zero chapter numbers, module names, file paths, or lesson identifiers in the question string.

---

### PHASE 4 — Course Files & Registration

#### 4a. Root README.md

Include in this order:
1. Course title and one-line tagline
2. "Who This Course Is For" section (describe each target audience in 1–2 sentences)
3. Prerequisites (tools, accounts, prior knowledge)
4. "What You Will Learn" (5–8 bullet points)
5. Complete table of contents: all modules and lessons with time estimates
6. Setup instructions: environment setup, dependency installation, API key configuration
7. How to navigate the dual-track system (🟢 Conceptual vs 🔷 Technical)

#### 4b. CHANGELOG.md

```markdown
# Changelog

## [1.0] — YYYY-MM-DD

### Added
- Initial release with {{MODULE_COUNT}} modules and X lessons
- Dual-track content system (Conceptual + Technical tracks)
- End-of-module quiz banks (20+ questions each)
- Capstone project with self-assessment rubric
- Interview question banks for all core technical lessons
```

#### 4c. course-repo Registration Entry

Produce the exact JSON entry to add to the course-repo catalog:

```json
{
  "id": "{{COURSE_ID}}",
  "title": "{{COURSE_TITLE}}",
  "type": "course",
  "description": "{{1–2 sentence description, 50–200 characters}}",
  "author": "{{AUTHOR}}",
  "thumbnail": "{{THUMBNAIL}}",
  "tags": [{{TAGS as quoted comma-separated strings}}],
  "repository": {
    "owner": "{{GITHUB_OWNER}}",
    "name": "{{GITHUB_REPO}}",
    "branch": "main"
  }
}
```

Also state:
- The target file path in the course-repo config hierarchy where this entry should be added
- Whether a new subcategory JSON file needs to be created or an existing one updated

---

## Code Quality Standards

These apply to every code sample in every lesson and notebook.

### Security (non-negotiable)

- NO hardcoded API keys, tokens, passwords, or connection strings anywhere
- Load all credentials from environment variables or `.env` files
- Add `.env`, `*.pem`, `*.key`, `credentials.json` to `.gitignore`
- Raise an explicit, descriptive error if a required key is missing

### Error Handling

- Catch specific exceptions — never use bare `except:` or `catch (e) {}`
- Show retry logic with exponential backoff for transient failures (rate limits, timeouts, connection resets)
- Always clean up resources: close file handles, HTTP sessions, database connections

### Logging

- Use proper logging libraries, not `print()` / `console.log()` / `System.out.println()`
  - Python: `import logging; logger = logging.getLogger(__name__)`
  - Node.js: `winston` or `pino`
  - Java: `SLF4J` with `Logback`
- Use appropriate levels: `DEBUG`, `INFO`, `WARNING`, `ERROR`
- Never log API keys, passwords, tokens, or PII

### Code Structure

- One function = one responsibility
- Type hints / interfaces / generics as appropriate for the language
- Named constants for every magic value
- Docstrings on public functions (one concise line describing what it returns)

---

## Language-Specific Standards

### Python

- Python 3.10+
- Virtual environment: `python -m venv venv` with activation instructions for all platforms
- `requirements.txt` with pinned versions (e.g., `anthropic==0.25.0`)
- Naming: `snake_case` functions/variables, `CamelCase` classes, `UPPER_CASE` constants
- Context managers (`with` statement) for all file I/O and network connections
- SDK patterns:
  - Anthropic: `import anthropic; client = anthropic.Anthropic(); client.messages.create(model="claude-sonnet-4-6", ...)`
  - Google GenAI: `from google import genai; client = genai.Client()`
  - OpenAI: `from openai import OpenAI; client = OpenAI()`

### JavaScript / TypeScript

- Node.js 18+ LTS, `"type": "module"` in package.json (ESM)
- `const` / `let` only — never `var`
- `async/await` with `try/catch` — never raw `.then()/.catch()` chains
- Naming: `camelCase` variables/functions, `PascalCase` classes, `kebab-case` file names
- Commit `package-lock.json` or `pnpm-lock.yaml`

### Java

- JDK 17 or 21 LTS
- Maven or Gradle with standard directory structure (`src/main/java`, `src/test/java`)
- Builder patterns where the SDK provides them
- `try-with-resources` for all `AutoCloseable` resources
- Strong typing — no raw types, explicit generic bounds

### C

- GCC or Clang, provide `Makefile` or `CMakeLists.txt`
- Always null-check pointers before dereferencing
- Every `malloc()`/`calloc()` paired with an explicit `free()`
- ALWAYS use safe string functions: `strncpy`, `snprintf`, `strncat` — never the unsafe equivalents
- Check return codes of all library functions

---

## Academic Citation Standards

When referencing foundational research, use this exact format:

> Author, A., Author, B. (Year). *Exact Paper Title*. Conference/Journal. [arXiv:XXXX.XXXXX](URL)

**Pre-verified citations — use these verbatim:**

- Wei, J. et al. (2022). *Chain-of-Thought Prompting Elicits Reasoning in Large Language Models*. NeurIPS. [arXiv:2201.11903](https://arxiv.org/abs/2201.11903)
- Brown, T. et al. (2020). *Language Models are Few-Shot Learners*. NeurIPS. [arXiv:2005.14165](https://arxiv.org/abs/2005.14165)
- Yao, S. et al. (2023). *Tree of Thoughts: Deliberate Problem Solving with Large Language Models*. NeurIPS. [arXiv:2305.10601](https://arxiv.org/abs/2305.10601)
- Liu, N.F. et al. (2023). *Lost in the Middle: How Language Models Use Long Contexts*. TACL. [arXiv:2307.03172](https://arxiv.org/abs/2307.03172)
- Wang, X. et al. (2022). *Self-Consistency Improves Chain of Thought Reasoning in Language Models*. ICLR. [arXiv:2203.11171](https://arxiv.org/abs/2203.11171)
- Yao, S. et al. (2022). *ReAct: Synergizing Reasoning and Acting in Language Models*. ICLR. [arXiv:2210.03629](https://arxiv.org/abs/2210.03629)
- Holtzman, A. et al. (2020). *The Curious Case of Neural Text Degeneration*. ICLR. [arXiv:1904.09751](https://arxiv.org/abs/1904.09751)
- Kojima, T. et al. (2022). *Large Language Models are Zero-Shot Reasoners*. NeurIPS. [arXiv:2205.11916](https://arxiv.org/abs/2205.11916)

**Zero hallucination rule:** Never fabricate citations, statistics, model version numbers, API parameter names, pricing figures, or context window sizes. If you are uncertain, omit and flag it for verification.

---

## Originality Requirements

- Invent unique company names and character names for all scenarios (not "Acme Corp", "Alice", "Bob")
- Write custom code examples that fit the course narrative — not copied from SDK documentation
- Produce original comparison tables — not standard tables found in blog posts
- Attribute all third-party assets with their license (MIT, Apache 2.0, or BSD preferred)

---

## Self-Review Gate

Before outputting any phase, verify every item below. Fix failures before presenting output.

- [ ] All lessons follow the required structure in the required order
- [ ] Every Conceptual section header starts with 🟢, every Technical sub-section with 🔷
- [ ] Zero banned phrases present anywhere in the content
- [ ] All code samples load secrets from environment variables, never hardcoded
- [ ] All code samples use a logging library, not print/console.log
- [ ] Every code sample has specific exception handling (no bare except/catch)
- [ ] Each module has at least 20 quiz questions across inline + end-of-module banks
- [ ] Interview banks have a minimum of 2–3 questions per tier (junior, mid_level, senior)
- [ ] Interview question text contains zero chapter numbers, module names, or file paths
- [ ] All academic citations include author, year, exact title, and arXiv/DOI link
- [ ] No fabricated model names, version numbers, API parameters, or statistics
- [ ] Each lesson is completable in ≤ 30 minutes (≤ ~1,500 words before an exercise)
- [ ] Python notebooks include the Colab launch badge immediately after the title cell
- [ ] metadata.json has every lesson registered exactly once, with correct `modes` entries
- [ ] course-repo registration JSON has all 8 required fields with no placeholder text

---

**Begin with Phase 1. Output the full course outline and complete metadata.json. Then stop and wait for me to type "proceed".**

— END PROMPT —
