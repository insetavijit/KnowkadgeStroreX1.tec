|**Subtopic**|**Focus & Purpose**|**Key Concepts / Details**|**One-Line Recall**|
|---|---|---|---|
|**[[WP2.7.3.1 Why Avoid]]**|Understand problems|Modifies main query, causes issues, anti-pattern|query_posts() modifies the main query destructively.|
|**[[WP2.7.3.2 Main Query Issues]]**|See the problems|Breaks conditionals, pagination issues, side effects|query_posts breaks themes in subtle ways.|
|**[[WP2.7.3.3 Proper Alternatives]]**|Use correct methods|WP_Query for secondary, pre_get_posts for main|Use WP_Query or pre_get_posts instead.|
|**[[WP2.7.3.4 pre_get_posts Hook]]**|Modify main query properly|pre_get_posts action, modify main query safely|pre_get_posts modifies main query correctly.|
|**[[WP2.7.3.5 Legacy Code]]**|Handle existing|Recognize in old themes, how to refactor, migration|Refactor query_posts() when found in old code.|
