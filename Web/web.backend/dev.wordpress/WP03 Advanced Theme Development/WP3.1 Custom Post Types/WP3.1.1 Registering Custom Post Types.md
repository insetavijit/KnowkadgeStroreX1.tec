| **Subtopic** | **Focus & Purpose** | **Key Concepts / Details** | **One-Line Recall** |
|---|---|---|---|
| **[[WP3.1.1.1 The register_post_type() Function]]** | Understand the core function for creating CPTs | Function signature, necessary parameters, return values | The foundational internal function for custom content. |
| **[[WP3.1.1.2 The init Hook]]** | Learn the correct execution timing | `add_action('init', ...)` importance, avoiding early firing errors | Registration must happen during the `init` sequence. |
| **[[WP3.1.1.3 Unique Post Type Keys]]** | Naming rules and best practices | Max 20 characters, creating unique keys, reserved terms | Short, unique naming prevents conflicts. |
| **[[WP3.1.1.4 Basic Supports & Features]]** | enabling default WordPress features | `supports` array, title, editor, thumbnails, excerpts | Turn on standard editor features for your type. |
| **[[WP3.1.1.5 Troubleshooting Registration]]** | Debugging common registration issues | Permalinks flushing, visibility checks, error logging | Fixes specific to CPT setup (like 404s). |
