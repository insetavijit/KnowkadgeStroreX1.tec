| **Subtopic** | **Focus & Purpose** | **Key Concepts / Details** | **One-Line Recall** |
|---|---|---|---|
| **[[WP3.6.3.1 The Golden Rule]]** | Avoiding breakage | ALWAYS return the data variable | If you don't return the value, the data disappears. |
| **[[WP3.6.3.2 Chaining Filters]]** | Sequential modification | Pipeline pattern; output of one is input of next | Multiple plugins can modify the same title one after another. |
| **[[WP3.6.3.3 Modifying Arguments]]** | Contextual data | Using extra arguments to decide how to filter | Only change the title if it's in the 'News' category. |
| **[[WP3.6.3.4 Priority in Filters]]** | Order of change | Who gets the last word? (Higher priority = last overwrite) | The function with separate priority 99 overrides priority 10. |
| **[[WP3.6.3.5 Common Filters]]** | Frequent use cases | `the_content`, `the_title`, `body_class` | The standard touchpoints for theme customization. |
