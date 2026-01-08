| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.8.8.1 Timing Chain Execution]]**              | Measure execution time                       | Start/end timing, duration calculation, profiling                               | Time chain execution to identify slow components.                   |
| **[[LC1.8.8.2 Token Usage Tracking]]**                | Monitor token consumption                    | Token counting, usage callbacks, consumption tracking                           | Track token usage via callbacks for cost control.                   |
| **[[LC1.8.8.3 Cost Monitoring]]**                     | Track API costs                              | Cost calculation, budget tracking, cost alerts                                  | Monitor costs by tracking tokens and pricing.                       |
| **[[LC1.8.8.4 Latency Measurement]]**                 | Track response times                         | P50/P99 latency, latency distribution, SLA tracking                             | Measure latency percentiles for performance SLAs.                   |
| **[[LC1.8.8.5 Performance Optimization]]**            | Improve chain performance                    | Bottleneck elimination, caching, parallelization                                | Optimize based on performance metrics and traces.                   |

# Performance Monitoring: The Cost of Intelligence

In AI Engineering, "Performance" means two things:
1.  **Latency** (Time to First Token).
2.  **Cost** (Dollars per 1k requests).

You cannot optimize what you do not measure.

---

## 1. Counting Tokens (`get_openai_callback`)

LangChain provides a context manager to audit token usage for a specific block of code.
This works by attaching a temporary callback handler that sums up usage.

```python
from langchain_community.callbacks import get_openai_callback

with get_openai_callback() as cb:
    chain.invoke("Tell me a joke")
    chain.invoke("Tell me another")

print(f"Total Tokens: {cb.total_tokens}")
print(f"Total Cost: ${cb.total_cost}")
```

**Architectural Note**:
This usually only works for OpenAI models. For Anthropic/Google, you may need to check the `response.response_metadata` directly or use LangSmith.

---

## 2. Latency Analysis

Why is your chain slow?
*   **Networking**: DNS/Connection to OpenAI API.
*   **Generation**: The model is outputting 500 tokens (approx 10 seconds).
*   **Seriation**: You are passing a 10MB PDF to the prompt.

**The Fix**:
Right-size your Prompt.
If you send 10k tokens of context but only need 1 sentence, you are paying for **Prompt Processing Time** (Pre-fill latency).

---

## 3. Caching (The Semantic Cache)

The fastest request is the one you don't make.
If 20% of your users ask "What is your pricing?", you should cache that answer.

```python
from langchain.globals import set_llm_cache
from langchain_community.cache import InMemoryCache

# Enable Global Caching
set_llm_cache(InMemoryCache())

# First call: 2 seconds (API Call)
llm.invoke("What is the capital of France?")

# Second call: 0.001 seconds (Cache Hit)
llm.invoke("What is the capital of France?")
```

**Production Tip**: Use `RedisCache` instead of `InMemoryCache` so the cache persists across server restarts.

---

## Quick Reference

| Metric | Target (Good) | Target (Bad) |
| :--- | :--- | :--- |
| **TTFT (Time To First Token)** | < 800ms | > 2000ms |
| **Total Generation Speed** | > 50 tokens/sec | < 10 tokens/sec |
| **Cache Hit Rate** | > 20% | 0% |
