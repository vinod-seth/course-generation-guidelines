# Technical Guideline: Python Standards

This guideline defines python-specific environment setup, coding conventions, and SDK usage guidelines for generated courses.

---

## 1. Zero-Friction Environment Setup

Every Python-based course must instruct students on establishing an isolated environment and pinning versions.

### Setup Checklist:
- **Python Version**: Recommend Python 3.10 or newer.
- **Virtual Environment Setup**:
  * Windows: `python -m venv venv` and `venv\Scripts\activate`
  * macOS / Linux: `python -m venv venv` and `source venv/bin/activate`
- **Dependencies (`requirements.txt`)**: Pinned versions for all dependencies. 
  ```text
  google-genai==0.1.1
  openai==1.12.0
  anthropic==0.18.0
  python-dotenv==1.0.1
  ```

---

## 2. Coding Conventions & Syntax

Follow standard Python idioms and PEP 8 guidelines:
- **Type Hints**: Explicitly type function signatures to clarify input and return expectations.
- **Naming Conventions**: Use `snake_case` for variables and function names, `CamelCase` for classes, and `UPPER_CASE` for constants.
- **Context Managers**: Always use context managers (`with` statements) for file I/O or network connections to prevent resource leaks.

---

## 3. SDK Integration Patterns

All generative AI API examples must use the latest modern syntax.

### A. Google GenAI SDK
- **Installation**: `pip install google-genai`
- **Initialization**: `from google import genai` and `client = genai.Client()`
- **Methods**: Use `client.models.generate_content()` with `gemini-2.5-flash` or other modern models.

*Example:*
```python
import os
from google import genai
from google.genai import errors

# Automatic client authentication from GEMINI_API_KEY environment variable
client = genai.Client()

def get_summary(text: str) -> str:
    try:
        response = client.models.generate_content(
            model='gemini-2.5-flash',
            contents=f"Summarize this text: {text}"
        )
        return response.text
    except errors.APIError as e:
        print(f"Google GenAI API Error: {e}")
        raise
```

### B. OpenAI SDK
- **Initialization**: `from openai import OpenAI` and `client = OpenAI()`
- **Structured Outputs**: Use `client.beta.chat.completions.parse()` with Pydantic classes.

*Example:*
```python
from openai import OpenAI
from pydantic import BaseModel

client = OpenAI()

class Recipe(BaseModel):
    name: str
    ingredients: list[str]
    steps: list[str]

completion = client.beta.chat.completions.parse(
    model="gpt-4o-mini",
    messages=[
        {"role": "user", "content": "How do you make an omelette?"}
    ],
    response_format=Recipe,
)
recipe = completion.choices[0].message.parsed
```

### C. Anthropic SDK
- **Initialization**: `import anthropic` and `client = anthropic.Anthropic()`
- **Rules**: Specify system instructions as top-level parameters in the `messages.create()` call. Use XML tags (e.g. `<rules>`) to structure inputs.
