| **Subtopic** | **Focus & Purpose** | **Key Concepts / Details** | **One-Line Recall** |
|---|---|---|---|
| **[[WP3.3.4.1 Single vs Array Return]]** | The `$single` argument | `true` returns value, `false` returns array of values | Always set the third arg to `true` for single values. |
| **[[WP3.3.4.2 Fetching All Meta]]** | Debugging and export | Omitting `$key` returns associative array of all meta | Get every piece of meta data for a post at once. |
| **[[WP3.3.4.3 Handling Missing Keys]]** | Preventing errors | Returns empty string (single) or empty array (multiple) | Always check `if ( ! empty() )` before output. |
| **[[WP3.3.4.4 Contextual Usage]]** | Where to use it | Inside the Loop vs outside (passing IDs) | Works anywhere as long as you have the Post ID. |
| **[[WP3.3.4.5 Caching Behavior]]** | Performance notes | WordPress caches all meta for a post on first load | Multiple calls for different keys don't hit the DB again. |
