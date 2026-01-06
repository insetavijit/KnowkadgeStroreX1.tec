### **[[01 SQL Fundamentals]]**

Master SQL as the universal language for database management. Learn why SQL skills are required at every company from startups to Fortune 500. Understand relational databases, query execution, and data manipulation that forms the backbone of data storage. SQL developers earn $70k-$130k, while database administrators and data engineers earn $90k-$160k. Essential for backend development, data analysis, data engineering, and virtually every tech role.

|Topic|Focus & Purpose|
|---|---|
|**[[1.1 SQL Introduction]]**|What is SQL; relational databases; RDBMS; SQL vs NoSQL; industry importance; job demand. Core concepts.|
|**[[1.2 Database Concepts]]**|Tables; rows; columns; primary keys; foreign keys; relationships; schema; database structure. Fundamentals.|
|**[[1.3 SQL Dialects]]**|MySQL; PostgreSQL; SQL Server; Oracle; SQLite; dialect differences; standard SQL. SQL variants.|
|**[[1.4 Environment Setup]]**|Database installation; GUI tools (DBeaver, pgAdmin, MySQL Workbench); command line; practice databases. Setup.|
|**[[1.5 First Queries]]**|SELECT basics; FROM clause; column selection; * wildcard; running queries. Getting started.|
|**[[1.6 SQL Syntax]]**|Statement structure; clauses; keywords; semicolons; case sensitivity; comments. Syntax basics.|
|**[[1.7 Project: Database Exploration]]**|Connecting to database; exploring tables; first SELECT queries. First project.|

### **[[02 SELECT Queries]]**

Master SELECT statements for data retrieval. Learn filtering, sorting, and limiting results. SELECT is the most frequently used SQL command and fundamental to all database work.

|Topic|Focus & Purpose|
|---|---|
|**[[2.1 SELECT Fundamentals]]**|SELECT clause; column selection; expressions; aliases; column naming. Basic SELECT.|
|**[[2.2 WHERE Clause]]**|Filtering rows; comparison operators; =, <>, <, >, <=, >=; condition syntax. Filtering.|
|**[[2.3 Logical Operators]]**|AND; OR; NOT; operator precedence; combining conditions; parentheses. Complex filters.|
|**[[2.4 LIKE & Pattern Matching]]**|LIKE operator; % wildcard; _ wildcard; pattern matching; case sensitivity. Pattern matching.|
|**[[2.5 IN & BETWEEN]]**|IN operator; value lists; BETWEEN; range queries; NOT IN; NOT BETWEEN. Value ranges.|
|**[[2.6 NULL Handling]]**|NULL concept; IS NULL; IS NOT NULL; NULL in comparisons; COALESCE; NULLIF. Null handling.|
|**[[2.7 ORDER BY]]**|Sorting results; ASC; DESC; multiple columns; NULL ordering; sort expressions. Ordering.|
|**[[2.8 LIMIT & OFFSET]]**|Result limiting; pagination; TOP; FETCH; database-specific syntax. Result limiting.|

### **[[03 Data Manipulation (DML)]]**

Master data manipulation for creating, updating, and deleting data. Learn INSERT, UPDATE, DELETE operations. DML skills are essential for maintaining and modifying data.

|Topic|Focus & Purpose|
|---|---|
|**[[3.1 INSERT Basics]]**|INSERT INTO; column specification; VALUES; inserting single rows; column order. Inserting data.|
|**[[3.2 INSERT Multiple Rows]]**|Multiple row insert; bulk insert; INSERT SELECT; copying data. Bulk insert.|
|**[[3.3 UPDATE Basics]]**|UPDATE statement; SET clause; WHERE condition; updating columns. Updating data.|
|**[[3.4 UPDATE with Conditions]]**|Conditional updates; multiple columns; calculated values; safe updates. Complex updates.|
|**[[3.5 DELETE Basics]]**|DELETE statement; WHERE condition; deleting rows; safety considerations. Deleting data.|
|**[[3.6 TRUNCATE]]**|TRUNCATE vs DELETE; performance; resetting identity; when to use. Truncate table.|
|**[[3.7 UPSERT]]**|INSERT ON CONFLICT; MERGE; upsert patterns; database-specific syntax. Upsert operations.|
|**[[3.8 Project: Data Management]]**|CRUD operations; inserting; updating; deleting; data maintenance. DML project.|

### **[[04 Aggregate Functions]]**

Master aggregate functions for data summarization. Learn COUNT, SUM, AVG, and grouping. Aggregation is essential for reporting and data analysis.

