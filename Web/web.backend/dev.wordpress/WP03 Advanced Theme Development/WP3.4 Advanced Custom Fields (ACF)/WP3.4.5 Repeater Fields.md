| **Subtopic** | **Focus & Purpose** | **Key Concepts / Details** | **One-Line Recall** |
|---|---|---|---|
| **[[WP3.4.5.1 The Repeater Field]]** | Repeating data sets | Adding unlimited rows of sub-fields (e.g., Sliders, Team Members) | A dynamic list of items. |
| **[[WP3.4.5.2 Sub-Fields]]** | The inner data | Fields defined inside the repeater row | The columns of your repeater table. |
| **[[WP3.4.5.3 Template Loop]]** | Displaying data | `if(have_rows())`, `while(have_rows()) : the_row()`, `get_sub_field()` | Standard WordPress Loop pattern, but for ACF data. |
| **[[WP3.4.5.4 Nested Repeaters]]** | Complex hierarchies | A repeater inside a repeater (e.g., Ingredients inside Steps) | Creating deep data structures (use carefully). |
| **[[WP3.4.5.5 Performance Warning]]** | Database impact | High number of rows = high number of meta entries | Lots of rows can slow down the edit screen. |
