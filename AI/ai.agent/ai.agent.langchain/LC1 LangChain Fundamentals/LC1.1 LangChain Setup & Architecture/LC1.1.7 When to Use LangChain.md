| **Subtopic**                                              | **Focus & Purpose**                            | **Key Concepts / Details**                                                     | **One-Line Recall**                                                  |
| --------------------------------------------------------- | ---------------------------------------------- | ------------------------------------------------------------------------------ | -------------------------------------------------------------------- |
| **[[LC1.1.7.1 Orchestration-Heavy Workflows]]**           | Identify complex workflow scenarios            | Multi-step pipelines, conditional logic, branching flows                       | Use LangChain when orchestrating complex multi-step LLM workflows.   |
| **[[LC1.1.7.2 Multi-Step Reasoning]]**                    | Handle tasks requiring chained thought         | Chain-of-thought, decomposition, iterative refinement                          | LangChain excels at tasks needing sequential reasoning steps.        |
| **[[LC1.1.7.3 Tool-Augmented Agents]]**                   | Build agents that use external tools           | Tool calling, API integration, action execution                                | Choose LangChain for agents that need to use external tools.         |
| **[[LC1.1.7.4 When Plain API Calls Suffice]]**            | Recognize simpler alternatives                 | Direct API usage, single-shot completions, minimal orchestration               | Skip LangChain for simple, single-call LLM interactions.             |
| **[[LC1.1.7.5 Decision Framework]]**                      | Apply a structured decision process            | Complexity assessment, feature requirements, trade-off analysis                | Evaluate project needs to decide if LangChain adds value.            |

# When to Use LangChain: The Decision Framework

Not every AI project needs a framework. Just as you wouldn't use React to build a static "Hello World" site, you shouldn't use LangChain for a single prompt.

The decision comes down to one variable: **Orchestration Complexity**.

---

## 1. The Simplification Trap

**Scenario**: You just want to summarise a block of text.
**Approach**: Direct API.

```python
# Pure OpenAI - Simple and Clean
response = client.chat.completions.create(
    model="gpt-3.5-turbo",
    messages=[{"role": "user", "content": "Summarize this..."}]
)
```

**Verdict**: **Avoid LangChain**. Introducing a framework here adds abstraction overhead without benefit. You don't need a heavy duty wrapper for a single function call.

---

## 2. The Tipping Point: Complexity Creep

As soon as your application evolves beyond "Input -> Output," complexity explodes.

**The Tipping Point Indicators:**
1.  **Context Management**: You need to track history across 50 turns.
2.  **Model Switching**: You want to test if Claude 3 is better than GPT-4 without rewriting code.
3.  **Structured Output**: You need the AI to return valid SQL, and you need retry logic if it fails.
4.  **RAG**: You need to fetch data from a database before answering.

**Verdict**: **Use LangChain**. Handling these manually leads to "Boilerplate Hell"—reinventing retry loops, parser logic, and connection handling.

---

## 3. The Sweet Spot: Cognitive Architectures

LangChain shines when the **control flow** depends on the model's output.

### 1. Agents (Dynamic Loops)
If the application needs to "decide" what to do next (e.g., "Search Google" vs "Calculate Math"), you need an Agent Runtime. Writing a robust ReAct loop from scratch is difficult and error-prone. LangChain solves this out of the box.

### 2. Multi-Hop Chains
"Take existing code, write a unit test for it, run the test, and if it fails, fix the code."
This is a 4-step loop with conditional logic. LangChain's `Graph` (via LangGraph) or `Chain` primitives model this DAG (Directed Acyclic Graph) perfectly.

---

## 4. The Trade-Off Matrix

| Feature | Raw API (OpenAI/Anthropic) | LangChain |
| :--- | :--- | :--- |
| **Setup Speed** | Instant | Low (Learning Curve) |
| **Control** | Absolute | High (but abstracted) |
| **Maintainability** | Low (Spaghetti code grows fast) | High (Modular components) |
| **Observability** | Manual logging | Built-in (LangSmith) |
| **Vendor Lock-in** | High (Rewrites needed to switch) | Low (Config change only) |

---

## 5. Professional Recommendation

**Start with the Raw API** for prototyping to understand the model's capabilities.
**Switch to LangChain** the moment you need:
1.  **Memory** (Conversation History).
2.  **Data** (RAG/Document Loaders).
3.  **Tools** (API Actions).

> **The "100-Line Code" Rule**: If your `openai_api_call.py` file exceeds 100 lines of logic (parsers, retries, history management), you have reinvented a worse version of LangChain. Switch now.

---

## Quick Reference

| Use Case | Recommendation | Why? |
| :--- | :--- | :--- |
| **Single Prompt** | ❌ No | Overkill. Just use `requests` or `openai`. |
| **Chatbot** | ✅ Yes | Needs Memory and History management. |
| **Q&A on PDF** | ✅ Yes | Needs Parsers, RecursiveSplitters, Retrievers. |
| **Autonomous Agent** | ✅✅ **Critical** | Needs Tool-use loops and error handling. |
| **Evaluation** | ✅ Yes | Needs consistent interfaces for testing many models. |