|Topic|Focus & Purpose|
|---|---|
|**[[4.1 COUNT Function]]**|COUNT(*); COUNT(column); COUNT(DISTINCT); counting rows; null handling. Counting.|
|**[[4.2 SUM & AVG]]**|SUM function; AVG function; numeric aggregation; null handling. Numeric aggregates.|
|**[[4.3 MIN & MAX]]**|MIN function; MAX function; finding extremes; date/string min/max. Extremes.|
|**[[4.4 GROUP BY]]**|Grouping rows; GROUP BY clause; aggregate per group; multiple columns. Grouping.|
|**[[4.5 HAVING Clause]]**|Filtering groups; HAVING vs WHERE; aggregate conditions; group filtering. Group filtering.|
|**[[4.6 DISTINCT]]**|Distinct values; column combinations; COUNT DISTINCT; unique results. Distinct.|
|**[[4.7 Aggregate Expressions]]**|Calculated aggregates; conditional aggregation; CASE in aggregates. Complex aggregates.|
|**[[4.8 Project: Sales Report]]**|Aggregate analysis; grouping; totals; averages; reporting queries. Aggregation project.|

### **[[05 Joins]]**

Master table joins for combining data from multiple tables. Learn join types, conditions, and patterns. Joins are fundamental to relational database queries.

|Topic|Focus & Purpose|
|---|---|
|**[[5.1 JOIN Concept]]**|Why joins; table relationships; combining tables; join syntax. Join basics.|
|**[[5.2 INNER JOIN]]**|Inner join; matching rows; ON clause; join conditions; most common join. Inner join.|
|**[[5.3 LEFT JOIN]]**|Left outer join; all left rows; unmatched rows; NULL for missing. Left join.|
|**[[5.4 RIGHT JOIN]]**|Right outer join; all right rows; less common usage; equivalent to LEFT. Right join.|
|**[[5.5 FULL OUTER JOIN]]**|Full outer join; all rows from both; matching and non-matching. Full join.|
|**[[5.6 CROSS JOIN]]**|Cartesian product; all combinations; use cases; caution with large tables. Cross join.|
|**[[5.7 Self Join]]**|Joining table to itself; hierarchical data; comparing rows; parent-child. Self join.|
|**[[5.8 Multiple Joins]]**|Joining multiple tables; join order; complex queries; performance. Multi-table joins.|

### **[[06 Subqueries]]**

Master subqueries for complex data retrieval. Learn scalar, column, and table subqueries. Subqueries enable sophisticated queries and data analysis.

|Topic|Focus & Purpose|
|---|---|
|**[[6.1 Subquery Basics]]**|What are subqueries; nested queries; subquery placement; execution order. Subquery concept.|
|**[[6.2 Scalar Subqueries]]**|Single value subquery; in SELECT; in WHERE; aggregate subqueries. Scalar subqueries.|
|**[[6.3 Column Subqueries]]**|Multiple values; IN with subquery; NOT IN; value list subqueries. Column subqueries.|
|**[[6.4 Table Subqueries]]**|Derived tables; subquery in FROM; inline views; aliasing. Table subqueries.|
|**[[6.5 Correlated Subqueries]]**|Outer reference; row-by-row execution; EXISTS; performance consideration. Correlated.|
|**[[6.6 EXISTS Operator]]**|EXISTS; NOT EXISTS; checking existence; correlated EXISTS; performance. EXISTS.|
|**[[6.7 Subquery vs JOIN]]**|When to use each; performance comparison; readability; best practices. Comparison.|
|**[[6.8 Project: Complex Queries]]**|Building complex queries; subqueries; analysis; reporting. Subquery project.|

### **[[07 Data Definition (DDL)]]**

Master data definition for creating and modifying database structures. Learn CREATE, ALTER, DROP operations. DDL skills are essential for database design and management.

|Topic|Focus & Purpose|
|---|---|
|**[[7.1 CREATE TABLE]]**|Creating tables; column definitions; data types; basic constraints. Table creation.|
|**[[7.2 Data Types]]**|Integer types; decimal; VARCHAR; TEXT; DATE; TIMESTAMP; BOOLEAN; type selection. Data types.|
|**[[7.3 Constraints]]**|PRIMARY KEY; NOT NULL; UNIQUE; CHECK; DEFAULT; constraint syntax. Column constraints.|
|**[[7.4 Foreign Keys]]**|FOREIGN KEY; REFERENCES; ON DELETE; ON UPDATE; referential integrity. Relationships.|
|**[[7.5 ALTER TABLE]]**|Adding columns; dropping columns; modifying columns; renaming; schema changes. Table modification.|
|**[[7.6 DROP & TRUNCATE]]**|DROP TABLE; DROP DATABASE; CASCADE; TRUNCATE; destructive operations. Removing objects.|
|**[[7.7 Indexes]]**|CREATE INDEX; index types; B-tree; performance impact; when to index. Indexing.|
|**[[7.8 Project: Schema Design]]**|Designing database schema; tables; relationships; constraints. DDL project.|

