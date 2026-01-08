| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.5.7.1 Unit Testing Components]]**             | Test chain parts independently               | Isolated tests, mock inputs, output validation                                  | Unit test each chain component independently.                       |
| **[[LC2.5.7.2 Integration Testing]]**                 | Test complete chains                         | End-to-end tests, component interaction, full flow                              | Integration test complete chain flows.                              |
| **[[LC2.5.7.3 Mocking]]**                             | Replace dependencies in tests                | Mock LLMs, mock tools, test doubles                                             | Mock external dependencies for fast, reliable tests.                |
| **[[LC2.5.7.4 Test Isolation]]**                      | Keep tests independent                       | No shared state, deterministic, reproducible                                    | Isolate tests to avoid interference.                                |
| **[[LC2.5.7.5 Testing Strategies]]**                  | Apply testing best practices                 | Test pyramids, coverage, CI integration                                         | Apply testing strategies for composed chains.                       |

# Testing Composed Chains: The Test Pyramid

LLM chains are notoriously hard to test because LLM outputs are non-deterministic.
But you *can* test everything *around* the LLM.

---

## 1. The Test Pyramid for AI

```
      /  E2E (Full LLM Calls)  \   <- Slowest, Most Expensive
     /  Integration (Mocked LLM)  \
    /   Unit (No LLM at all)        \ <- Fastest, Cheapest
```

*   **Unit**: Test your data transformations, parsers, adapters *without* calling any LLM.
*   **Integration**: Test the full chain flow with a **Mocked LLM**.
*   **E2E**: Test with real LLMs. This is expensive and flaky. Use sparingly.

---

## 2. Mocking the LLM

```python
from unittest.mock import MagicMock

def test_chain_with_mocked_llm():
    mock_llm = MagicMock()
    mock_llm.invoke.return_value = AIMessage(content='{"answer": "test"}')
    
    chain = prompt | mock_llm | parser
    result = chain.invoke({"question": "Hello"})
    
    assert result["answer"] == "test"
```

**Benefit**: Runs in milliseconds. No API calls. Deterministic.

---

## 3. LangSmith Datasets (For E2E)

For E2E tests, use LangSmith to create a **Golden Dataset** of known inputs -> expected outputs.

```python
from langsmith import Client

client = Client()
results = client.run_on_dataset(
    dataset_name="my_eval_set",
    llm_or_chain_factory=lambda: my_chain
)
```

This runs your chain against a set of curated examples and checks if the outputs are acceptable.

---

## Quick Reference

| Test Type | LLM Call? | Speed | When to Use |
| :--- | :--- | :--- | :--- |
| **Unit** | No | <1s | Every commit (CI). |
| **Integration** | Mocked | <10s | Every PR. |
| **E2E** | Real | ~min | Nightly / Weekly. |
