# Technical Guideline: JavaScript & TypeScript Standards

This guideline defines JavaScript/TypeScript-specific environment setup, coding conventions, and SDK usage guidelines for generated courses.

---

## 1. Zero-Friction Environment Setup

Every JavaScript-based course must guide students on configuring Node.js project scopes, runtime settings, and dependency pinning.

### Setup Checklist:
- **Node.js Version**: Recommend Node.js 18+ or 20+ (LTS).
- **Package Initialization**: Guide students to create a `package.json` with ESM module configuration (`"type": "module"`).
- **TypeScript (Recommended)**: If writing TypeScript, provide a minimal `tsconfig.json` configuration.
- **Dependencies (`package.json`)**: Pin package versions.
  ```json
  {
    "name": "course-example",
    "type": "module",
    "dependencies": {
      "@google/genai": "^0.1.1",
      "openai": "^4.26.0",
      "dotenv": "^16.4.1"
    },
    "devDependencies": {
      "typescript": "^5.3.3"
    }
  }
  ```
- **Lockfiles**: Instruct students to commit their `package-lock.json` or `pnpm-lock.yaml` to ensure build reproducibility.

---

## 2. Coding Conventions & Syntax

Follow idiomatic JavaScript standards:
- **Modern ES6+ Features**: Use `const` and `let` (never `var`), arrow functions, templates, and ES Modules (`import/export` instead of `require`).
- **Asynchronous Flow**: Standardize on `async/await` patterns with comprehensive `try/catch` wrapping rather than raw `.then()/.catch()` promise chains.
- **Naming Conventions**: Use `camelCase` for variables, function names, and file names (or `kebab-case` for files), and `PascalCase` for classes/interfaces.

---

## 3. SDK Integration Patterns

Ensure all API example code blocks use the latest Javascript/TypeScript client syntax.

### A. Google GenAI SDK
- **Installation**: `npm install @google/genai`
- **Import**: `import { GoogleGenAI } from '@google/genai';`
- **Instantiation**: `const ai = new GoogleGenAI();`
- **Method Call**: `ai.models.generateContent()` using `gemini-2.5-flash`.

*Example (ESM module / TypeScript):*
```typescript
import { GoogleGenAI } from '@google/genai';

// Authenticates automatically via process.env.GEMINI_API_KEY
const ai = new GoogleGenAI();

async function getSummary(text: string): Promise<string | null> {
  try {
    const response = await ai.models.generateContent({
      model: 'gemini-2.5-flash',
      contents: `Summarize this text: ${text}`
    });
    return response.text;
  } catch (error) {
    console.error('Google GenAI Error:', error);
    throw error;
  }
}
```

### B. OpenAI SDK
- **Initialization**: `import OpenAI from 'openai';` and `const openai = new OpenAI();`
- **Structured Outputs**: Demonstrate JSON structured responses using `response_format` schemas.

*Example:*
```javascript
import OpenAI from 'openai';

const openai = new OpenAI();

async function getStructuredOmeletteRecipe() {
  const completion = await openai.chat.completions.create({
    model: 'gpt-4o-mini',
    messages: [{ role: 'user', content: 'Provide an omelette recipe.' }],
    response_format: { type: 'json_object' }
  });
  return JSON.parse(completion.choices[0].message.content);
}
```
