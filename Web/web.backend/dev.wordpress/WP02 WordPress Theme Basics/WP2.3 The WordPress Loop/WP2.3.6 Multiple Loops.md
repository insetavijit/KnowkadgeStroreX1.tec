|**Subtopic**|**Focus & Purpose**|**Key Concepts / Details**|**One-Line Recall**|
|---|---|---|---|
|**[[WP2.3.6.1 Running Multiple Loops]]**|Use secondary queries|WP_Query for second Loop, different content sections|Use WP_Query for additional Loops.|
|**[[WP2.3.6.2 Resetting Queries]]**|Clean up after Loop|wp_reset_postdata(), restore global $post, avoid conflicts|Always reset after custom queries.|
|**[[WP2.3.6.3 wp_reset_postdata()]]**|Restore post data|After custom WP_Query, restores main query post|Call wp_reset_postdata() after WP_Query loops.|
|**[[WP2.3.6.4 Secondary Queries]]**|Create custom queries|new WP_Query($args), custom post retrieval, sidebar queries|Secondary queries use new WP_Query.|
|**[[WP2.3.6.5 Loop Management]]**|Organize multiple Loops|Main vs secondary, proper reset, avoiding issues|Manage Loops carefully to avoid conflicts.|
