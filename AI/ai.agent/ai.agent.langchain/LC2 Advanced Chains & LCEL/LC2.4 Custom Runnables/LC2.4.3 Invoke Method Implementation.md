| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.4.3.1 Implementing Invoke]]**                 | Code invoke method                           | def invoke(self, input, config), core logic                                     | Implement invoke() with input processing logic.                     |
| **[[LC2.4.3.2 Input Processing]]**                    | Handle incoming data                         | Validation, transformation, preparation                                         | Process and validate input before main logic.                       |
| **[[LC2.4.3.3 Output Generation]]**                   | Create return values                         | Result construction, format, return patterns                                    | Generate and return properly formatted output.                      |
| **[[LC2.4.3.4 Error Handling in Invoke]]**            | Manage failures                              | Try/except, error propagation, error types                                      | Handle errors gracefully within invoke.                             |
| **[[LC2.4.3.5 Config Usage]]**                        | Use RunnableConfig                           | Accessing config, callbacks, tags, metadata                                     | Use config for callbacks and runtime settings.                      |

# Invoke Method: The Core Execution

`invoke(input, config)` is the fundamental method. Everything else builds on it.

---

## 1. The Signature

```python
def invoke(
    self,
    input: Input,
    config: Optional[RunnableConfig] = None
) -> Output:
    ...
```

*   **`input`**: The data from the previous step. Its type is defined by your `Runnable[Input, Output]` generics.
*   **`config`**: Runtime settings (callbacks, metadata, etc.).

---

## 2. A Complete Implementation

```python
from langchain_core.runnables import Runnable, RunnableConfig
from typing import Optional

class SentimentScorer(Runnable[str, float]):
    def __init__(self, model_path: str):
        self.model = load_model(model_path)
    
    def invoke(
        self,
        input: str,
        config: Optional[RunnableConfig] = None
    ) -> float:
        # 1. Preprocess
        cleaned = input.strip().lower()
        
        # 2. Execute Core Logic
        score = self.model.predict(cleaned)
        
        # 3. Return
        return score
```

---

## 3. Accessing Config

The `config` dictionary contains:
*   `callbacks`: List of callback handlers.
*   `tags`: List of strings for filtering.
*   `metadata`: Custom key-value pairs.
*   `run_name`: Name for LangSmith.
*   `configurable`: Custom settings (e.g., `model_name`).

```python
def invoke(self, input, config=None):
    config = config or {}
    timeout = config.get("configurable", {}).get("timeout", 30)
    # ... use timeout
```

---

## Quick Reference

| Step | Purpose |
| :--- | :--- |
| **Validate** | Ensure input matches expected type. |
| **Transform** | Clean or reshape input. |
| **Execute** | Run core logic (API call, DB query). |
| **Return** | Output in expected schema. |
