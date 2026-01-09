| **Subtopic** | **Focus & Purpose** | **Key Concepts / Details** | **One-Line Recall** |
|---|---|---|---|
| **[[WP3.3.7.1 Individual Keys]]** | Query-friendly storage | Storing one value per row (e.g. `price`) | Use when you need to order or filter by this value. |
| **[[WP3.3.7.2 Serialized Arrays]]** | Compact storage | Storing an entire array in one row (autopackaged) | Use for settings/lots of data that doesn't need querying. |
| **[[WP3.3.7.3 JSON Storage]]** | Modern compact storage | `json_encode()` manually, interoperability | Better than serialization for external app usage. |
| **[[WP3.3.7.4 Underscore Prefixing]]** | System vs User meta | `_my_key` vs `my_key` distinctions | Always prefix meta internal to your plugin logic. |
| **[[WP3.3.7.5 Cleaning Up (Uninstall)]]** | Data hygiene | Deleting meta when plugin is uninstalled | Don't leave orphan data in the DB forever. |
