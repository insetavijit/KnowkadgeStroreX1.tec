| **Subtopic** | **Focus & Purpose** | **Key Concepts / Details** | **One-Line Recall** |
|---|---|---|---|
| **[[WP3.6.4.1 The Integer Scale]]** | Ordering logic | 1 runs before 10; 10 runs before 100 | Low numbers = First; High numbers = Last. |
| **[[WP3.6.4.2 Default Priority]]** | Standard behavior | If omitted, priority is 10 | Most plugins use 10, so use 11 to override them. |
| **[[WP3.6.4.3 Negative Priorities]]** | Extreme early execution | Using -1 or 0 to ensure running first | Use for critical setup that others depend on. |
| **[[WP3.6.4.4 PHP_INT_MAX]]** | The absolute end | Ensuring your code runs absolutely last | Use when you must override everything else. |
| **[[WP3.6.4.5 Troubleshooting Order]]** | Debugging conflicts | Using 'Query Monitor' to see hook firing order | Figuring out why your change isn't showing up. |
