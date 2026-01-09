| **Subtopic** | **Focus & Purpose** | **Key Concepts / Details** | **One-Line Recall** |
|---|---|---|---|
| **[[WP3.7.2.1 Outputting Widgets]]** | Frontend display | `dynamic_sidebar( 'id-here' )` placement in templates | Printing the bucket's contents to the page. |
| **[[WP3.7.2.2 Conditional Checks]]** | Handling empty areas | `is_active_sidebar()`, hiding wrapper divs if empty | Don't print an empty `<div>` if there are no widgets. |
| **[[WP3.7.2.3 Default/Fallback Content]]** | Backward compatibility | Code inside the `if` check (runs if NO widgets exist) | Show a hardcoded menu if the user hasn't added widgets. |
| **[[WP3.7.2.4 Template Logic]]** | Integration | Placing in `sidebar.php`, `footer.php`, not just sidebars | Putting widget areas anywhere in your HTML structure. |
| **[[WP3.7.2.5 Return Values]]** | Debugging | Returns true/false based on success | Check if the sidebar actually loaded. |
