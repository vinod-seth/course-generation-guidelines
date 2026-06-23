# Course Generation Guideline: Originality & Attribution

This guideline ensures that all generated courses are strictly original, legally compliant, and appropriately cited. It directs the autonomous course generation system to produce unique learning material and avoid plagiarism.

---

## 1. Core Principles

1. **Zero Plagiarism**: No verbatim copying of official documentation, competitor guides, books, blog posts, or public repositories.
2. **Fresh Prose & Explanations**: Concepts must be described in custom, newly generated terminology and structural frameworks.
3. **Unique Scenarios**: Avoid cliché, generic, or copied business scenarios/examples.
4. **Transparent Sourcing**: Any external concept, model, framework, or paper must be explicitly cited with original authors and links.

---

## 2. Preventing Duplication in Examples & Code

To ensure examples and code snippets are genuinely unique:
- **Custom Personas & Companies**: Do not use generic placeholders like "Alice/Bob" or "Acme Corp" repeatedly unless they are part of a distinct, course-specific context. Generate unique corporate settings, user scenarios, and problem definitions.
- **Tailored Code Snippets**: Avoid copying cookbook examples or standard documentation snippets. All code should:
  - Use custom variable names, comments, and structure.
  - Match the exact narrative of the course.
  - Avoid identical logic flow to publicly available repositories (e.g. OpenAI Cookbooks, Anthropic API examples).
- **Multi-Provider Comparisons**: When comparing APIs (e.g., OpenAI vs. Anthropic vs. Google GenAI), write structurally unique comparisons. Do not replicate standard table structures found in common developer articles.

---

## 3. Academic Citation Standards

When mentioning any research-based or foundational technique, the generator **must** include proper citation.

### Citation Checklist:
- **Concept & Authors**: Mention the core concept along with the primary authors and publication year.
- **Paper Title**: Include the exact paper title in italicized text.
- **Link**: Provide a working link to the publication (arXiv page, DOI link, or conference proceeding).
- **Zero Hallucination**: Do not fabricate academic citations, paper names, or author contributions ("ghost citations").

### Required Citations for Common Topics:
- **Chain-of-Thought**: Wei et al. (2022) - *Chain-of-Thought Prompting Elicits Reasoning in Large Language Models* (https://arxiv.org/abs/2201.11903)
- **Few-Shot Learning**: Brown et al. (2020) - *Language Models are Few-Shot Learners* (https://arxiv.org/abs/2005.14165)
- **Tree of Thoughts**: Yao et al. (2023) - *Tree of Thoughts: Deliberate Problem Solving with Large Language Models* (https://arxiv.org/abs/2305.10601)
- **Lost in the Middle**: Liu et al. (2023) - *Lost in the Middle: How Language Models Use Long Contexts* (https://arxiv.org/abs/2307.03172)
- **Self-Consistency**: Wang et al. (2022) - *Self-Consistency Improves Chain of Thought Reasoning in Language Models* (https://arxiv.org/abs/2203.11171)
- **ReAct (Reason and Act)**: Yao et al. (2022) - *ReAct: Synergizing Reasoning and Acting in Language Models* (https://arxiv.org/abs/2210.03629)

---

## 4. Referencing External Sources

If the course uses external datasets, third-party libraries, or open-source projects:
- **Attribution Block**: Provide a clear "References & Credits" section at the end of the lesson.
- **Permissive Licenses Only**: Ensure any referenced tool/library is open-source (e.g., MIT, Apache 2.0, BSD). Do not recommend proprietary or restrictive-license dependencies without explicit licensing notices.
- **Fair Use Limits**: Limit any quoted prose or official API schema listings to short, educational snippets, rewriting description details in the course's own voice.
