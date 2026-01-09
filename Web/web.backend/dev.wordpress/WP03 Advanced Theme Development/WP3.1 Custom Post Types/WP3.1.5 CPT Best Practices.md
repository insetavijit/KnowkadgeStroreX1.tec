| **Subtopic** | **Focus & Purpose** | **Key Concepts / Details** | **One-Line Recall** |
|---|---|---|---|
| **[[WP3.1.5.1 Themes vs Plugins]]** | Deciding where code belongs | Portability, data locking explanation (Theme switch issue) | Register CPTs in plugins to save content when themes change. |
| **[[WP3.1.5.2 Prefixing & Naming Conventions]]** | Avoiding conflicts | Namespace prefixes (e.g., `acme_project`), reserved words list | Always prefix function names and CPT keys. |
| **[[WP3.1.5.3 Flushing Rewrite Rules Correctly]]** | Managing permalinks | `flush_rewrite_rules()`, activation hook vs `init` hook | Flush rules only once on activation, never on every page load. |
| **[[WP3.1.5.4 Internationalization (i18n)]]** | Making CPTs translation-ready | `__()`, `_x()`, text domains for labels | Wrap all label strings in translation functions. |
| **[[WP3.1.5.5 Security & Data Validation]]** | Securing input/output | Sanitizing args, escaping output labels, user capability checks | Trust no input, even in registration arguments. |
