| **Subtopic** | **Focus & Purpose** | **Key Concepts / Details** | **One-Line Recall** |
|---|---|---|---|
| **[[WP3.6.1.1 The Concept]]** | Triggering vs Modifying | "Do something at this point" vs "Change this piece of data" | Actions do not return values; Filters must return values. |
| **[[WP3.6.1.2 Actions (Events)]]** | Execution points | `wp_head`, `save_post`, `init` | Hooks that fire at specific times during page load. |
| **[[WP3.6.1.3 Filters (Data)]]** | Transformation | `the_content`, `body_class`, `excerpt_length` | Hooks that pass data through your function to change it. |
| **[[WP3.6.1.4 Syntax Difference]]** | Code structure | `do_action()` calls flow; `apply_filters()` assigns variables | You `echo` in an action; you `return` in a filter. |
| **[[WP3.6.1.5 When to use which?]]** | Decision making | Inserting HTML (Action) vs changing text (Filter) | If you need to print output, use Action. If you need to change a string, use Filter. |
