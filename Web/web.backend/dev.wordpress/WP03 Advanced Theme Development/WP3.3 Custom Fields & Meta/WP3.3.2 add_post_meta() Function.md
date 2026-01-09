| **Subtopic** | **Focus & Purpose** | **Key Concepts / Details** | **One-Line Recall** |
|---|---|---|---|
| **[[WP3.3.2.1 Basic Usage]]** | Adding new data | Function args: `$post_id`, `$meta_key`, `$meta_value` | Attaches a piece of data to a post ID. |
| **[[WP3.3.2.2 The 'unique' Parameter]]** | Preventing duplicates | Fourth argument (`true`/`false`), ensuring single values | Set to `true` to ensure only one value exists per key. |
| **[[WP3.3.2.3 Multiple Values per Key]]** | Storing lists | Default behavior allowing multiple rows for one key | You can have multiple 'mood' entries for one post. |
| **[[WP3.3.2.4 Return Values]]** | Error checking | Returns `meta_id` on success, `false` on failure | Check the return to see if the save worked. |
| **[[WP3.3.2.5 Bulk Adding]]** | Loops and imports | looping through arrays to add multiple meta fields | Efficiently adding initial data to posts. |
