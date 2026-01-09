| **Subtopic** | **Focus & Purpose** | **Key Concepts / Details** | **One-Line Recall** |
|---|---|---|---|
| **[[WP3.6.5.1 Creating Actions]]** | Defining events | Placing `do_action( 'my_theme_header' )` in templates | Letting others insert code into your theme without editing files. |
| **[[WP3.6.5.2 Creating Filters]]** | Allow modification | `apply_filters( 'my_theme_copyright', $text )` | Making your hardcoded text changeable by child themes. |
| **[[WP3.6.5.3 Naming Custom Hooks]]** | Best practices | Prefixing (`acme_before_content`) | Descriptive names help other developers find insertion points. |
| **[[WP3.6.5.4 Documentation]]** | Inline docs | Describing arguments `do_action( ... $post_id )` | Tell developers what data they have access to. |
| **[[WP3.6.5.5 Pluggable Themes]]** | Framework thinking | Building a theme that is meant to be extended | The difference between a simple theme and a framework. |