### **[[08 Advanced SELECT]]**

Master advanced SELECT features for complex queries. Learn CASE expressions, CTEs, and window functions. Advanced features enable sophisticated data analysis.

|Topic|Focus & Purpose|
|---|---|
|**[[8.1 CASE Expression]]**|CASE WHEN THEN; simple CASE; searched CASE; conditional logic. Conditional logic.|
|**[[8.2 Common Table Expressions]]**|WITH clause; CTE syntax; readable queries; multiple CTEs; CTE chains. CTEs.|
|**[[8.3 Recursive CTEs]]**|Recursive queries; hierarchical data; tree traversal; recursive CTE syntax. Recursion.|
|**[[8.4 UNION]]**|UNION; UNION ALL; combining results; column compatibility; set operations. Union.|
|**[[8.5 INTERSECT & EXCEPT]]**|INTERSECT; EXCEPT (MINUS); set operations; finding common/different rows. Set operations.|
|**[[8.6 String Functions]]**|CONCAT; SUBSTRING; LENGTH; UPPER; LOWER; TRIM; REPLACE; string manipulation. String functions.|
|**[[8.7 Date Functions]]**|NOW(); DATE functions; EXTRACT; DATE_ADD; DATE_DIFF; date manipulation. Date functions.|
|**[[8.8 Project: Advanced Analysis]]**|Complex queries; CTEs; CASE; string/date functions; analysis. Advanced project.|

### **[[09 Window Functions]]**

Master window functions for advanced analytics. Learn ranking, running totals, and moving averages. Window functions are essential for data analysis and reporting.

|Topic|Focus & Purpose|
|---|---|
|**[[9.1 Window Function Basics]]**|OVER clause; window concept; vs aggregate; row-level results. Window basics.|
|**[[9.2 PARTITION BY]]**|Partitioning; groups within windows; resetting calculations; partition definition. Partitions.|
|**[[9.3 ORDER BY in Windows]]**|Window ordering; running calculations; cumulative functions; order specification. Window ordering.|
|**[[9.4 ROW_NUMBER]]**|Row numbering; unique ranking; pagination; duplicate handling. Row numbering.|
|**[[9.5 RANK & DENSE_RANK]]**|Ranking with ties; RANK gaps; DENSE_RANK continuous; ranking patterns. Ranking.|
|**[[9.6 LAG & LEAD]]**|Previous row values; next row values; offset; default values; comparison. Offset functions.|
|**[[9.7 Running Totals]]**|SUM OVER; running aggregates; cumulative calculations; moving averages. Running calculations.|
|**[[9.8 Project: Analytics Report]]**|Window function analysis; rankings; running totals; comparisons. Analytics project.|

### **[[10 Views & Stored Procedures]]**

Master views and stored procedures for reusable SQL. Learn view creation, stored procedures, and functions. These features enable code reuse and abstraction.

|Topic|Focus & Purpose|
|---|---|
|**[[10.1 Views Basics]]**|CREATE VIEW; view concept; virtual tables; view usage; abstraction. View creation.|
|**[[10.2 View Advantages]]**|Security; simplification; logic encapsulation; query reuse; maintenance. View benefits.|
|**[[10.3 Updateable Views]]**|INSERT/UPDATE through views; restrictions; INSTEAD OF triggers. Modifying views.|
|**[[10.4 Materialized Views]]**|Materialized views; performance; refresh; storage; vs regular views. Materialized.|
|**[[10.5 Stored Procedures]]**|CREATE PROCEDURE; parameters; CALL/EXECUTE; procedure logic. Procedures.|
|**[[10.6 Functions]]**|CREATE FUNCTION; scalar functions; table functions; return types. User functions.|
|**[[10.7 Variables & Control Flow]]**|DECLARE; SET; IF/ELSE; LOOP; WHILE; procedural SQL. Procedural logic.|
|**[[10.8 Project: Reusable SQL]]**|Creating views; procedures; functions; business logic. Reusability project.|

### **[[11 Transactions & Concurrency]]**

Master transactions for data integrity. Learn ACID properties, isolation levels, and locking. Transaction skills are critical for reliable database applications.

