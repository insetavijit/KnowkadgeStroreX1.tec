| **Subtopic** | **Focus & Purpose** | **Key Concepts / Details** | **One-Line Recall** |
|---|---|---|---|
| **[[WP3.7.1.1 The Function]]** | Initialization | Hooking to `widgets_init`, defining the ID and Name | The command to create a drop zone for widgets. |
| **[[WP3.7.1.2 Arguments Array]]** | Configuration | `name`, `id` (must be unique), `description` (shows in admin) | Controls how the sidebar is labeled in the backend. |
| **[[WP3.7.1.3 Wrapper HTML]]** | Markup control | `before_widget` / `after_widget`, `before_title` | Defining the HTML tags that wrap every widget. |
| **[[WP3.7.1.4 Multiple Registration]]** | scalability | `register_sidebars( $n )` vs individual calls | Creating "Footer 1" through "Footer 4" dynamically. |
| **[[WP3.7.1.5 Context]]** | Limitations | Only works in themes (and some plugins); creates the container, not content | It builds the bucket; users fill it with water. |
