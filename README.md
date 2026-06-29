# Course Generation Guidelines

This directory contains the core guideline markdown files used by the autonomous course generation application. These rules ensure that all generated courses are high-quality, properly structured, original, easy to understand, and contain interactive practical exercises and quizzes.

---

## Guidelines Index

Please refer to the separate guidelines below for specific areas of course generation:

1. **[01 Originality & Attribution Guidelines](file:///c:/vinod/course-generation-guidelines/generic/01_originality_and_attribution_guidelines.md)**
   - Methods to prevent duplicacy and plagiarism.
   - Creating custom example scenarios, company profiles, and unique code.
   - Enforcing academic citation rules (author name, paper title, arXiv link).

2. **[02 Structural Taxonomy & Organization Guidelines](file:///c:/vinod/course-generation-guidelines/generic/02_structural_taxonomy_guidelines.md)**
   - Establishing directories, taxonomy categories, and file schemas.
   - Pacing lessons based on technical depth.
   - Mapping out course and module prerequisites.

3. **[03 Pedagogical Clarity & Readability Guidelines](file:///c:/vinod/course-generation-guidelines/generic/03_pedagogical_clarity_guidelines.md)**
   - Designing with the **Dual-Track** system (🟢 Conceptual vs. 🔷 Technical).
   - Conversational tone and style guidelines.
   - Strictly banned LLM phrasing and transition blocklists.
   - Cognitive load limits per lesson.

4. **[General Code Quality & Standards](file:///c:/vinod/course-generation-guidelines/tech_specific/general_code_quality_guidelines.md)**
   - Secure key and secret management (.env files, no hardcoded API keys).
   - Robust error handling, exception boundaries, and resource cleanup.
   - Production-ready logging standards.

5. **Language-Specific Technical Guidelines**
   - **[Python Standards](file:///c:/vinod/course-generation-guidelines/tech_specific/python_guidelines.md)**: Virtual environments, PEP 8, and Python SDK examples.
   - **[JavaScript & TypeScript Standards](file:///c:/vinod/course-generation-guidelines/tech_specific/javascript_guidelines.md)**: Node.js setups, ESM modules, and async/await syntax.
   - **[Java Standards](file:///c:/vinod/course-generation-guidelines/tech_specific/java_guidelines.md)**: Maven/Gradle project structures and builders.
   - **[C Standards](file:///c:/vinod/course-generation-guidelines/tech_specific/c_guidelines.md)**: Makefiles, memory safety (`malloc`/`free`), and libcurl integration.

6. **[05 Quizzes & Assessments Guidelines](file:///c:/vinod/course-generation-guidelines/generic/05_quizzes_and_assessments_guidelines.md)**
   - Minimum volume mandate of at least 20 questions per chapter/module across quizzes and practice sets.
   - Markdown formatting for interactive checkbox quizzes and click-to-reveal explanation blocks.
   - Mandating formal final assessments and capstone project evaluation rubrics.
   - Production-grade tier-1 interview test suite requirements and JSON schemas.

---

## Integration with Reviewer Agents

These generation guidelines directly correspond to the criteria evaluated by the `course-reviewer` application. Generating courses that follow these rules will ensure that automated critiques, structural audits, and plagiarism runs succeed with a perfect score (5/5).
