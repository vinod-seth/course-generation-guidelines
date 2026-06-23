# Course Generation Guideline: Quizzes & Assessments

This guideline details the structural and syntax requirements for creating interactive concept checks, chapter quizzes, and final capstone project assessments. Following these formats enables the learning platform to parse and render assessments correctly.

---

## 1. GFM Interactive Quiz Syntax

Concept checks must be written at the end of each lesson to support interactive rendering in the portal.

### Syntax Rules:
- **Section Heading**: Use `## 🟢 Concept Check` or `## Concept Check`.
- **Question Format**: State the question in plain text, followed by options.
- **GFM Checkboxes**: Use checkbox syntax for answer options:
  - Correct answer option: `* [x] [Option Text]`
  - Incorrect/distractor option: `* [ ] [Option Text]`
- **No static bullets**: Do not use standard bullets (`*`) or numbers (`1.`) for choices, as the parser will not render them interactively.

### Example:
```markdown
## 🟢 Concept Check

What is the correct way to initialize the modern Google GenAI SDK client in Python?

* [ ] `import google.generativeai as genai; genai.configure()`
* [x] `from google import genai; client = genai.Client()`
* [ ] `from google.genai import client; client.init()`
```

---

## 2. Click-to-Reveal Solutions

To prevent spoiling answers immediately, detailed explanations must be wrapped in HTML details blocks.

### Details block requirements:
- **Wrapper**: Place the answers and explanations inside `<details>` and `</details>` tags.
- **Summary Tag**: The summary line must start with the key emoji: `<summary>🔑 Click to Reveal Answer & Explanation</summary>`.
- **Spacing**: Insert a blank line between the `<summary>` line, the markdown content, and the closing `</details>` tag. This ensures the markdown engine renders the inner block correctly.

### Example:
```html
<details>
<summary>🔑 Click to Reveal Answer & Explanation</summary>

**Correct Answer:** Option B.

**Explanation:**
The new Google GenAI SDK uses the `google` root package namespace and instantiates clients via `genai.Client()`. Option A is the legacy SDK.
</details>
```

---

## 3. Question Variety & Pedagogy

Do not rely solely on simple factual multiple-choice questions. Quizzes should evaluate deeper comprehension:
- **Debugging Challenges**: Provide a snippet of broken code or prompt, and ask the student to identify the error or the fix.
- **Scenario Questions**: Present a problem (e.g. latency constraints) and ask the user to choose the appropriate mitigation strategy (e.g. prompt caching vs. model routing).
- **Reflection Prompts**: Include open-ended reflection prompts with expandable guidelines on how to think about the answer.

---

## 4. Capstone Project Rubrics

Every course must end with a comprehensive Capstone Project or final lab. The capstone instructions must include a **Self-Assessment Rubric** with measurable success criteria:

- **Accuracy/Quality**: Expected behavior of the finalized system (e.g., correct JSON structure, grounding check results).
- **Performance Benchmarks**: Feasible latency thresholds (e.g. initial token under 800ms) or model constraints.
- **Cost Efficiency**: Guidance on prompt token count optimization (e.g., incorporating caching).
- **Grading Scale**: A table detailing expectations for `Excellent (Pass)`, `Satisfactory`, and `Needs Improvement`.
