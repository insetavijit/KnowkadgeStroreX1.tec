| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.6.6.1 Retry Parsing]]**                       | Retry on parse failure                       | RetryOutputParser, automatic retries, max attempts                              | RetryOutputParser retries parsing on failure.                       |
| **[[LC1.6.6.2 OutputFixingParser]]**                  | Fix malformed output                         | OutputFixingParser class, LLM-based fixing, error correction                    | OutputFixingParser uses LLM to fix parsing errors.                  |
| **[[LC1.6.6.3 Handling Partial Outputs]]**            | Deal with incomplete responses               | Partial parsing, stream handling, incremental validation                        | Handle partial outputs during streaming parsing.                    |
| **[[LC1.6.6.4 Fallback Strategies]]**                 | Define backup behavior                       | Default values, alternative parsers, graceful degradation                       | Define fallbacks when primary parsing fails.                        |
| **[[LC1.6.6.5 Robust Parsing Pipelines]]**            | Build resilient parsing                      | Multiple parser stages, validation layers, error recovery                       | Layer parsers for robust, resilient parsing pipelines.              |

# Parsing Strategies: Beyond JSON

JSON is the "Happy Path". But the real world is messy.
Sometimes you need to parse CSV, XML, Markdown lists, or unstructured blobs.

This file covers the **Heuristic Parsing Strategies** you need when Native Tool Calling is not an option.

---

## 1. The Regex Strategy (Extraction)

When an LLM refuses to output *just* the JSON and chatters ("Here is your data..."), `JsonOutputParser` usually fails.
The architectural fix is **Regex Extraction** *before* parsing.

```python
import re

def extract_json_block(text: str) -> str:
    # Look for ```json ... ```
    match = re.search(r"```json\n(.*?)\n```", text, re.DOTALL)
    if match:
        return match.group(1)
    return text

chain = model | extract_json_block | JsonOutputParser()
```

**Pattern**: The "Sanitizer Middleware". Always sanitize the raw string before handing it to a brittle parser.

---

## 2. The XML Strategy (Anthropic's Favorite)

Anthropic models (Claude) are fine-tuned on XML. They prefer `<tag>content</tag>` over JSON.
XML is notoriously robust for **Long Content Generation** (like writing a book chapter) because it has an explicit closing tag `</chapter>`.

```python
from langchain_core.output_parsers import XMLOutputParser

chain = prompt | model | XMLOutputParser()
# Output: {'root': [{'tag': 'content'}]}
```

**Architecture Tip**: If your prompt is massive (RAG with 50 pages), XML parsing often yields fewer syntax errors than JSON because JSON's closing braces `}}` are easy to lose count of.

---

## 3. The CSV Strategy (Lists)

If you just need a list of items, JSON is overkill (too many tokens for `[",",","]`).
Use a Comma Separated List parser.

```python
from langchain_core.output_parsers import CommaSeparatedListOutputParser

parser = CommaSeparatedListOutputParser()
# Prompt: "List 5 fruits. Output as CSV."
# Output: "apple, banana, cherry" -> ["apple", "banana", "cherry"]
```

---

## 4. The "Pandas" Strategy

Sometimes you want code, not data.
`PandasDataFrameOutputParser` helps generating Python code to manipulate dataframes.

**Security Warning**:
This parser essentially asks the LLM to write Python code.
**NEVER** `exec()` this code blindly in a production environment. Use a sandboxed environment (like `e2b` or Docker).

---

## Quick Reference

| Strategy | Best Use Case | Risk |
| :--- | :--- | :--- |
| **Regex** | Extracting specific ID/Pattern from chatter. | Fragile if pattern changes. |
| **XML** | Large document generation (Claude). | Verbose (more tokens). |
| **CSV** | Simple lists of strings. | Splitting errors on commas inside content. |
| **Wait/Retry** | Transient network/model glitches. | Increased latency. |
