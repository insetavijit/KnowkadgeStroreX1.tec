| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.2.7.1 Temperature]]**                         | Control output randomness                    | 0.0 to 2.0 range, determinism vs creativity, use case alignment                 | Lower temperature = focused; higher = creative.                     |
| **[[LC1.2.7.2 Max Tokens]]**                          | Limit response length                        | max_tokens parameter, context budget, truncation prevention                     | Set max_tokens to control response length and costs.                |
| **[[LC1.2.7.3 Top-p (Nucleus Sampling)]]**            | Alternative sampling strategy                | top_p vs temperature, probability mass, typical values                          | Use top_p for probability-based token sampling.                     |
| **[[LC1.2.7.4 Frequency & Presence Penalty]]**        | Reduce repetition                            | frequency_penalty, presence_penalty, token diversity, -2.0 to 2.0 range         | Use penalties to reduce repetitive or redundant output.             |
| **[[LC1.2.7.5 Stop Sequences]]**                      | Control output termination                   | stop parameter, custom delimiters, multi-stop, parsing implications             | Stop sequences halt generation at specific strings.                 |

# Model Parameters: Tuning the Engine

LLMs are probabilistic engines. They don't have "Answers"; they have "Next Token Probabilities."
Model parameters control how the engine **samples** from these probabilities.

Think of these parameters as the **BIOS Settings** of your AI application.

---

## 1. Temperature (Entropy Control)

Temperature controls the "Flatness" of the probability distribution.

*   **Temp 0.0**: "Greedy Decoding." The model *always* picks the most likely next token.
    *   *Result*: Deterministic, robotic, repetitive.
    *   *Use Case*: SQL generation, Coding, Data extraction.
*   **Temp 1.0**: "Standard Sampling." The model picks from the distribution proportionally.
    *   *Result*: Natural, fluent, varied.
    *   *Use Case*: Chatbots, summarization.
*   **Temp 2.0**: "Maximum Entropy." The model amplifies rare tokens.
    *   *Result*: Hallucinatory, chaotic, potentially brilliant or broken.
    *   *Use Case*: Brainstorming wild ideas.

> **Architectural Rule**: For Agents and Tools, ALWAYS use **Temperature 0**. You want the tool arguments to be mathematically precise, not "creative."

---

## 2. Top-P (Nucleus Sampling)

Top-P is a sharper knife than Temperature. It truncates the long tail of low-probability tokens.
`top_p=0.9` means: "Only consider the top 90% of probability mass. Ignore the bottom 10% of crazy words."

**The Golden Rule**: Use Temperature OR Top-P. Do not tune both simultaneously unless you are a research scientist. They fight each other.

---

## 3. Stop Sequences (The Safety Brakes)

A `stop` sequence tells the model: "If you generate this string, STOP immediately and return control to the Python process."

This is **critical** for:
1.  **Chatbots**: Stop at `User:` so the AI doesn't hallucinate a fake conversation between two people.
2.  **Agents**: Stop at `Observation:` so the AI doesn't hallucinate the result of a tool call before running it.

```python
chat = ChatOpenAI(model="gpt-4")

# "Chain of Thought" Pattern
chat.invoke(
    "Think step-by-step...", 
    stop=["\nFINAL ANSWER:"] # Stop before giving the final answer if logic is split
)
```

---

## 4. Run-Time Parameter Injection

In a LangChain app, you often reuse the same model object but need different parameters for different conceptual steps.
Do not instantiate 5 `ChatOpenAI` objects. Use `.bind()`.

```python
# The Singleton Model
llm = ChatOpenAI(model="gpt-4")

# The Variants
creative_llm = llm.bind(temperature=0.9)
coding_llm = llm.bind(temperature=0.0)
short_llm = llm.bind(max_tokens=50)

# Implementation
story = creative_llm.invoke("Write a story")
code = coding_llm.invoke("Write python code for it")
```

---

## 5. Penalties (The Anti-Looping Mechanism)

If your model gets stuck saying "The cat sat on the cat sat on the cat...", you need penalties.

*   **Frequency Penalty**: Punishes a token based on how many times it has appeared so far. (Eliminates verbatim repetition).
*   **Presence Penalty**: Punishes a token if it has appeared *at all*. (Encourages new topics).

> **Warning**: High penalties damage reasoning capability. Use sparingly (0.1 - 0.5), never aggressively (2.0), or the model will become incoherent efficiently.

---

## Quick Reference

| Parameter | Default | Recommended (Code) | Recommended (Chat) |
| :--- | :--- | :--- | :--- |
| **Temperature** | 0.7 | **0.0** | 0.7 - 1.0 |
| **Top-P** | 1.0 | 1.0 | 0.9 |
| **Max Tokens** | Inf | ~4000 (Safety) | Inf |
| **Stop** | None | `["\nObservation:"]` | None |
