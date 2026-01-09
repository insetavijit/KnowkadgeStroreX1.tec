| **Subtopic** | **Focus & Purpose** | **Key Concepts / Details** | **One-Line Recall** |
|---|---|---|---|
| **[[WP3.6.6.1 remove_action/filter]]** | Unhooking | Removing default WP or Plugin behavior | Disabling features you don't want. |
| **[[WP3.6.6.2 Removal Requirements]]** | Exact match | Priority and callback must match exactly to remove | You must know the exact priority used to add it. |
| **[[WP3.6.6.3 Unhooking Classes]]** | Complexity | Accessing the class instance to remove its method | Removing hooks inside objects is harder than functions. |
| **[[WP3.6.6.4 has_action()]]** | Conditional checking | Checking if a hook has any functions attached | Check if something is hooked before doing something. |
| **[[WP3.6.6.5 current_action()]]** | Context awareness | Determining which hook is currently firing | Useful in reusable functions to know where they are running. |
