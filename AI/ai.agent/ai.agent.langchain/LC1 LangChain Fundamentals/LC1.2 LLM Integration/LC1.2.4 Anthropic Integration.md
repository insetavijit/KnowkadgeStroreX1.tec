| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.2.4.1 Setting Up ChatAnthropic]]**            | Initialize Anthropic chat models             | ChatAnthropic class, langchain-anthropic package, basic usage                   | Use ChatAnthropic() to initialize Claude models.                    |
| **[[LC1.2.4.2 Claude Models Overview]]**              | Understand Claude model variants             | Claude 3 Opus, Sonnet, Haiku; capabilities; context windows; use cases          | Claude offers Opus (powerful), Sonnet (balanced), Haiku (fast).     |
| **[[LC1.2.4.3 API Configuration]]**                   | Configure Anthropic authentication           | ANTHROPIC_API_KEY env var, direct key passing, API versioning                   | Set ANTHROPIC_API_KEY for Claude model access.                      |
| **[[LC1.2.4.4 Anthropic-Specific Features]]**         | Leverage unique Anthropic capabilities       | Extended context, system prompts, thinking mode, tool use                       | Anthropic offers extended context and unique prompt handling.       |
| **[[LC1.2.4.5 Message Formatting Differences]]**      | Handle Anthropic message requirements        | System message handling, alternating roles, content blocks                      | Anthropic requires alternating user/assistant messages.             |

# Anthropic Integration: The High-Context Specialist

If OpenAI is the "Default," Anthropic is the "Specialist." The Claude family of models architectures are distinct because they were prioritized for **Safety, Context Length, and Coding Capability** from day one.

While textually similar to OpenAI, the `ChatAnthropic` wrapper handles significant "Protocol Drift" under the hood to make them compatible.

---

## 1. The Model Architecture (Opus/Sonnet/Haiku)

Anthropic uses a clear "Three Body" problem approach to model selection.

| Model | Identity | Best Use Case |
| :--- | :--- | :--- |
| **Claude 3.5 Opus** | The Genius | Complex reasoning, Math, Creative Writing. Slower. |
| **Claude 3.5 Sonnet** | The Workhorse | **Coding**. It is widely considered the SOTA coding model (as of 2024). |
| **Claude 3 Haiku** | The Flash | Extreme speed. Categorization, summary of small texts. |

```python
from langchain_anthropic import ChatAnthropic

# The SOTA Coding Setup
chat = ChatAnthropic(
    model_name="claude-3-5-sonnet-20240620",
    temperature=0
)
```

---

## 2. The Strict Protocol: Alternating Roles

Unlike OpenAI, which is forgiving, Anthropic's API is **Pedantic**.
It strictly enforces `User -> AI -> User -> AI`.
You cannot have `User -> User`.

**The LangChain Fix**:
If you accidentally send two `HumanMessages` in a row, `ChatAnthropic`'s wrapper automatically **merges** them into a single string to prevent an API crash.

> **Why this matters**: When building conversational agents that might "think" to themselves (looping), you must ensure the conversation history doesn't violate this structure. LangChain's `BaseChatModel` abstraction handles 90% of this, but it's a common source of debugging pain.

---

## 3. Large Context Windows & "Needle in a Haystack"

Claude's claim to fame is its 200k+ token context window and near-perfect recall.

**Architectural implication**:
With OpenAI, you often need **RAG** (Chop data into small chunks -> Vector Store -> Retrieve).
With Anthropic, you can often just **Stuff the Prompt** (Put the entire 100-page PDF in the prompt).

```python
# The "Context Stuffing" Pattern
chain = (
    {"context": load_big_pdf, "question": RunnablePassthrough()}
    | prompt
    | ChatAnthropic(model="claude-3-opus-20240229")
)
```
*Note: This is more expensive ($) but significantly more accurate than RAG for global understanding.*

---

## 4. System Prompts & Tool Use

Anthropic treats System Prompts differently. They are not part of the message list; they are top-level parameters.
LangChain hides this execution detail:

```python
# You write this:
messages = [
    SystemMessage(content="You are a pirate."),
    HumanMessage(content="Hi")
]
# LangChain sends this to API:
# { "system": "You are a pirate", "messages": [{"role": "user", "content": "Hi"}] }
```

**Tool Use (Beta/Main)**:
Anthropic's tool use is robust but verbose. The wrapper handles formatting the XML-like structures or JSON structures that Claude expects, normalizing them into the standard `ToolMessage` format used by the rest of your app.

---

## 5. Technical Nuances

1.  **Stop Sequences**: Anthropic allows custom stop sequences to halt generation early.
    ```python
    chat.bind(stop=["\nObservation:"])
    ```
2.  **Streaming**: Claude's streaming API uses "Server-Sent Events" (SSE). LangChain normalizes this so `chat.stream()` looks identical to OpenAI's stream, despite the disparate underlying protocols.

---

## Quick Reference

| Feature | Code | Note |
| :--- | :--- | :--- |
| **Package** | `pip install langchain-anthropic` | Separate from core. |
| **Env Var** | `ANTHROPIC_API_KEY` | Starts with `sk-ant...` |
| **Key Model** | `claude-3-5-sonnet-20240620` | Go-to for coding. |
| **Constraint** | Must alternate User/AI | Wrapper helps merge duplicates. |
| **Superpower** | Context Window | Good for massive document analysis. |
