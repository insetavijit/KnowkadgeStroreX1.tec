| **Subtopic**                                          | **Focus & Purpose**                         | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | ------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.2.2.1 ChatModel Class]]**                     | Understand message-based interface          | ChatModel, message lists, SystemMessage, HumanMessage, AIMessage                | ChatModels work with structured message conversations.              |
| **[[LC1.2.2.2 LLM Class]]**                           | Understand completion-based interface       | LLM, string input/output, text completions, legacy patterns                     | LLMs take string input and return string completions.               |
| **[[LC1.2.2.3 Message-Based vs Completion-Based]]**   | Compare the two paradigms                   | Conversation context, role-based messages, single-string completions            | ChatModels use messages; LLMs use plain strings.                    |
| **[[LC1.2.2.4 When to Use Each]]**                    | Make appropriate interface choices          | Conversational apps vs text generation, provider support, feature requirements  | Use ChatModels for conversations, LLMs for simple completions.      |
| **[[LC1.2.2.5 Migration Considerations]]**            | Migrate between interface types             | Adapting code, converting messages to strings, preserving functionality         | Migrate legacy LLM code to ChatModel for modern features.           |

# ChatModels vs LLMs: The Paradigm Shift

In 2022, "LLMs" were text-completion engines. You gave them a string, and they predicted the next token.
In 2024, the best models (GPT-4, Claude 3, Llama 3) are **Chat Models**. They are fine-tuned to understand structured instructions.

LangChain treats these as distinct primitives: `LLM` vs `ChatModel`. Understanding the difference allows you to write effective prompts.

---

## 1. The Core Distinction

### The Legacy "LLM" (String In, String Out)
Think of this as an advanced autocomplete.
*   **Input**: "The capital of France is"
*   **Output**: " Paris."

```python
# Legacy LLM Usage
llm.invoke("The capital of France is")
```

### The Modern "ChatModel" (Messages In, Message Out)
Think of this as a role-playing conversation.
*   **Input**: `[System: "Be concise.", Human: "Capital of France?"]`
*   **Output**: `[AI: "Paris."]`

```python
# Modern Chat Usage
chat.invoke([
    SystemMessage(content="Be concise."),
    HumanMessage(content="Capital of France?")
])
```

---

## 2. The Message Primitives

Structuring your input into specific message types provides **semantic hints** to the model about how to interpret the text.

| Message Type | Role | Analogy |
| :--- | :--- | :--- |
| **SystemMessage** | Meta-instructions, guardrails, personality. | The "Director" giving notes to an actor. |
| **HumanMessage** | The user's query or input. | The "Audience" asking a question. |
| **AIMessage** | The model's response. | The "Actor" performing lines. |
| **ToolMessage** | Results from function calls. | The "Prop" handed to the actor. |

> **Pro Tip**: Placing instructions in the `SystemMessage` is significantly more robust against "Jailbreaks" than placing them in the `HumanMessage`.

---

## 3. Why the Industry Shifted

Why did OpenAI and Anthropic deprecate their completion endpoints in favor of Chat?

1.  **Safety**: It is easier to train a model to refuse harmful requests when the system instructions are separated from user input.
2.  **Multimodality**: A "message" can contain images, files, or tool calls. A raw string cannot easily represent this structure.
3.  **Function Calling**: Models listen for specific tool signatures in the stream. This requires a structured message protocol.

---

## 4. When to Use Which?

### Use `ChatModel` (99% of cases)
*   **Examples**: `ChatOpenAI`, `ChatAnthropic`, `ChatOllama`.
*   **Why**: It supports System Prompts, Tool Calling, and Multimodal inputs. It is the focus of all modern R&D.

### Use `LLM` (1% of cases)
*   **Examples**: `OpenAI` (Legacy), `HuggingFacePipeline` (Base models).
*   **Why**: You are using an old, base completion model (like `gemma-2b-base`) that hasn't been fine-tuned for instruction following. This is rare in production apps but common researchers.

---

## 5. Converting Between Paradigms

Sometimes you need to swap them. LangChain handles the translation automatically.

*   **Chat -> LLM**: If you pass a list of messages to a pure `LLM`, LangChain flattens them into a string:
    *   `System: You are helpful.` + `Human: Hi` -> `"System: You are helpful.\nHuman: Hi"`
*   **LLM -> Chat**: If you pass a string to a `ChatModel`, LangChain wraps it in a `HumanMessage`.

---

## Quick Reference

| Feature | LLM | ChatModel |
| :--- | :--- | :--- |
| **Input** | String | List[`BaseMessage`] |
| **Output** | String | `AIMessage` |
| **System Prompts** | Hacky (Prepended string) | Native (`SystemMessage`) |
| **Tool Use** | Difficult | Native |
| **Modern Best Practice** | ❌ Deprecated | ✅ Standard |
