|**Subtopic**|**Focus & Purpose**|**Key Concepts / Details**|**One-Line Recall**|
|---|---|---|---|
|**[[WP2.7.6.1 WP_Query Loop]]**|Loop with WP_Query|$query->have_posts(), $query->the_post(), standard Loop|Loop through WP_Query with while structure.|
|**[[WP2.7.6.2 foreach with get_posts]]**|Loop with array|foreach ($posts as $post), setup_postdata, simple iteration|Use foreach with get_posts array.|
|**[[WP2.7.6.3 Query Iteration]]**|Iterate correctly|While vs foreach, choosing method, post setup|Choose loop style based on use case.|
|**[[WP2.7.6.4 Proper Reset]]**|Reset after query|wp_reset_postdata(), restore global $post, essential|Always reset after custom queries.|
|**[[WP2.7.6.5 Nested Loops]]**|Handle nested queries|Multiple queries, proper reset between, scope|Reset between nested query loops.|
