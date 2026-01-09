| **Subtopic** | **Focus & Purpose** | **Key Concepts / Details** | **One-Line Recall** |
|---|---|---|---|
| **[[WP3.3.6.1 add_meta_box()]]** | Registering the UI container | ID, Title, Callback, Screen, Context, Priority | Creates the white box in the post editor screen. |
| **[[WP3.3.6.2 The Callback Function]]** | Rendering the form inputs | HTML input fields, `value=""`, retrieving current data | What the user actually sees and types into. |
| **[[WP3.3.6.3 Nonce Verification]]** | Security check | `wp_create_nonce()`, `wp_verify_nonce()` | Ensuring the save request came from the actual editor. |
| **[[WP3.3.6.4 The 'save_post' Hook]]** | Saving the data | Checking autosaves, permissions, nonces, then updating | The logic that runs when "Update" is clicked. |
| **[[WP3.3.6.5 Styling Meta Boxes]]** | Admin UX | Using `.widefat` classes, CSS for admin screens | Making your custom fields look native. |
