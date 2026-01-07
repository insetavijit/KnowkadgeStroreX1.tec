| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.3.8.1 Clarity and Specificity]]**             | Write unambiguous prompts                    | Precise language, no ambiguity, explicit expectations                           | Be specific and unambiguous in prompt instructions.                 |
| **[[LC1.3.8.2 Instruction Formatting]]**              | Structure instructions effectively           | Numbered steps, bullet points, clear delimiters                                 | Format instructions with clear structure and hierarchy.             |
| **[[LC1.3.8.3 Context Placement]]**                   | Position context optimally                   | Context ordering, primacy/recency, attention patterns                           | Place important context where the model attends most.               |
| **[[LC1.3.8.4 Output Format Specification]]**         | Define expected output structure             | Format examples, JSON schemas, structured output hints                          | Explicitly specify the desired output format.                       |
| **[[LC1.3.8.5 Iterative Refinement]]**                | Improve prompts systematically               | Testing, evaluation, A/B comparison, version tracking                           | Iterate on prompts based on output quality testing.                 |

# Prompt Best Practices: The Professional Standard

Prompt Engineering is not "whispering." It is **Programming in Natural Language**.
Just as Python has PEP-8, Prompts have architectural standards that maximize model compliance.

---

## 1. The Standard Structure (RTCFC)

Do not write a "Wall of Text." Structure your prompt into five distinct blocks.

1.  **ROLE**: Who is the AI? (Persona)
2.  **TASK**: What must be done? (Verb)
3.  **CONTEXT**: What data is needed? (Input)
4.  **FORMAT**: How should it look? (Output)
5.  **CONSTRAINTS**: What is forbidden? (Negative)

 **The Template**:
```text
# ROLE
You are a Senior Data Engineer.

# TASK
Analyze the provided SQL logs and identify inefficient queries.

# CONTEXT
Logs: {logs}

# CONSTRAINTS
- Do not explain basic SQL concepts.
- Do not suggest indexing unless the table > 1GB.

# FORMAT
Output a CSV string with columns: query, duration, issue.
```

---

## 2. Chain of Thought (CoT)

For logic, math, or reasoning, LLMs are bad at "Zero-Shot" answers.
They improve by 300% if you ask them to "Think" first.

**The Magic Phrase**: `"Let's think step by step."`

**Architectural Pattern**:
Force the model to output a `scratchpad` field before the `answer` field.

```json
// Desired Output
{
    "thought_process": "First I will calculate the total...",
    "final_answer": 42
}
```

If you ask for *only* the JSON answer, the model has no "mental space" to do the math. It must hallucinate the answer immediately.

---

## 3. The "Emotion" Hack (Attention Manipulation)

LLMs pay attention to "Urgency" markers.
Adding phrases like **"This is critical for my career"** or **"I have no fingers"** (tipping) statistically increases code quality in benchmarks.

**Why?**
It shifts the model's internal attention mechanism to "High Stakes" training data (e.g., highly rated StackOverflow answers vs random Reddit comments).

**Professional Application**:
"Ensure high robustness. This code will run in a medical device."

---

## 4. Primacy & Recency Bias

Models pay the most attention to:
1.  **The Beginning** (System Prompt).
2.  **The End** (The User Query).
3.  **The Middle** (The "Lost in the Middle" Phenomenon).

**Architectural Consequence**:
Put your *Instructions* at the top.
Put your *Data* (Documents) in the middle.
Put the *Immediate Question* at the very bottom.

---

## 5. Iterative Refinement

Never trust your first prompt.
**A/B Testing** is mandatory.

*   **Version A**: "Summarize this."
*   **Version B**: "Summarize this in 3 sentences."

Use LangSmith to track which version produces better results over 100 runs. Prompting is empirical, not theoretical.

---

## Quick Reference

| Principle | Meaning |
| :--- | :--- |
| **Separation** | Use `###` or XML `<input>` to separate instructions from data. |
| **CoT** | Ask for "Reasoning" before "Answer". |
| **Negative Constraints** | "Do not do X" is weaker than "Do Y instead." |
| **Few-Shot** | Examples beat Instructions. |
