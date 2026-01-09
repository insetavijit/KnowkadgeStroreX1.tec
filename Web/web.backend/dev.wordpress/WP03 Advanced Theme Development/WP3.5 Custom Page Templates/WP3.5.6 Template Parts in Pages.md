| **Subtopic** | **Focus & Purpose** | **Key Concepts / Details** | **One-Line Recall** |
|---|---|---|---|
| **[[WP3.5.6.1 get_template_part()]]** | Modularity | Including re-usable chunks (`content-page.php`) | Don't rewrite the loop; include it. |
| **[[WP3.5.6.2 Passing Arguments]]** | Advanced inclusion | Passing data to parts (WP 5.5+ feature) | Send specific variables into your partial. |
| **[[WP3.5.6.3 get_header/footer variants]]** | Custom wrappers | `get_header( 'shop' )` loads `header-shop.php` | Different nav bars for different sections of the site. |
| **[[WP3.5.6.4 Loop Isolation]]** | Code hygiene | Keeping the main template file clean | Put the heavy logic in a partial or function. |
| **[[WP3.5.6.5 DRY Principle]]** | Best practice | "Don't Repeat Yourself" – share code with `page.php` | Inherit as much as possible, change only what's needed. |
