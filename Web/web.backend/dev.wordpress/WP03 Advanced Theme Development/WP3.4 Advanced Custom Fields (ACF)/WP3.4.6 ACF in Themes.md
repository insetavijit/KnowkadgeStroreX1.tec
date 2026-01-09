| **Subtopic** | **Focus & Purpose** | **Key Concepts / Details** | **One-Line Recall** |
|---|---|---|---|
| **[[WP3.4.6.1 get_field() vs the_field()]]** | Retrieval vs Echo | Storing in variable vs printing directly | `the_field` echoes, `get_field` returns. |
| **[[WP3.4.6.2 Return Formats]]** | Data types matter | Image Array vs ID vs URL; Post Object vs ID | Know what the function returns before you use it. |
| **[[WP3.4.6.3 Working with Images]]** | Best practice display | Using Image Array + `wp_get_attachment_image()` | Always use the ID or Array to get proper `scrset`. |
| **[[WP3.4.6.4 Debugging]]** | Viewing raw data | `var_dump()` or `print_r()` on `get_field()` | When in doubt, print the array to see the structure. |
| **[[WP3.4.6.5 Options Pages]]** | Site-wide data | `get_field('name', 'option')` global retrieval | Getting footer data or global settings. |
