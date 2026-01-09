| **Subtopic** | **Focus & Purpose** | **Key Concepts / Details** | **One-Line Recall** |
|---|---|---|---|
| **[[WP3.3.1.1 The wp_postmeta Table]]** | Database structure | `meta_id`, `post_id`, `meta_key`, `meta_value` columns | A vertical table storing extra data for posts. |
| **[[WP3.3.1.2 Key-Value Pairs]]** | Data model basics | One key can have multiple values (unless restricted) | Like a dictionary or hash map for your content. |
| **[[WP3.3.1.3 Hidden Meta Keys]]** | UI privacy | Underscore prefix (`_price`), hiding from "Custom Fields" box | Prefixing a key with `_` hides it from the user. |
| **[[WP3.3.1.4 Meta vs Taxonomies]]** | Architectural choice | Meta for specific data (price), Tax for grouping (brand) | Use meta for unique attributes, tax for sorting. |
| **[[WP3.3.1.5 Performance Considerations]]** | Database impact | Non-indexed values, expensive text searches on meta | Meta queries are slower than taxonomy queries. |
