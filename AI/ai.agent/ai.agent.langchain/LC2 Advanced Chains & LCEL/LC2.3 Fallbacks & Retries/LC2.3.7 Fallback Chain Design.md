| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.3.7.1 Simpler Fallback Models]]**             | Use less complex alternatives                | Smaller models, simpler prompts, reduced capability                             | Use simpler, more reliable models as fallbacks.                     |
| **[[LC2.3.7.2 Cost-Effective Fallbacks]]**            | Minimize fallback costs                      | Cheaper models, cached responses, pre-computed answers                          | Choose cost-effective fallbacks for budget control.                 |
| **[[LC2.3.7.3 Faster Fallbacks]]**                    | Prioritize speed                             | Lower latency options, local models, cached results                             | Use faster fallbacks when speed matters most.                       |
| **[[LC2.3.7.4 Fallback Hierarchy]]**                  | Design fallback tiers                        | Premium → standard → basic, tiered degradation                                  | Design tiered fallback hierarchy by capability.                     |
| **[[LC2.3.7.5 Fallback Selection Criteria]]**         | Choose appropriate fallbacks                 | Reliability, cost, capability trade-offs                                        | Select fallbacks balancing reliability, cost, and capability.       |

# Fallback Chain Design: The Tiered Architecture

The order and nature of your fallbacks is a design decision with cost, latency, and quality trade-offs.

---

## 1. The Standard Hierarchy

| Tier | Model | Quality | Cost/1K Req | Latency |
| :--- | :--- | :--- | :--- | :--- |
| **Primary** | GPT-4o | **** | $0.50 | 2s |
| **Fallback 1** | Claude 3.5 Sonnet | *** | $0.30 | 1.5s |
| **Fallback 2** | GPT-4o-mini | ** | $0.02 | 0.8s |
| **Fallback 3** | Hardcoded | * | $0.00 | 0.001s |

**Principle**: Quality Decreases, Speed Increases, Cost Decreases.

---

## 2. Provider Diversity (Avoid Cascade Failure)

If your fallback is also on OpenAI, an OpenAI outage kills *both*.

**Bad**:
`gpt-4 -> gpt-3.5-turbo` (Both on same infra)

**Good**:
`gpt-4 -> claude-3 -> gemini-pro` (Different providers)

---

## 3. Designing for Cache Hits

The best fallback is one that doesn't need an API call at all.

**Pattern**: Semantic Cache.
```python
from langchain_core.cache import InMemoryCache

cache = InMemoryCache()

# On Fallback 3, check the cache first
def check_cache(x):
    cached = cache.lookup(x["question"])
    if cached:
        return cached
    return "I cannot answer that right now."
```

If a user asks a common question ("What are your business hours?"), the cache can serve it even when all LLMs are down.

---

## Quick Reference

| Fallback Type | Trade-off |
| :--- | :--- |
| **Cheaper Model** | Lower quality, same latency. |
| **Faster Model** | Same quality (maybe lower), lower latency. |
| **Cache** | Zero cost, instant, but limited coverage. |
| **Hardcoded** | Zero cost, instant, terrible quality. |
