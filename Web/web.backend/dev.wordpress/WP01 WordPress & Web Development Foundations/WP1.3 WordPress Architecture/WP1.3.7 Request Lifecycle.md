| **Subtopic** | **Focus & Purpose** | **Key Concepts / Details** | **One-Line Recall** |
| :--- | :--- | :--- | :--- |
| **[[WP1.3.7.1 Index.php Initialization]]** | Starting line | All non-admin requests hit root index.php; defines WP_USE_THEMES. | It all starts at index.php. |
| **[[WP1.3.7.2 Loading Core]]** | Bootup | wp-blog-header.php -> wp-load.php -> wp-config.php -> wp-settings.php. | WordPress loads its brain before its face. |
| **[[WP1.3.7.3 Parsing the Query]]** | Interpretation | $wp->parse_request(); URL analysis; determining what content is requested. | WordPress figures out what URL you typed. |
| **[[WP1.3.7.4 Querying the Database]]** | Fetching content | WP_Query gets data from the DB based on the parsed request. | WordPress grabs the right posts from the DB. |
| **[[WP1.3.7.5 Loading the Template]]** | Presentation | Template Loader finds correct theme file; The Loop outputs content; response sent. | WordPress picks a template to show the content. |
