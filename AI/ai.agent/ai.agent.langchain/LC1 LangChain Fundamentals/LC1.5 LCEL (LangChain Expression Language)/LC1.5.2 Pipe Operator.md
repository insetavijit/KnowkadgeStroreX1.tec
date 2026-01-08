| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC1.5.2.1 Using the Pipe Operator]]**             | Chain components with \|                      | \| syntax, left-to-right flow, operator overloading                            | Use \| to pipe output of one component into the next.              |
| **[[LC1.5.2.2 Chaining Runnables]]**                  | Connect multiple runnables                   | Runnable A \| Runnable B, chain of operations                                    | Chain runnables together using the pipe operator.                   |
| **[[LC1.5.2.3 Left to Right Data Flow]]**             | Understand execution direction               | Input → Component1 → Component2 → Output                                        | Data flows left-to-right through piped components.                  |
| **[[LC1.5.2.4 Reading LCEL Expressions]]**            | Parse LCEL syntax visually                   | Breaking down expressions, identifying components, tracing flow                 | Read LCEL expressions as data flowing through pipes.                |
| **[[LC1.5.2.5 Pipe Syntax Patterns]]**                | Apply common patterns                        | Common idioms, formatting conventions, multiline expressions                    | Follow established patterns for clean LCEL syntax.                  |

# The Pipe Operator (`|`): Architectural Grammar

The vertical bar `|` (Bitwise OR) is overloaded in LangChain to mean **"Compose"**.
It automatically wraps the left and right operands into a `RunnableSequence`.

---

## 1. Syntax Mechanics

When Python sees `A | B`, it calls `A.__or__(B)`.
In LangChain, this method does one thing:
1.  Verify `A` is a `Runnable`.
2.  Verify `B` is a `Runnable`.
3.  Return `RunnableSequence(first=A, last=B)`.

**The Associative Property**:
`A | B | C` is semantically equivalent to `((A | B) | C)` or `(A | (B | C))`.
The result is a flattened list of steps: `[A, B, C]`.

---

## 2. Type Covariance (The Invisible Hand)

For `A | B` to work, the **Output Type** of A must match the **Input Type** of B.

| Component A | Output Type | Component B | Input Type | Valid? |
| :--- | :--- | :--- | :--- | :--- |
| `Prompt` | `PromptValue` | `LLM` | `PromptValue` | ✅ Yes |
| `LLM` | `AIMessage` | `StrOutputParser` | `Message` | ✅ Yes |
| `LLM` | `AIMessage` | `Prompt` | `Dict` | ❌ **CRASH** |

**The most common crash**:
Trying to pipe a Model (which outputs a Message object) directly into a Prompt (which expects a Dictionary).
**Fix**: `model | JsonOutputParser() | next_prompt`.

---

## 3. Coercion (The "Auto-Wrap" Magic)

LangChain is forgiving. If you pipe something that isn't a Runnable, it tries to coerced it.

### Function Coercion
```python
# You write this:
chain = prompt | model | (lambda x: x.upper())

# LangChain compiles this:
chain = prompt | model | RunnableLambda(lambda x: x.upper())
```

### Dictionary Coercion
```python
# You write this:
chain = {"context": retriever, "q": RunnablePassthrough()} | prompt

# LangChain compiles this:
chain = RunnableParallel({"context": retriever, "q": RunnablePassthrough()}) | prompt
```

This grammar makes LCEL code extremely concise compared to usage of the explicit classes.

---

## 4. Multi-Line Formatting

For complex chains, do not write one long line. Use parentheses to verify indentation.

```python
# Professional Style
chain = (
    {"context": retriever, "question": RunnablePassthrough()}
    | prompt
    | model
    | StrOutputParser()
)
```

**Debug Tip**:
If you get `TypeError: unsupported operand type(s) for |`, it usually means you forgot to instantiate a class.
*   **Wrong**: `PromptTemplate | ChatOpenAI` (Class types)
*   **Right**: `PromptTemplate(...) | ChatOpenAI(...)` (Instances)

---

## Quick Reference

| Symbol | Meaning | Underlying Class |
| :--- | :--- | :--- |
| `\|` | Sequence | `RunnableSequence` |
| `{ k: v }` | Parallel | `RunnableParallel` |
| `func` | Transformation | `RunnableLambda` |
