# Technical Guideline: Java Standards

This guideline defines Java-specific environment setup, project taxonomy, coding conventions, and SDK usage guidelines for generated courses.

---

## 1. Zero-Friction Environment Setup

Every Java-based course must teach standard package setups, directory structures, and build automation configurations.

### Setup Checklist:
- **Java Version**: Recommend JDK 17 or JDK 21 (LTS).
- **Project Structure**: Follow the Maven/Gradle standard directory layout:
  ```
  [project-root]/
  ├── pom.xml (or build.gradle)
  └── src/
      ├── main/
      │   ├── java/         # Source code (.java files)
      │   └── resources/    # Configs, .env, templates
      └── test/
          └── java/         # Test suites (JUnit 5)
  ```
- **Build Configurations**: Provide clean configuration snippets for dependencies.
  * *Maven dependency example:*
    ```xml
    <dependency>
        <groupId>dev.langchain4j</groupId>
        <artifactId>langchain4j-open-ai</artifactId>
        <version>0.27.1</version>
    </dependency>
    ```

---

## 2. Coding Conventions & Syntax

Follow clean, idiomatic Java rules:
- **Naming Conventions**: Use `camelCase` for variables and methods, `PascalCase` for classes and interfaces, and `UPPER_SNAKE_CASE` for constants.
- **Resource Management**: Always wrap AutoCloseable resources (e.g., file streams, HTTP client connections) in `try-with-resources` statements to prevent resource leaks.
- **Builder Pattern**: Utilize Builder patterns where available (common in modern Java clients).
- **Strong Typing**: Use explicit type signatures, interfaces, and generic collections. Avoid using raw types.

---

## 3. SDK Integration Patterns

All Java code examples should use modern libraries and configurations.

### A. Google GenAI / Vertex AI SDK (with LangChain4j or Official Client)
- **Framework**: Recommend `LangChain4j` or the modern `google-cloud-vertexai` SDK.
- **Initialization**: Show instantiation using builder patterns.

*Example (Vertex AI with LangChain4j):*
```java
import dev.langchain4j.model.chat.ChatLanguageModel;
import dev.langchain4j.model.google.VertexAiGeminiChatModel;

public class GeminiExample {
    public static void main(String[] args) {
        // Authenticates automatically using GOOGLE_APPLICATION_CREDENTIALS
        ChatLanguageModel model = VertexAiGeminiChatModel.builder()
                .project("my-gcp-project")
                .location("us-central1")
                .modelName("gemini-2.5-flash")
                .build();

        String response = model.generate("Explain quantum computing in one sentence.");
        System.out.println(response);
    }
}
```

### B. OpenAI Java SDK (with LangChain4j)
- **Instantiation**: Use builders to supply api keys and timeouts.

*Example:*
```java
import dev.langchain4j.model.chat.ChatLanguageModel;
import dev.langchain4j.model.openai.OpenAiChatModel;

public class OpenAIExample {
    public static void main(String[] args) {
        ChatLanguageModel model = OpenAiChatModel.builder()
                .apiKey(System.getenv("OPENAI_API_KEY"))
                .modelName("gpt-4o-mini")
                .build();

        String response = model.generate("Hello, how are you?");
        System.out.println(response);
    }
}
```
