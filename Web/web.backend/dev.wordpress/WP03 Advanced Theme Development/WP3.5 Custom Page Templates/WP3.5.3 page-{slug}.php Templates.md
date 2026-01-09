| **Subtopic** | **Focus & Purpose** | **Key Concepts / Details** | **One-Line Recall** |
|---|---|---|---|
| **[[WP3.5.3.1 Automatic Targeting]]** | No selection needed | Naming file `page-about.php` targets `/about/` URL | WordPress automatically matches the file to the slug. |
| **[[WP3.5.3.2 page-{ID}.php]]** | ID based targeting | `page-42.php` targets post ID 42 | Targets a specific page ID (rarely used, hard to read). |
| **[[WP3.5.3.3 Pros & Cons]]** | When to use | Easy setup vs Fragile (breaks if slug changes) | Great for 'Contact' or 'Home', risky for others. |
| **[[WP3.5.3.4 Hierarchy Position]]** | Order of operations | Custom Template > `page-{slug}` > `page-{id}` > `page.php` | Selected template beats slug-based template. |
| **[[WP3.5.3.5 Dynamic Body Classes]]** | CSS hook | `page-template-default` vs `page-template-about` | Styling specific pages without custom templates. |
