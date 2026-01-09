| **Subtopic** | **Focus & Purpose** | **Key Concepts / Details** | **One-Line Recall** |
|---|---|---|---|
| **[[WP3.1.4.1 The 'capability_type' Argument]]** | Setting basic permission models | Defaults ('post', 'page'), how it maps to primitive caps | Decides if permissions behave like Posts or Pages. |
| **[[WP3.1.4.2 Meta Capabilities Logic]]** | Understanding granular permissions | `edit_post`, `read_post`, `delete_post` distinctions | The specific actions a user can take on a single item. |
| **[[WP3.1.4.3 The 'map_meta_cap' Argument]]** | Automating capability mapping | `true` vs `false` (default), mapping meta to primitive caps | Let WordPress handle the complex permission logic automatically. |
| **[[WP3.1.4.4 Custom Capabilities Mapping]]** | Creating custom permission sets | The `capabilities` array, defining unique strings (e.g., `edit_books`) | Fully distinct permissions separate from standard Posts. |
| **[[WP3.1.4.5 Role Management for CPTs]]** | Granting access to users | `add_cap()`, `remove_cap()`, plugins for role management | Tying your custom capabilities to user roles. |
