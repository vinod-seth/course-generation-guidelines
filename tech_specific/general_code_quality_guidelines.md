# Technical Guideline: General Code Quality & standards

This guideline outlines language-agnostic requirements for code snippets, error handling, security, logging, and modular structure in generated courses. Adhering to these rules ensures that code examples are production-ready, readable, and secure.

---

## 1. Secure Key & Secret Management

No code example or setup guide in any course should ever expose credentials or hardcode API keys.

### Rules:
- **Environment Variables**: Instruct students to load credentials from the system environment or standard configuration managers.
- **Use `.env` Files**: For local execution, show how to use `.env` files.
- **Environment Isolation**: Always add `.env` (and other environment secret files like `.pem`, `*.key`, `config.json`) to the standard `.gitignore` template shown in the course.
- **Never Hardcode Secrets**: Do not use placeholder strings like `"YOUR_API_KEY_HERE"` directly in the main code block. Instead, write code that reads from environment variables, throwing an explicit error if the key is missing.

*Example:*
```
# Good Practice: Checked at startup
API_KEY = get_env_variable("API_KEY")
if not API_KEY:
    raise ConfigurationError("API_KEY environment variable is not set")
```

---

## 2. Robust Error Handling

Do not show "quick-and-dirty" code blocks that crash on network failure, invalid responses, or unexpected inputs.

### Rules:
- **Catch Specific Exceptions**: Always catch targeted API or networking exceptions (e.g., Timeout, ConnectionReset, RateLimit) rather than using generic `catch-all` blocks.
- **Graceful Degradation**: Show how the application should behave if a service is down (e.g., fallback models, retries, returning a clean error message).
- **Resources Cleanup**: Ensure file handles, database connections, and HTTP client sessions are properly closed using language-specific idioms (e.g., `using` statements, `try-with-resources`, or `finally` blocks).

---

## 3. Production-Ready Logging

Avoid using simple stdout print statements (like `print()`, `console.log()`, `System.out.println()`) for system status or error reporting in production-like examples.

### Rules:
- **Use Logging Libraries**: Demonstrate standard system logging levels (`DEBUG`, `INFO`, `WARNING`, `ERROR`).
- **Structured Log Messages**: Include relevant metadata (e.g., operation ID, execution time) when explaining complex agent actions or api pipeline transitions.
- **Sanitize Logs**: Ensure no sensitive variables (API keys, user passwords, PII) are printed to the logs.

---

## 4. Modular Code Structure

Explain code through modular, reusable design rather than monolithic script files.

### Rules:
- **Single Responsibility Principle**: Break down complex pipelines into small, named functions with explicit return statements.
- **Type Safety**: Use static types, type hints, or interfaces where supported by the language.
- **Self-Documenting Code**: Code should have clear variable naming conventions, and docstrings explaining complex or non-obvious configurations (such as model hyperparameters or custom prompt tags).
