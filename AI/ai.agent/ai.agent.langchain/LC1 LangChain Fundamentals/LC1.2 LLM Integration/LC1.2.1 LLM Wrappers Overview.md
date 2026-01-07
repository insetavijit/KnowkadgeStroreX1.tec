| **Subtopic**                                          | **Focus & Purpose**                         | **Key Concepts / Details**                                                     | **One-Line Recall**                                                |
| ----------------------------------------------------- | ------------------------------------------- | ------------------------------------------------------------------------------ | ------------------------------------------------------------------ |
| **[[LC1.2.1.1 What LLM Wrappers Provide]]**           | Understand wrapper benefits                 | Unified API, provider abstraction, common interface methods                    | LLM wrappers provide a unified interface across providers.         |
| **[[LC1.2.1.2 Abstraction Over Provider APIs]]**      | Hide provider-specific details              | Consistent method signatures, error normalization, response formatting         | Wrappers abstract away provider-specific API differences.          |
| **[[LC1.2.1.3 Uniform Interface Design]]**            | Learn common wrapper methods                | invoke(), stream(), batch(), ainvoke(), common parameters                      | All LLM wrappers share the same core interface methods.            |
| **[[LC1.2.1.4 Wrapper Design Patterns]]**             | Understand implementation patterns          | Adapter pattern, inheritance hierarchy, mixin usage                            | Wrappers follow adapter and inheritance patterns.                  |
| **[[LC1.2.1.5 Extending Wrappers]]**                  | Create custom LLM wrappers                  | Subclassing BaseLLM, implementing required methods, custom integrations        | Extend base classes to create custom LLM wrappers.                 |

# LLM Wrappers: The Universal Adapter

In software engineering, this is known as the **Adapter Pattern**.
Every Model Provider (OpenAI, Anthropic, Google, Cohere) has a completely different API signature.
*   OpenAI uses `messages=[{"role": "user"}]`.
*   Anthropic uses `system="..."` top-level parameters + `messages`.
*   HuggingFace might use raw string inputs.

LangChain Wrappers (`BaseChatModel`) normalize this chaos into a single, predictable interface.

---

## 1. The Unified Interface (Runnable Protocol)

Regardless of whether the model is running on a server in San Francisco (OpenAI) or locally on your laptop (Ollama), the command to use it is **identical**.

```python
# The "Interface" Contract
response = model.invoke("Hello, world!")
```

This uniformity extends to all execution modes:

| Method | Role | Critical Use Case |
| :--- | :--- | :--- |
| **.invoke()** | Synchronous 1-to-1 | Scripts, testing, simple tools. |
| **.stream()** | Yields token-by-token | Creating perceived speed (Typing effect). |
| **.batch()** | Parallel processing | Categorizing 1,000 rows only 10x faster. |
| **.ainvoke()** | Async (Non-blocking) | Web servers (FastAPI) handling 10k users. |

> **Architectural Win**: You can switch your entire backend from Synchronous to Asynchronous just by adding the letter `a` (`invoke` -> `ainvoke`). You don't need to rewrite your logic using `asyncio` loops manually.

---

## 2. Standardized Inputs & Outputs

Wrappers don't just send text; they **normalize** the data structures.

### Standardized Input
Instead of learning 5 different prompt formats, you use one: **List of Messages**.
*   `SystemMessage`: "You are a helpful assistant."
*   `HumanMessage`: "What is 2+2?"
*   `AIMessage`: "4."

The Wrapper is responsible for translating this list into the specific JSON format the provider demands.

### Standardized Output
Raw APIs return messy JSON blobs. LangChain returns an `AIMessage` object.
*   `.content`: The actual text string.
*   `.response_metadata`: The raw provider info (usage tokens, finish reasons).

```python
# It doesn't matter if it's GPT-4 or Claude 3
print(response.content) # Always works
print(response.response_metadata['token_usage']) # Standardized access
```

---

## 3. Configuration Injection (Runtime Binding)

Wrappers are not static. You can inject runtime configuration without instantiating a new class. This is used heavily for **Model Routing**.

### The `.bind()` Pattern
You can "attach" parameters to a model call.

```python
# Create a specialized version of the model that behaves differently
json_model = model.bind(response_format={"type": "json_object"})

# Now this specific object always forces JSON output
json_model.invoke("List 5 cities")
```

This allows you to create "Micro-Models" from a single base model.
*   `writer_model` (Temperature 0.9)
*   `coder_model` (Temperature 0.0)
*   `json_model` (JSON output)

---

## 4. Why Not Just Request?

"I can just use `requests.post`!"
Yes, you can. But then you own the maintenance of:
1.  **Retries**: Handling 429 Rate Limits with exponential backoff.
2.  **Timeouts**: Handling hanging connections.
3.  **Auth**: Rotating API keys securely.

LangChain wrappers handle these **Resiliency Concerns** internally.

---

## Quick Reference

| Feature | Description |
| :--- | :--- |
| **Normalization** | `SystemMessage` in LangChain maps to `system` (Claude) or `messages[0]` (OpenAI). |
| **Polymorphism** | All models look the same to the application logic. |
| **Async** | Native support for `async/await` without boilerplate. |
| **Resiliency** | Built-in retry logic for rate limits. |
