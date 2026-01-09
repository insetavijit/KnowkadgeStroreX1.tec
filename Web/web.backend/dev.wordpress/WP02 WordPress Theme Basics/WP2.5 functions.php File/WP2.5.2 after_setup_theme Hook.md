|**Subtopic**|**Focus & Purpose**|**Key Concepts / Details**|**One-Line Recall**|
|---|---|---|---|
|**[[WP2.5.2.1 Hook Purpose]]**|Understand timing|Fires after theme loaded, before init, setup timing|after_setup_theme fires when theme loads.|
|**[[WP2.5.2.2 Initialization Timing]]**|Know sequence|Before headers, early in load, feature registration time|Use after_setup_theme for early setup.|
|**[[WP2.5.2.3 Registering Features]]**|Set up theme|add_theme_support, register_nav_menus, content_width|Register theme features on this hook.|
|**[[WP2.5.2.4 Setup Best Practices]]**|Follow standards|Single callback, organized code, named function|Use one well-organized setup function.|
|**[[WP2.5.2.5 Hook Priority]]**|Control timing|Priority parameter, load order, plugin compatibility|Default priority is 10; adjust if needed.|