|Topic|Focus & Purpose|
|---|---|
|**[[11.1 Transaction Basics]]**|Transaction concept; BEGIN; COMMIT; ROLLBACK; transaction lifecycle. Transaction basics.|
|**[[11.2 ACID Properties]]**|Atomicity; Consistency; Isolation; Durability; reliability guarantees. ACID.|
|**[[11.3 Savepoints]]**|SAVEPOINT; partial rollback; nested transactions; savepoint management. Savepoints.|
|**[[11.4 Isolation Levels]]**|READ UNCOMMITTED; READ COMMITTED; REPEATABLE READ; SERIALIZABLE. Isolation.|
|**[[11.5 Concurrency Issues]]**|Dirty reads; non-repeatable reads; phantom reads; lost updates. Concurrency problems.|
|**[[11.6 Locking]]**|Row locks; table locks; shared vs exclusive; deadlocks; lock management. Locking.|
|**[[11.7 Deadlock Handling]]**|Deadlock detection; prevention; resolution; timeout; best practices. Deadlocks.|
|**[[11.8 Project: Transaction Safety]]**|Implementing transactions; isolation; error handling; integrity. Transaction project.|

### **[[12 Query Optimization]]**

Master query optimization for database performance. Learn execution plans, indexing strategies, and optimization techniques. Optimization skills are essential for production databases.

|Topic|Focus & Purpose|
|---|---|
|**[[12.1 Execution Plans]]**|EXPLAIN; EXPLAIN ANALYZE; reading plans; understanding execution. Execution plans.|
|**[[12.2 Index Strategy]]**|Index types; composite indexes; covering indexes; index selection. Indexing strategy.|
|**[[12.3 Query Analysis]]**|Slow query identification; query profiling; performance metrics. Query analysis.|
|**[[12.4 Optimization Techniques]]**|Avoiding SELECT *; limiting results; efficient joins; query rewriting. Techniques.|
|**[[12.5 Join Optimization]]**|Join order; join algorithms; nested loop; hash join; merge join. Join performance.|
|**[[12.6 Subquery Optimization]]**|Subquery vs JOIN; EXISTS vs IN; correlated subquery performance. Subquery tuning.|
|**[[12.7 Statistics]]**|Table statistics; ANALYZE; optimizer statistics; cardinality estimation. Statistics.|
|**[[12.8 Project: Performance Tuning]]**|Optimizing slow queries; indexes; execution plans; benchmarks. Optimization project.|

### **[[13 Database Administration]]**

Master database administration basics. Learn backup, security, and maintenance. DBA skills are valuable for full-stack developers and dedicated admins.

|Topic|Focus & Purpose|
|---|---|
|**[[13.1 User Management]]**|CREATE USER; roles; privileges; GRANT; REVOKE; access control. User management.|
|**[[13.2 Permissions]]**|Table permissions; column permissions; schema permissions; least privilege. Permissions.|
|**[[13.3 Backup & Recovery]]**|Backup strategies; pg_dump; mysqldump; point-in-time recovery; restore. Backup.|
|**[[13.4 Data Import/Export]]**|COPY; LOAD DATA; bulk operations; CSV import; data migration. Data transfer.|
|**[[13.5 Maintenance]]**|VACUUM; ANALYZE; table maintenance; index rebuilding; housekeeping. Maintenance.|
|**[[13.6 Monitoring]]**|Query logs; performance monitoring; connection monitoring; alerts. Monitoring.|
|**[[13.7 Project: DBA Tasks]]**|User setup; backups; permissions; maintenance routines. Admin project.|

### **[[14 Real-World Projects]]**

Master building production database solutions. Build impressive portfolio pieces that demonstrate SQL expertise. Real projects are essential for landing database and development positions.

|Topic|Focus & Purpose|
|---|---|
|**[[14.1 E-Commerce Database]]**|Products; orders; customers; inventory; complex queries; reporting. E-commerce schema.|
|**[[14.2 Blog/CMS Database]]**|Posts; categories; comments; users; hierarchical data; full-text. Content schema.|
|**[[14.3 Analytics Queries]]**|Business metrics; KPIs; trend analysis; cohort analysis; dashboards. Analytics.|
|**[[14.4 Reporting System]]**|Report queries; aggregations; pivoting; scheduled reports; exports. Reporting.|
|**[[14.5 Data Warehouse Queries]]**|Star schema; fact/dimension; OLAP queries; analytical queries. Warehousing.|
|**[[14.6 Migration Scripts]]**|Schema migrations; data migrations; version control; rollback. Migrations.|
|**[[14.7 Interview Questions]]**|Common SQL interview questions; query challenges; optimization problems. Interviews.|
|**[[14.8 Production Database]]**|Complete database design; queries; optimization; documentation. Portfolio project.|
