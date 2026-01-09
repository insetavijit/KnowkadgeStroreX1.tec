| **Subtopic** | **Focus & Purpose** | **Key Concepts / Details** | **One-Line Recall** |
|---|---|---|---|
| **[[WP3.2.1.1 The register_taxonomy() Function]]** | Core registration logic | Function signature, `$taxonomy`, `$object_type`, `$args` | The primary function to create new groupings. |
| **[[WP3.2.1.2 Hooking to 'init']]** | Correct timing for registration | `add_action('init', ...)` necessity, preventing errors | Always register taxonomies on the init hook. |
| **[[WP3.2.1.3 Connecting to Post Types]]** | Associating tax with content | `register_taxonomy_for_object_type()` vs `$object_type` array | Decides which content types get this taxonomy. |
| **[[WP3.2.1.4 Taxonomy Keys]]** | Naming the taxonomy | Unique string identifiers, length limits (32 chars) | The internal database name for your group. |
| **[[WP3.2.1.5 Verification & Troubleshooting]]** | Checking if it works | `taxonomy_exists()`, debugging registration placement | Confirming your code actually created the tax. |
