| **Subtopic** | **Focus & Purpose** | **Key Concepts / Details** | **One-Line Recall** |
|---|---|---|---|
| **[[WP3.3.3.1 Create or Update Logic]]** | Smart saving | Automatic fallback: adds if missing, updates if exists | The safest way to save data without checking existence. |
| **[[WP3.3.3.2 The 'prev_value' Argument]]** | Creating vs Updating | Targeting specific values when multiple exist | Change only the 'blue' mood to 'red'. |
| **[[WP3.3.3.3 Return Values]]** | Understanding outcomes | Returns `true` if updated, `false` if unchanged (same value) | Returns false if you update with the exact same value. |
| **[[WP3.3.3.4 Escaping Before Save]]** | Security best practices | `sanitize_text_field()`, `sanitize_meta()` usage | Always clean data before putting it in the DB. |
| **[[WP3.3.3.5 Deleting via Update]]** | Clearing values | Setting to empty string (sometimes) vs `delete_post_meta` | Don't use update to delete; use the proper delete function. |
