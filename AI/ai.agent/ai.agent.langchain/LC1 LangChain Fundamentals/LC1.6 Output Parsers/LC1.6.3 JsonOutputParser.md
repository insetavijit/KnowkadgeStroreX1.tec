| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.6.3.1 Parsing JSON from LLM Output]]**        | Extract JSON data                            | JsonOutputParser class, dict output, structured data                            | JsonOutputParser extracts JSON from LLM responses.                  |
| **[[LC1.6.3.2 JSON Formatting Instructions]]**        | Guide LLM to produce JSON                    | Format instructions, example outputs, schema hints                              | Include format instructions to guide JSON output.                   |
| **[[LC1.6.3.3 Handling Malformed JSON]]**             | Deal with parsing failures                   | JSON errors, partial parsing, recovery strategies                               | Handle JSONDecodeError when LLM produces invalid JSON.              |
| **[[LC1.6.3.4 JSON Extraction Patterns]]**            | Apply common extraction methods              | Code block extraction, JSON finding, cleanup patterns                           | Extract JSON from markdown code blocks or mixed text.               |
| **[[LC1.6.3.5 Nested JSON Structures]]**              | Handle complex JSON                          | Nested objects, arrays, deep structures, path access                            | JsonOutputParser handles nested structures automatically.           |

# JsonOutputParser: The Structure Bridge

Before "Function Calling" existed, the only way to get structured data was to beg the model:
> "Please output valid JSON..."

`JsonOutputParser` is the legacy, yet still useful, tool for this pattern.
It performs two jobs:
1.  **Prompting**: It tells the model to output JSON (via `format_instructions`).
2.  **Repairing**: It strips Markdown backticks (\`\`\`json) before calling `json.loads`.

---

## 1. The Partial Streaming Miracle

The biggest architectural reason to use `JsonOutputParser` is **Streaming UI Updates**.

Standard `json.loads(string)` fails if the string is incomplete.
`{"name": "Alice", "age":` <- **Error**.

`JsonOutputParser` supports **Partial Parsing**. It reconstructs the JSON object *as it arrives*.

```python
chain = model | JsonOutputParser()

# Model outputs: '{"name":'
# Parser emits: {}

# Model outputs: ' "Alice",'
# Parser emits: {"name": "Alice"}

# Model outputs: ' "age": 30}'
# Parser emits: {"name": "Alice", "age": 30}
```

**Use Case**:
Showing a "filling out form" animation in your UI while the model is still thinking about the last field.

---

## 2. Using Pydantic for Validation

You can provide a Pydantic model to `JsonOutputParser` to get the `input_schema` benefits, but *it typically outputs a Dict, not a Pydantic Object*.
(Use `PydanticOutputParser` if you want the actual Object).

```python
from langchain_core.pydantic_v1 import BaseModel, Field

class Joke(BaseModel):
    setup: str = Field(description="question to set up a joke")
    punchline: str = Field(description="answer to resolve the joke")

parser = JsonOutputParser(pydantic_object=Joke)

chain = prompt | model | parser
```

**Architectural Note**:
This does NOT force the model to output this schema at the API level (like OpenAI JSON Mode). It only provides the `format_instructions` text to insert into the prompt. It is a "Soft Constraint".

---

## 3. The "Markdown Trap"

LLMs love to wrap JSON in markdown:
\`\`\`json
{"foo": "bar"}
\`\`\`

`JsonOutputParser` automatically detects and strips these backticks.
However, if the model outputs text *before* the JSON ("Sure, here is the JSON:"), the parser might fail or return just the JSON part depending on its strictness settings.

---

## Quick Reference

| Feature | Details |
| :--- | :--- |
| **Output Type** | `dict` (Standard Python Dictionary). |
| **Streaming** | ✅ Yes (Partial JSON reconstruction). |
| **Reliability** | ⚠️ Medium (Depends on Prompt Engineering). |
| **Best For** | Open-Source models that don't support Tool Calling. |
