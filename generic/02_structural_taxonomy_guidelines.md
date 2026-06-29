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

## 3. Metadata and Taxonomy Fields & Curriculum Manifest

Each course must specify its categorization details and full curriculum manifest in a root `metadata.json` file. The schema is:

```json
{
  "title": "Course Title Here",
  "domain": "Generative AI",
  "tech_stack": ["Python", "Hugging Face", "PyTorch"],
  "difficulty": "beginner",
  "prerequisites": ["Basic Python"],
  "estimated_hours": 10,
  "modules": 7,
  "lessons": 18,
  "version": "1.1",
  "curriculum": [
    {
      "module_id": "module_01",
      "title": "Module 1: Title",
      "lessons": [
        {
          "id": "m1_l1",
          "title": "Lesson 1 Title",
          "defaultMode": "mdx",
          "modes": {
            "mdx": "tutorial/01_module/01_lesson.md",
            "notebook": "tutorial/01_module/01_lesson.ipynb"
          }
        }
      ]
    }
  ]
}
```

### Key Requirements for Curriculum Manifest & Multi-Format Modes:
1. **Single Logical Lesson Entity**: In `metadata.json`, each lesson must be registered once under the `lessons` array. Never create duplicate lesson entries for different format representations.
2. **Multi-Format Mode Pairings**: When a lesson provides both static reading content (Markdown `.md`/`.mdx`) and interactive code (Jupyter Notebook `.ipynb`), they must be mapped under the `modes` dictionary object.
3. **Default Mode Specification**: Define `defaultMode` (typically `"mdx"`) for every lesson to instruct learning portals on which format view to display by default.

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
