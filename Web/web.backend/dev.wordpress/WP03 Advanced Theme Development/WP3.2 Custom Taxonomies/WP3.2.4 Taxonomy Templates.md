| **Subtopic** | **Focus & Purpose** | **Key Concepts / Details** | **One-Line Recall** |
|---|---|---|---|
| **[[WP3.2.4.1 Template Hierarchy for Taxonomies]]** | Understanding file priority | Order: `taxonomy-{tax}-{term}`, `taxonomy-{tax}`, `taxonomy.php`, `archive` | Logic for choosing the term archive file. |
| **[[WP3.2.4.2 taxonomy-{taxonomy}.php]]** | Targeting a specific taxonomy | Creating a layout for "Genres" generally | The generic template for all terms in a tax. |
| **[[WP3.2.4.3 taxonomy-{taxonomy}-{term}.php]]** | Targeting a specific term | Layout for "Genre: Horror" specifically | A specialized layout for a single term. |
| **[[WP3.2.4.4 Displaying Term Meta]]** | Showing descriptions | `term_description()`, `single_term_title()`, generic archive functions | Outputting the term's title and bio. |
| **[[WP3.2.4.5 Conditional Tags for Taxonomies]]** | Logic checks in code | `is_tax()`, `is_category()`, `is_tag()` | checking if the user is viewing a term page. |
