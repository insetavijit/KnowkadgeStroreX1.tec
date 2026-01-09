| **Subtopic** | **Focus & Purpose** | **Key Concepts / Details** | **One-Line Recall** |
|---|---|---|---|
| **[[WP3.2.7.1 Naming Conventions]]** | Code standards | Singular vs Plural keys, prefixes (`acme_genre`) | Prefix your taxonomy keys to avoid collisions. |
| **[[WP3.2.7.2 Reserved Terms]]** | Avoiding conflicts | ‘tag’, ‘cat’, ‘date’, list of forbidden slugs | Don't name a taxonomy something WordPress uses. |
| **[[WP3.2.7.3 Term Caching]]** | Performance optimization | `update_term_meta_cache`, avoiding N+1 queries | Efficiently loading terms for lists of posts. |
| **[[WP3.2.7.4 Deletion Safety]]** | Managing data removal | What happens to posts when terms are deleted? | Terms vanish, but posts stay (default behavior). |
| **[[WP3.2.7.5 Translation Readiness]]** | i18n for Taxonomies | Translating labels and rewrite slugs (carefully) | Ensure all UI labels are wrapped in `__()`. |
