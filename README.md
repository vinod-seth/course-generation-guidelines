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

4. **[04 Technical Term Glossary & Hover Definitions](file:///c:/vinod/course-generation-guidelines/generic/04_technical_term_glossary_guidelines.md)**
   - Wrapping load-bearing technical terms in `<abbr title="...">` so definitions appear on hover, tap, and focus.
   - Which terms qualify (and the density ceiling that keeps pages readable).
   - Rules for writing a tooltip-sized definition; renderer support requirements.

5. **[General Code Quality & Standards](file:///c:/vinod/course-generation-guidelines/tech_specific/general_code_quality_guidelines.md)**
   - Secure key and secret management (.env files, no hardcoded API keys).
   - Robust error handling, exception boundaries, and resource cleanup.
   - Production-ready logging standards.

6. **Language-Specific Technical Guidelines**
   - **[Python Standards](file:///c:/vinod/course-generation-guidelines/tech_specific/python_guidelines.md)**: Virtual environments, PEP 8, and Python SDK examples.
   - **[JavaScript & TypeScript Standards](file:///c:/vinod/course-generation-guidelines/tech_specific/javascript_guidelines.md)**: Node.js setups, ESM modules, and async/await syntax.
   - **[Java Standards](file:///c:/vinod/course-generation-guidelines/tech_specific/java_guidelines.md)**: Maven/Gradle project structures and builders.
   - **[C Standards](file:///c:/vinod/course-generation-guidelines/tech_specific/c_guidelines.md)**: Makefiles, memory safety (`malloc`/`free`), and libcurl integration.

7. **Resume-to-Offer Guidelines** (`interview_prep/`) — for the **candidate-specific, company-targeted** course archetype, whose syllabus is *derived* from a resume × a target company rather than authored in advance. These apply **in addition to** the generic guidelines above.
   - **[01 Pipeline & Chapter Structure](file:///c:/Autonomous-course-generation/course-generation-guidelines/interview_prep/01_resume_to_offer_pipeline_guidelines.md)**: the fixed generation order (Target Lock → Dossier → Audit → Tech Stack → Introduction → Gap Map → Round Prep → Readiness).
   - **[02 Company Dossier Sourcing](file:///c:/Autonomous-course-generation/course-generation-guidelines/interview_prep/02_company_dossier_guidelines.md)**: mandatory provenance tags for every process claim; no invented rounds, rubrics, or pass rates; no impersonating the company.
   - **[03 Resume Audit & Scoring](file:///c:/Autonomous-course-generation/course-generation-guidelines/interview_prep/03_resume_audit_and_scoring_guidelines.md)**: the auditable /100 rubrics (resume-intrinsic and company-relative), the Claim Vault, and how to deliver bad news.
   - **[04 Candidate Data & Privacy](file:///c:/Autonomous-course-generation/course-generation-guidelines/interview_prep/04_candidate_data_and_privacy_guidelines.md)**: PII exclusion, private-by-default repositories, anonymisation for reuse.
   - Archetype context: **[RESUME_TO_OFFER_ARCHETYPE.md](file:///c:/Autonomous-course-generation/course-creation-context/RESUME_TO_OFFER_ARCHETYPE.md)**

8. **[05 Quizzes & Assessments Guidelines](file:///c:/vinod/course-generation-guidelines/generic/05_quizzes_and_assessments_guidelines.md)**
   - Minimum volume mandate of at least 20 questions per chapter/module across quizzes and practice sets.
   - Markdown formatting for interactive checkbox quizzes and click-to-reveal explanation blocks.
   - Mandating formal final assessments and capstone project evaluation rubrics.
   - Production-grade tier-1 interview test suite requirements and JSON schemas.

---

## Integration with Reviewer Agents

These generation guidelines directly correspond to the criteria evaluated by the `course-reviewer` application. Generating courses that follow these rules will ensure that automated critiques, structural audits, and plagiarism runs succeed with a perfect score (5/5).
