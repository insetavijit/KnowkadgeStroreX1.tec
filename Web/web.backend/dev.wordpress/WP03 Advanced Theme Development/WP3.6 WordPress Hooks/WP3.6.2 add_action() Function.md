| **Subtopic** | **Focus & Purpose** | **Key Concepts / Details** | **One-Line Recall** |
|---|---|---|---|
| **[[WP3.6.2.1 Formatting]]** | Syntax | `add_action( 'hook', 'callback', priority, args )` | The standard way to hook a function to an event. |
| **[[WP3.6.2.2 The Callback]]** | The worker function | Naming functions, using class methods `array($this, 'method')` | The actual code that runs when the hook fires. |
| **[[WP3.6.2.3 Priority Level]]** | Timing control | Default is 10; Lower runs earlier, Higher runs later | Use priority to insert content exactly where you want it. |
| **[[WP3.6.2.4 Argument Count]]** | Passing data | Defining how many arguments your callback accepts | If the hook passes 3 variables, set the 4th arg to 3. |
| **[[WP3.6.2.5 Anonymous Functions]]** | Closures | Using `function(){}` directly in the hook (hard to unhook) | Quick one-off logic, but bad for extensibility. |
