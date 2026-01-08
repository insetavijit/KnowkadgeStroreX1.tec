| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.6.7.1 Common Parsing Errors]]**               | Identify typical failures                    | JSONDecodeError, ValidationError, format mismatches                             | Common errors include JSON decode and validation failures.          |
| **[[LC1.6.7.2 OutputParserException]]**               | Handle parser exceptions                     | OutputParserException class, error messages, exception handling                 | Catch OutputParserException for parsing failures.                   |
| **[[LC1.6.7.3 Debugging Parse Failures]]**            | Diagnose parsing issues                      | Raw output inspection, prompt review, format verification                       | Debug by inspecting raw LLM output and prompts.                     |
| **[[LC1.6.7.4 Logging Parser Activity]]**             | Track parsing operations                     | Logging setup, parse attempts, success/failure tracking                         | Log parsing attempts for debugging and monitoring.                  |
| **[[LC1.6.7.5 Graceful Degradation]]**                | Fail gracefully                              | Fallback values, partial success, user feedback                                 | Implement graceful degradation when parsing fails.                  |

# Error Handling: Self-Correcting Chains

In Distributed Systems, "Transient Failures" are expected.
In AI Systems, "Semantic Failures" (The model misunderstood the instructions) are also expected.

LangChain provides architectural components to **Auto-Heal** these breakages without crashing the application.

---

## 1. The `OutputFixingParser` (The Auto-Corrector)

If `JsonOutputParser` raises a `JSONDecodeError`, don't crash.
Instead, use another LLM call to fix the mistake.

**The Logic**:
1.  **Catch** the invalid string.
2.  **Prompt** the "Fixer Model": "I have a string that caused a JSON error: [STRING]. Please fix the syntax."
3.  **Return** the fixed object.

```python
from langchain.output_parsers import OutputFixingParser

# 1. Define the Strict Parser
base_parser = PydanticOutputParser(pydantic_object=Actor)

# 2. Wrap it in the Fixer
fixer_parser = OutputFixingParser.from_llm(
    parser=base_parser,
    llm=ChatOpenAI(model="gpt-3.5-turbo") # Use a cheap model for fixing
)

chain = prompt | model | fixer_parser
```

**Cost Warning**: This doubles your token usage on error (Original + Fix).

---

## 2. The `RetryOutputParser` (The Do-Over)

Sometimes fixing the string isn't enough (e.g., the answer is factually wrong or missing fields completely).
You need to **Retry the Generation**.

`RetryOutputParser` captures the original prompt, the bad output, and the error, and feeds them *all* back to the model.

> "You tried to answer X, but you said Y, which caused Error Z. Please try again."

```python
from langchain.output_parsers import RetryOutputParser

retry_parser = RetryOutputParser.from_llm(
    parser=base_parser,
    llm=ChatOpenAI()
)

# Architectural Requirement: The Retry Parser needs the Original Prompt!
chain = (
    RunnableParallel(
        completion=prompt | model, # The first attempt
        prompt_value=prompt        # Pass the prompt through
    ) 
    | retry_parser
)
```

---

## 3. Exception Hierarchy

When writing `try/except` blocks, know your enemy.

*   `OutputParserException`: The base class for all parsing errors.
*   `ValueError`: Often raised by Pydantic internal validation.

```python
try:
    result = chain.invoke("...")
except OutputParserException as e:
    # Access the raw output that caused the crash
    print(f"Failed to parse: {e.llm_output}")
    # Fallback logic
    return None
```

---

## Quick Reference

| Component | Strategy | Cost | Relies on |
| :--- | :--- | :--- | :--- |
| **OutputFixingParser** | "Fix this JSON string" | 2x (Small Prompt) | Syntax being repairable. |
| **RetryOutputParser** | "Try the whole task again" | 2x (Full Prompt) | Prompt logic being retriable. |
| **Circuit Breaker** | "Stop everything" | 1x | Application Logic. |
