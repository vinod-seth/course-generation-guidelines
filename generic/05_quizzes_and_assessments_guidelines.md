# Course Generation Guideline: Quizzes & Assessments

This guideline details the structural, numerical volume, and syntax requirements for creating interactive concept checks, chapter quizzes, comprehensive final assessments, and interview test suites across all course repositories. Following these formats enables autonomous course generators and review agents to validate course completeness.

---

## 1. Chapter/Module Question Volume Mandate (Minimum 20 Questions)

Every generated module or chapter in a course MUST contain **at least 20 questions** distributed across interactive concept checks, chapter quizzes, and practice exercises.

### Distribution Requirements per Chapter:
- **Lesson Concept Checks**: 2 to 4 interactive GFM checkbox questions per individual lesson.
- **End-of-Chapter Quiz Bank**: Comprehensive practice set bringing the total question count for the chapter/module to **at least 20 distinct questions**.
- **Question Types**: Questions must cover conceptual understanding, code output prediction, debugging scenarios, and architecture trade-offs.

---

## 2. GFM Interactive Quiz Syntax

Concept checks and chapter quizzes must be written to support interactive rendering in the portal.

### Syntax Rules:
- **Section Heading**: Use `## 🟢 Concept Check` or `## 📝 Chapter Quiz`.
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

## 3. Click-to-Reveal Solutions

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

## 4. Question Variety & Pedagogy

Do not rely solely on simple factual multiple-choice questions. Quizzes should evaluate deeper comprehension:
- **Debugging Challenges**: Provide a snippet of broken code or prompt, and ask the student to identify the error or the fix.
- **Scenario Questions**: Present a problem (e.g. latency constraints) and ask the user to choose the appropriate mitigation strategy (e.g. prompt caching vs. model routing).
- **Reflection Prompts**: Include open-ended reflection prompts with expandable guidelines on how to think about the answer.

---

## 5. Mandatory Final Assessment & Capstone Rubrics

Every course MUST include a formal, cumulative **Final Assessment** and a practical **Capstone Project**.

### Requirements:
1. **Cumulative Final Assessment**: A dedicated comprehensive exam covering all modules in the course. Must evaluate synthesis of concepts across the entire curriculum.
2. **Capstone Project Rubric**: The capstone project instructions must include a **Self-Assessment Rubric** with measurable success criteria:
   - **Accuracy/Quality**: Expected behavior of the finalized system (e.g., correct JSON structure, grounding check results).
   - **Performance Benchmarks**: Feasible latency thresholds (e.g. initial token under 800ms) or model constraints.
   - **Cost Efficiency**: Guidance on prompt token count optimization (e.g., incorporating caching).
   - **Grading Scale**: A table detailing expectations for `Excellent (Pass)`, `Satisfactory`, and `Needs Improvement`.

---

## 6. Production-Grade Tier-1 Interview Test Suite Mandate

Every generated course MUST provide a production-grade, comprehensive **Interview Test Suite**. Every core technical lesson must include an `interview` mode mapping to a structured `.json` question bank, and the course root must include a dedicated **Comprehensive Course Interview Suite**.

### Interview Question JSON Schema & Rules:
1. **Experience-Tiered Divisions**: Questions must be categorized into `junior` (0-2y), `mid_level` (3-5y), and `senior` (6+y) experience buckets. Each tier MUST contain **multiple questions** (minimum 2-3 questions per tier).
2. **Clean & Authentic Question Wording**: Questions MUST be generic, professional interview questions focused purely on the technical subject matter. **NEVER** mention chapter numbers, module prefixes, or file names in the question text (e.g. do NOT write "Explain Chapter 02 Variables...").
3. **Complexity Classifications**: Each question must specify its complexity rating: `'Easy'`, `'Medium'`, `'Hard'`, or `'System Design'`.
4. **Target Company Tags**: Tag questions based on top-tier company interview loops: `'Google'`, `'Meta'`, `'OpenAI'`, `'Anthropic'`, or `'General'`.
5. **Candidate Preparation Guidance**: Provide a high-level `preparation_guide` instructing the candidate on how to approach the answer, along with `star_framework_tip` structuring advice.
6. **Production-Grade Explanations & Pitfalls**: Provide in-depth explanations with code examples, list `common_pitfalls` ("what candidates get wrong"), and attach official documentation/paper `references`.

### Schema Example:
```json
{
  "lesson_title": "SLM Optimization",
  "experience_levels": {
    "senior": [
      {
        "id": "q1",
        "question": "How do you mitigate memory bottlenecks when serving a quantized 3B SLM under high concurrency?",
        "complexity": "System Design",
        "companies": ["Google", "OpenAI"],
        "core_intent": "Evaluates knowledge of vLLM, PagedAttention, and KV-cache management.",
        "preparation_guide": "Focus on memory allocation during continuous batching and KV-cache paging.",
        "explanation": "To achieve high concurrency, standard KV-cache allocations cause fragmentation...",
        "star_framework_tip": "Outline the problem (fragmentation), explain PagedAttention, and detail latency metrics.",
        "common_pitfalls": ["Confusing model weights memory with dynamic KV-cache memory"],
        "references": [
          { "title": "vLLM PagedAttention Paper", "url": "https://arxiv.org/abs/2309.06180" }
        ]
      }
    ]
  }
}
```
