| **Subtopic** | **Focus & Purpose** | **Key Concepts / Details** | **One-Line Recall** |
| :--- | :--- | :--- | :--- |
| **[[WP1.2.6.1 Creating a Database]]** | Storage container | Using phpMyAdmin; "New Database"; Collation (utf8mb4_unicode_ci). | Create the bucket for your data first. |
| **[[WP1.2.6.2 Database Users]]** | Access control | Root user (default local); creating dedicated users; granting privileges. | Don't use root for production databases. |
| **[[WP1.2.6.3 Character Sets & Collation]]**| Data integrity | utf8mb4 support for emojis/languages; unicode_ci for sorting rules. | Use utf8mb4 to support all characters. |
| **[[WP1.2.6.4 Table Prefixes]]** | Security/Organization | changing wp_; preventing SQL injection guessing; multiple installs in one DB. | Change wp_ prefix for better security. |
| **[[WP1.2.6.5 Import/Export]]** | Data portability | Exporting .sql files; importing via phpMyAdmin; handling max upload size limits. | SQL files are your database backups. |
