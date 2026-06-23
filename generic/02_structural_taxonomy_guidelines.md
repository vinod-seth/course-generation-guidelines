# Course Generation Guideline: Structural Taxonomy & Organization

This guideline defines how courses must be structured, categorized, organized, and paced based on their tech stack and target domain. Adhering to this structure ensures that the generated courses are easy to navigate and logically sequenced.

---

## 1. Course Directory Hierarchy

The autonomous generator must organize course files according to a strict folder taxonomy:

```
[course-repo-root]/
├── README.md               # Main course entrypoint and syllabus
├── metadata.json           # Global course metadata (title, domain, etc.)
├── CHANGELOG.md            # Versioning and updates log
├── modules/
│   ├── 01_introduction/    # Module folder (prefixed with 2-digit index)
│   │   ├── README.md       # Module summary and goals
│   │   ├── lesson1.md      # Individual lesson file
│   │   └── lesson2.md
│   └── 02_advanced_topics/
│       ├── README.md
│       └── lesson1.md
└── assets/                 # Shared images, diagrams, or datasets
```

---

## 2. Document & Lesson Structure

Every individual lesson markdown file must adhere to the following sequence of sections:

1. **Title**: `# ` header with lesson name.
2. **Metadata Table**: Short, standardized table detailing prerequisites, reading time, and domain tag.
3. **📍 Lesson Roadmap**: Blockquote mapping sections to target audiences (for mixed courses).
4. **Learning Objectives**: Bulleted list of what the learner will be able to do.
5. **Main Sections**: Alternating between conceptual explanations (`## 🟢 [Conceptual]`) and technical demonstrations (`## 🔷 [Technical]`).
6. **Hands-on Labs/Exercises**: A concrete, guided practice task.
7. **Concept Check / Quiz**: Inline GFM checkbox quiz.
8. **Summary & Resources**: Key takeaways and external links.

---

## 3. Metadata and Taxonomy Fields

Each course must specify its categorization details in a root `metadata.json` file. The schema is:

- `course_title`: Clean title of the course.
- `domain`: High-level category (e.g., `Software Engineering`, `Generative AI`, `Cloud Infrastructure`, `Security`).
- `tech_stack`: List of primary technologies used (e.g., `["Python", "FastAPI", "Google GenAI SDK"]`).
- `difficulty`: One of `Beginner`, `Intermediate`, `Advanced`.
- `prerequisites`: List of required courses or skills.
- `estimated_hours`: Total time required for course completion.

---

## 4. Domain-Specific Pacing & Layouts

Ensure pacing matches the technical domain:

### A. GenAI & Prompt Engineering Courses
- Must include a roadmap of models being used (e.g. Gemini 2.5 Flash, Claude 3.5 Sonnet).
- Pacing: Concepts should immediately lead to API experiments (e.g., within the first 10 minutes of reading).

### B. Software Engineering & Systems Courses
- Must establish environment layout and directory hierarchy early.
- Code blocks must contain modular files matching a real project architecture, rather than single-script snippets.

### C. DevOps, Security, & Cloud Courses
- Must include architecture diagrams (rendered via Mermaid JS).
- Pacing: Emphasis on configuration validation (e.g., checking terraform plans, evaluating log policies).
