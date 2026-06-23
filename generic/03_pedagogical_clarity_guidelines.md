# Course Generation Guideline: Pedagogical Clarity & Readability

This guideline governs the presentation style, tone, and cognitive load design of generated courses. Following these practices makes content approachable, engaging, and easy to understand for diverse learner groups.

---

## 1. The Dual-Track System

To accommodate both non-technical and technical learners simultaneously, courses covering mixed topics must separate conceptual content from technical implementations:

- **Core Concepts Track (🟢)**: Focusing on high-level architecture, design patterns, business impact, and general rules. Written in clear, non-jargon language.
- **Technical Deep-Dive Track (🔷)**: Focusing on SDK configurations, Python/JavaScript script code, CLI commands, and database queries.

### Visual Delineation:
- Secondary headers (`##`) and third-level headers (`###`) must start with either `🟢` or `🔷` to alert readers.
- If a lesson is designated as *Mixed-Audience*, a **Lesson Roadmap** table must be included at the very beginning of the lesson file (see [02_structural_taxonomy_guidelines.md](file:///c:/vinod/course-generation-guidelines/generic/02_structural_taxonomy_guidelines.md)).

---

## 2. Professional Tone & Language

The generated material must sound like it was written by an experienced human developer and technical educator. 

### Style Rules:
- **Active Voice**: Prefer active, direct verbs. (e.g., *"Configure the environment variable"* instead of *"The environment variable should be configured"*).
- **Concise Sentences**: Keep sentences under 25 words where possible to improve readability.
- **Developer Conversational**: Write in a friendly, peer-to-peer developer tone. Avoid overly formal academic structures, but do not use forced slang.

---

## 3. Strict LLM Phrasing Blocklist

Autonomous generators frequently introduce repetitive transition phrases. The following words/phrases are **strictly banned** and must be rewritten with direct human expressions:

| Banned LLM Phrase | Human Alternative |
|---|---|
| "Let's dive deep" / "Dive in" | "Let's review", "We will explore" |
| "Here's a hard truth" / "Deceptively simple" | *State the concept directly without hyperbole.* |
| "In today's rapidly evolving landscape" | *Omit completely, begin with the topic.* |
| "Before you can command..." / "Harness the power..." | *Use direct actions: "To initialize the model...", "To use..."* |
| "It's important to note that..." | *State the note directly.* |
| "Imagine this scenario..." | "Consider a case where..." |
| "Tapestry", "Delve", "Crucial", "Revolutionary" | *Use plain terms: structure, explore, important, significant.* |

---

## 4. Cognitive Load Management

Learners drop off when bombarded with too many new concepts before having a chance to apply them.
- **The 20-Minute Rule**: No more than 20 minutes of reading/conceptual material (approximately 1,200 words) should be presented without an interactive activity (e.g., a mini-exercise, quick code execution, or inline quiz).
- **Incremental Scaffolding**: Introduce a single concept, show its code implementation, test it, and then expand on it. Do not introduce five concepts at once and then provide a single massive code script.
- **Visual Breakouts**: Use note boxes or callouts strategically to highlight crucial points:
  ```markdown
  > [!NOTE]
  > Informational tip or secondary detail.
  
  > [!IMPORTANT]
  > Crucial setup or API requirement to prevent failure.
  ```
