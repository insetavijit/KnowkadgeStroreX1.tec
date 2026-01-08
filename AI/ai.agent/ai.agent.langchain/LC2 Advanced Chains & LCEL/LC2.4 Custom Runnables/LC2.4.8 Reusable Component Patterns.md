| **Subtopic**                                          | **Focus & Purpose**                          | **Key Concepts / Details**                                                      | **One-Line Recall**                                                 |
| ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **[[LC2.4.8.1 Designing Reusable Runnables]]**        | Create shareable components                  | Single purpose, clear interfaces, documentation                                 | Design runnables for reuse across projects.                         |
| **[[LC2.4.8.2 Parameterization]]**                    | Make runnables configurable                  | Constructor parameters, configuration options, flexibility                      | Parameterize runnables for flexible reuse.                          |
| **[[LC2.4.8.3 Configuration Options]]**               | Support runtime config                       | Config parameters, environment settings, defaults                               | Support configuration for varied use cases.                         |
| **[[LC2.4.8.4 Documentation]]**                       | Document components                          | Docstrings, examples, type hints, usage guides                                  | Document runnables for team sharing.                                |
| **[[LC2.4.8.5 Sharing Components]]**                  | Distribute runnables                         | Package creation, internal libraries, open source                               | Package runnables as reusable libraries.                            |

# Reusable Component Patterns: Building a Library

The goal of creating custom Runnables is not just for one project. It's to build **Shareable Components**.

---

## 1. Designing for Reuse

**Single Responsibility**: A runnable should do *one thing well*.
*   Good: `SentimentScorer`, `SQLValidator`, `PDFExtractor`.
*   Bad: `DoEverythingChain`.

**Clear Interface**: Use explicit types.
*   `Runnable[str, SentimentResult]` is clearer than `Runnable[Any, Any]`.

---

## 2. Parameterization (Constructor)

Hard-coded values are the enemy of reuse.

```python
# Bad: Hard-coded
class MyRetriever(Runnable):
    def __init__(self):
        self.k = 5

# Good: Configurable
class MyRetriever(Runnable):
    def __init__(self, k: int = 5, threshold: float = 0.8):
        self.k = k
        self.threshold = threshold
```

---

## 3. Packaging for Distribution

If your custom runnables are useful across many projects, package them.

```
my_ai_components/
├── __init__.py
├── retrievers/
│   └── hybrid_retriever.py
├── parsers/
│   └── citation_parser.py
└── setup.py
```

Then install via `pip install my_ai_components`.

---

## 4. Documentation

Every reusable runnable needs:
1.  **Docstring**: What does it do?
2.  **Type Hints**: What does it accept/return?
3.  **Example**: How do I use it?

```python
class SentimentScorer(Runnable[str, float]):
    """
    Scores sentiment of input text on a -1 to 1 scale.
    
    Example:
        >>> scorer = SentimentScorer()
        >>> scorer.invoke("I love this!") 
        0.95
    """
```

---

## Quick Reference

| Principle | Action |
| :--- | :--- |
| **Single Purpose** | One class = one job. |
| **Parameterization** | Pass config in `__init__`. |
| **Clear Types** | `Runnable[In, Out]` generics. |
| **Documentation** | Docstrings + Examples. |
