| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.3.1.1 Creating PromptTemplate]]**             | Initialize basic prompt templates            | PromptTemplate class, template string, from_template() method                   | Use PromptTemplate.from_template() for simple prompts.              |
| **[[LC1.3.1.2 Input Variables]]**                     | Define dynamic placeholders                  | input_variables list, {variable} syntax, variable naming                        | Declare input_variables for all placeholders in template.           |
| **[[LC1.3.1.3 Template Syntax]]**                     | Understand formatting options                | f-string style {}, jinja2 templates, escaping braces                            | Use {variable} syntax for placeholder substitution.                 |
| **[[LC1.3.1.4 Format Method]]**                       | Generate final prompt strings                | format(), invoke(), passing variable values                                     | Call format() or invoke() to fill template variables.               |
| **[[LC1.3.1.5 Basic Prompt Construction]]**           | Build effective simple prompts               | Instruction patterns, context inclusion, clear formatting                       | Structure prompts with clear instructions and context.              |

# PromptTemplate Basics: The Cognitive Schema

A prompt is not a string. It is a **Function** that takes structured input and returns a string.
Treating prompts as "Magic Strings" scattered throughout your code is the root cause of unmaintainable AI applications.

The `PromptTemplate` object is a **Schema Definition** for the cognitive task.

---

## 1. The Anatomy of a Template

A production prompt has two distinct parts:
1.  **Static Protocol**: The invariant instructions (The "Code").
2.  **Dynamic Context**: The variable user input (The "Data").

LangChain enforces this separation using Python's f-string syntax `{variable}` within a reusable class.

```python
from langchain_core.prompts import PromptTemplate

# Define the Schema
template = PromptTemplate.from_template(
    "Translate the following text from {source_lang} to {target_lang}: {text}"
)

# Bind the Data (Late Binding)
prompt_value = template.invoke({
    "source_lang": "English",
    "target_lang": "French", 
    "text": "Hello World"
})
# Result: "Translate the following text from English to French: Hello World"
```

---

## 2. Safety: Why not just use f-strings?

"Why can't I just use `f'Translate {text}'`?"

1.  **Serialization**: You can save a `PromptTemplate` to a JSON/YAML file. You cannot save a compiled Python f-string.
2.  **Validation**: LangChain validates that all required variables are present **before** sending the request, preventing runtime API errors.
3.  **Partial Application**: You can "pre-fill" variables.

**Partial Application Example**:
Imagine a translation bot where the source language is always English.

```python
# Create a specialized template from a generic one
french_translator = template.partial(source_lang="English", target_lang="French")

# Now it only needs one argument
french_translator.invoke({"text": "Hello"})
```

---

## 3. Cognitive Optimization (CO)

Just as code is optimized for the compiler, prompts must be optimized for the LLM.

### The Standard Instruction Format
Do not write conversational sentences. Write explicit algorithms.

**Bad**:
`template = "Can you please help me find the errors in this code {code}?"`

**Good**:
```python
template = """
ROLE: Senior Python Linter

TASK: Analyze the provided code for syntax errors and logic flaws.

FORMAT: Output a JSON list of errors.

CODE:
{code}
"""
```

### The Delimiter Defense
When injecting user input, always surround it with delimiters (triple quotes, XML tags). This prevents **Prompt Injection**.
If the user inputs `Ignore previous instructions`, the delimiters help the model realize it is *data*, not *instruction*.

```python
# Safer pattern
template = "Summarize this text:\n'''\n{user_input}\n'''"
```

---

## 4. Templating Engines (Jinja2)

For complex logic (if/else statements inside the prompt), standard `{}` is not enough.
LangChain supports **Jinja2**.

*   *Scenario*: Only include the "History" section if the conversation is > 0 turns.

```python
pt = PromptTemplate.from_template(
    """
    You are a bot.
    {% if use_history %}
    Previous conversation: {history}
    {% endif %}
    Question: {question}
    """,
    template_format="jinja2"
)
```

---

## Quick Reference

| Method | Role | Example |
| :--- | :--- | :--- |
| **from_template()** | Fast creation | `PromptTemplate.from_template("Hello {name}")` |
| **.invoke(dict)** | Formatting | Returns a `StringPromptValue` (Wrapper). |
| **.format(dict)** | Raw String | Returns the plain string. |
| **.save("p.yaml")** | Storage | Serializes prompt to disk. |
