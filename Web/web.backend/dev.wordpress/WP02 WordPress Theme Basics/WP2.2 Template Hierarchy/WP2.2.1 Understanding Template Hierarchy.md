|**Subtopic**|**Focus & Purpose**|**Key Concepts / Details**|**One-Line Recall**|
|---|---|---|---|
|**[[WP2.2.1.1 Hierarchy Concept]]**|Grasp the core idea|Template selection logic, most-specific-first, fallback chain|WordPress finds the most specific matching template.|
|**[[WP2.2.1.2 Decision Tree]]**|Understand flow|Query type → template search → fallback → index.php|The hierarchy is a decision tree from specific to general.|
|**[[WP2.2.1.3 Query-Based Selection]]**|Connect queries to templates|URL → query → template type, WP_Query determines template|Queries determine which template hierarchy to use.|
|**[[WP2.2.1.4 Hierarchy Logic]]**|Master the rules|Naming patterns, slug matching, ID matching, type matching|Hierarchy checks slug, then ID, then type, then fallback.|
|**[[WP2.2.1.5 Core Mechanism]]**|Know internals|template-loader.php, locate_template(), get_query_template()|WordPress uses template-loader.php to find templates.|
