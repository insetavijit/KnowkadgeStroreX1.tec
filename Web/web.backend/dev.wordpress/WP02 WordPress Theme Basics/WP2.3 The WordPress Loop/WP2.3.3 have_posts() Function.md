|**Subtopic**|**Focus & Purpose**|**Key Concepts / Details**|**One-Line Recall**|
|---|---|---|---|
|**[[WP2.3.3.1 Checking for Posts]]**|Test availability|Returns true/false, checks remaining posts, query status|have_posts() checks if posts exist in query.|
|**[[WP2.3.3.2 Boolean Return]]**|Understand return|Returns true if posts remain, false when exhausted|have_posts() returns boolean true or false.|
|**[[WP2.3.3.3 Query Status]]**|Check query|Checks global $wp_query, current_post vs post_count|have_posts() compares current post to total.|
|**[[WP2.3.3.4 Usage Patterns]]**|Apply correctly|Loop condition, before Loop check, conditional display|Use have_posts() as Loop condition.|
|**[[WP2.3.3.5 No Posts Handling]]**|Handle empty|else clause, no posts found message, empty query|Handle no posts with else in Loop.|
