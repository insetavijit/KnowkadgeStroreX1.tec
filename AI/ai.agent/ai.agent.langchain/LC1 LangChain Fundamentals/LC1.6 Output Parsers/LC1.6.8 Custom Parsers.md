| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.6.8.1 Building Custom Output Parsers]]**      | Create domain-specific parsers               | Custom parser classes, specialized extraction, domain logic                     | Build custom parsers for specialized output needs.                  |
| **[[LC1.6.8.2 BaseOutputParser Interface]]**          | Implement the base interface                 | BaseOutputParser class, required methods, type parameters                       | Extend BaseOutputParser to create custom parsers.                   |
| **[[LC1.6.8.3 Parse Method]]**                        | Implement core parsing logic                 | parse() method, string input, typed output                                      | Implement parse() to define core parsing logic.                     |
| **[[LC1.6.8.4 Get Format Instructions]]**             | Generate prompting guidance                  | get_format_instructions() method, LLM guidance, output hints                    | Implement get_format_instructions() for LLM guidance.               |
| **[[LC1.6.8.5 Specialized Parsing Use Cases]]**       | Apply custom parsers practically             | Domain extraction, custom formats, legacy system integration                    | Custom parsers suit domain-specific extraction needs.               |

# Custom Parsers: Domain-Specific Logic

Sometimes, you aren't parsing JSON. You are parsing a Domain Specific Language (DSL), a log file, or a custom protocol.
LangChain allows you to build a parser that integrates natively with the `Runnable` ecosystem.

---

## 1. The Easy Way: `RunnableLambda`

For 90% of cases, you don't need a class. A function is enough.

```python
def parse_sales_code(text: str) -> dict:
    # Expected format: "ITEM-SKU-PRICE"
    parts = text.strip().split("-")
    return {
        "item": parts[0],
        "sku": parts[1],
        "price": float(parts[2])
    }

chain = model | StrOutputParser() | parse_sales_code
```

**Pros**: Zero boilerplate.
**Cons**: No `get_format_instructions()`. You must manually tell the model "Please output in ITEM-SKU-PRICE format".

---

## 2. The Formal Way: Subclassing `BaseOutputParser`

If you want to package your parser as a reusable component (library), subclass `BaseOutputParser`.
You *must* define the generic type `T` (what it returns).

```python
from langchain_core.output_parsers import BaseOutputParser
from typing import List

class BooleanListParser(BaseOutputParser[List[bool]]):
    """Parse 'YES, NO, YES' into [True, False, True]"""

    def parse(self, text: str) -> List[bool]:
        cleaned = text.strip().upper().split(",")
        return [item.strip() == "YES" for item in cleaned]

    def get_format_instructions(self) -> str:
        return "Output a comma-separated list of YES or NO values."
```

**Architectural Benefit**:
By implementing `get_format_instructions`, you allow users to inject the instructions into their prompt automatically:

```python
parser = BooleanListParser()
prompt = PromptTemplate(
    template="Answer 3 questions.\n{format_instructions}",
    partial_variables={"format_instructions": parser.get_format_instructions()}
)
```

---

## 3. Streaming Support

`BaseOutputParser` does not support streaming by default. It waits for the full string.
To support streaming, you must implement `parse_iterator`.

This is complex because you have to handle "partial tokens."
*   If the token is `"Y"`, you can't parse it yet.
*   If the next token is `"E"`, you still can't.
*   If the next token is `"S,"`, NOW you can emit `True`.

This requires a state machine. Most developers avoid this unless absolutely necessary.

---

## Quick Reference

| Method | Complexity | Use Case |
| :--- | :--- | :--- |
| **Function** | Low | Ad-hoc regex or split logic. |
| **BaseOutputParser** | Medium | Reusable logic with Prompt Instructions. |
| **TransformOutputParser** | High | Streaming Protocol Parsers. |
