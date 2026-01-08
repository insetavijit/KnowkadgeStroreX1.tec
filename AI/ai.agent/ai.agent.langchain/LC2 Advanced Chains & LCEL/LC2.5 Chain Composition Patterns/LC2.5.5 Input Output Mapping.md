| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.5.5.1 RunnablePassthrough.assign]]**          | Add fields to passthrough                    | assign() method, field addition, data enrichment                                | Use assign() to add computed fields to data.                        |
| **[[LC2.5.5.2 Key Transformation]]**                  | Rename and map keys                          | Key renaming, field mapping, restructuring                                      | Transform keys to match downstream requirements.                    |
| **[[LC2.5.5.3 Data Reshaping]]**                      | Restructure data format                      | Format conversion, nesting, flattening                                          | Reshape data between chain components.                              |
| **[[LC2.5.5.4 Adapter Patterns]]**                    | Bridge incompatible interfaces               | Adapter chains, format conversion, compatibility                                | Use adapters to bridge incompatible interfaces.                     |
| **[[LC2.5.5.5 Data Flow Patterns]]**                  | Design data movement                         | Flow direction, data transformations, pipeline patterns                         | Design clear data flow through chain pipelines.                     |

# Input Output Mapping: The Glue Code

When Module A outputs `{"result": ...}` but Module B expects `{"input": ...}`, you need an **Adapter**.

---

## 1. `RunnablePassthrough.assign()` (The Swiss Army Knife)

This is the most important data manipulation tool in LCEL.

```python
from langchain_core.runnables import RunnablePassthrough

# Original Input: {"question": "What is 2+2?"}

chain = (
    RunnablePassthrough.assign(
        # Pass through all existing keys, PLUS add these new ones:
        docs=retriever,               # Adds docs
        formatted_q=format_question   # Adds formatted_q
    )
    | llm
)

# Input to LLM: {"question": "...", "docs": [...], "formatted_q": "..."}
```

**Benefit**: You don't have to write `x["question"]` manually. Everything passes through.

---

## 2. Key Renaming (The Adapter)

If Module A says `answer` but Module B expects `response`:

```python
def rename_key(x):
    return {"response": x["answer"]}

adapter = RunnableLambda(rename_key)

chain = module_a | adapter | module_b
```

---

## 3. Flattening / Nesting

**Flatten**:
```python
# From: {"user": {"name": "Alice", "id": 1}}
# To: {"user_name": "Alice", "user_id": 1}
```

**Nest**:
```python
# From: {"user_name": "Alice", "user_id": 1}
# To: {"user": {"name": "Alice", "id": 1}}
```

These are common when bridging between external APIs and your internal chain format.

---

## Quick Reference

| Operation | Tool |
| :--- | :--- |
| **Add fields** | `RunnablePassthrough.assign()` |
| **Rename keys** | `RunnableLambda(fn)` |
| **Complex transform** | `RunnableLambda(fn)` |
