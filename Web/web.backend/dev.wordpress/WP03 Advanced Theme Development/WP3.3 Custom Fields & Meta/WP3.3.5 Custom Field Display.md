| **Subtopic** | **Focus & Purpose** | **Key Concepts / Details** | **One-Line Recall** |
|---|---|---|---|
| **[[WP3.3.5.1 Sanitization on Output]]** | Security (XSS prevention) | `esc_html()`, `esc_url()`, `esc_attr()` | Never echo raw database content to the screen. |
| **[[WP3.3.5.2 Conditional Display]]** | Hiding empty fields | `if ( $value ) { echo ... }` logic | Don't print the "Price:" label if the price is missing. |
| **[[WP3.3.5.3 formatting Meta Data]]** | Presentation | `number_format()`, `date()`, `nl2br()` for text areas | Convert raw DB strings into readable HTML. |
| **[[WP3.3.5.4 Shortcodes for Meta]]** | User-generated content | Creating a shortcode to display a meta field | Allow users to insert custom fields in post content. |
| **[[WP3.3.5.5 The 'the_meta()' Function]]** | Legacy/Debug display | Automatically listing all keys/values (rarely used now) | A quick way to dump all custom fields (mostly for testing). |
