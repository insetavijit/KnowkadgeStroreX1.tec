### **[[01 SQLAlchemy Fundamentals]]**

Master SQLAlchemy as the leading Python SQL toolkit and ORM. Learn why SQLAlchemy is used by Dropbox, Reddit, Yelp, and leading Python applications. Understand database abstraction, ORM patterns, and the flexibility that makes SQLAlchemy the standard for Python database access. SQLAlchemy skills are required for Python backend developers ($90k-$140k) and data engineers ($100k-$160k). Essential for building robust Python database applications.

|Topic|Focus & Purpose|
|---|---|
|**[[1.1 SQLAlchemy Introduction]]**|What is SQLAlchemy; ORM concept; Core vs ORM; ecosystem; SQLAlchemy 2.0; market importance. Industry context.|
|**[[1.2 Installation & Setup]]**|pip installation; database drivers; engine creation; connection strings. Environment setup.|
|**[[1.3 Architecture Overview]]**|Engine; Connection; Session; MetaData; declarative base; component relationship. Architecture.|
|**[[1.4 Database Engines]]**|create_engine(); database URLs; PostgreSQL; MySQL; SQLite; connection parameters. Engine creation.|
|**[[1.5 Connection Basics]]**|Engine.connect(); connection context; executing raw SQL; text(); result handling. Connections.|
|**[[1.6 SQLAlchemy 2.0 Style]]**|Modern 2.0 patterns; select(); type hints; new session patterns; migration from 1.x. Modern API.|
|**[[1.7 Project: First Connection]]**|Connecting to database; basic queries; engine setup; testing connectivity. First project.|

### **[[02 SQLAlchemy Core]]**

Master SQLAlchemy Core for SQL expression construction. Learn metadata, tables, and query building. Core provides database-agnostic SQL generation and direct database access.

|Topic|Focus & Purpose|
|---|---|
|**[[2.1 MetaData & Tables]]**|MetaData object; Table definition; Column; data types; reflection. Schema definition.|
|**[[2.2 Column Types]]**|Integer; String; Text; Boolean; DateTime; Float; Numeric; type selection. Column types.|
|**[[2.3 Constraints]]**|PrimaryKeyConstraint; ForeignKeyConstraint; UniqueConstraint; CheckConstraint. Constraints.|
|**[[2.4 Select Statements]]**|select(); where(); order_by(); limit(); offset(); column selection. Query building.|
|**[[2.5 Insert Statements]]**|insert(); values(); returning(); bulk insert; insert from select. Insert queries.|
|**[[2.6 Update & Delete]]**|update(); delete(); where conditions; returning; affected rows. Update/delete.|
|**[[2.7 Joins in Core]]**|join(); outerjoin(); select_from(); join conditions; multiple tables. Core joins.|
|**[[2.8 Project: Core Queries]]**|Building queries with Core; CRUD operations; complex queries. Core project.|

### **[[03 ORM Basics]]**

Master SQLAlchemy ORM for object-relational mapping. Learn declarative models, sessions, and basic CRUD. ORM provides Pythonic database interaction through classes.

|Topic|Focus & Purpose|
|---|---|
|**[[3.1 Declarative Base]]**|DeclarativeBase; mapped_column(); Mapped type; model classes. Model definition.|
|**[[3.2 Model Definition]]**|Class definition; __tablename__; columns; primary key; model structure. Defining models.|
|**[[3.3 Data Types in ORM]]**|Mapped types; String; Integer; DateTime; relationship types; type mapping. ORM types.|
|**[[3.4 Session Basics]]**|Session; sessionmaker; session lifecycle; add(); commit(); rollback(). Session management.|
|**[[3.5 Creating Objects]]**|Object instantiation; session.add(); session.add_all(); flushing; committing. Creating records.|
|**[[3.6 Querying Objects]]**|session.query(); select(); scalar(); scalars(); first(); all(); iteration. Querying.|
|**[[3.7 Updating Objects]]**|Modifying attributes; session tracking; commit changes; update patterns. Updating.|
|**[[3.8 Deleting Objects]]**|session.delete(); bulk delete; cascade; orphan removal. Deleting.|

### **[[04 Relationships]]**

Master ORM relationships for connected data. Learn one-to-many, many-to-many, and relationship configuration. Relationships are essential for modeling real-world data.

|Topic|Focus & Purpose|
|---|---|
|**[[4.1 Relationship Basics]]**|relationship(); back_populates; connected objects; navigation. Relationship concept.|
|**[[4.2 One-to-Many]]**|Parent-child; foreign key; relationship definition; bidirectional. One-to-many.|
|**[[4.3 Many-to-One]]**|Reverse relationship; foreign key placement; navigation direction. Many-to-one.|
|**[[4.4 One-to-One]]**|uselist=False; unique foreign key; one-to-one patterns. One-to-one.|
|**[[4.5 Many-to-Many]]**|Association table; secondary parameter; relationship configuration. Many-to-many.|
|**[[4.6 Association Objects]]**|Association proxies; extra data on relationships; complex associations. Association objects.|
|**[[4.7 Relationship Options]]**|order_by; lazy; cascade; back_populates; relationship tuning. Configuration.|
|**[[4.8 Project: Relational Model]]**|Building complete model; relationships; navigation; CRUD. Relationship project.|

### **[[05 Querying with ORM]]**

Master ORM querying for data retrieval. Learn select, filter, join, and advanced queries. Query skills are essential for effective data access.

|Topic|Focus & Purpose|
|---|---|
|**[[5.1 Select Statement]]**|select(); from_statement; column selection; query building. ORM select.|
|**[[5.2 Filtering]]**|where(); filter operators; ==, !=, <, >; and_(); or_(); not_(). Filtering.|
|**[[5.3 Operators]]**|in_(); like(); ilike(); between(); is_(); is_not(); contains(). Query operators.|
|**[[5.4 Ordering & Limiting]]**|order_by(); asc(); desc(); limit(); offset(); pagination. Ordering.|
|**[[5.5 Joins]]**|join(); outerjoin(); relationship-based joins; explicit joins. ORM joins.|
|**[[5.6 Eager Loading]]**|selectinload(); joinedload(); subqueryload(); lazy loading problems. Eager loading.|
|**[[5.7 Aggregations]]**|func.count(); func.sum(); func.avg(); group_by(); having(). Aggregations.|
|**[[5.8 Project: Complex Queries]]**|Building complex queries; joins; aggregations; optimization. Query project.|

### **[[06 Session Management]]**

Master session handling for reliable database operations. Learn session patterns, transactions, and lifecycle. Proper session management ensures data integrity.

|Topic|Focus & Purpose|
|---|---|
|**[[6.1 Session Lifecycle]]**|Session states; new; pending; persistent; detached; expired. Object states.|
|**[[6.2 Sessionmaker]]**|sessionmaker(); configuration; factory pattern; session creation. Session factory.|
|**[[6.3 Transaction Management]]**|begin(); commit(); rollback(); transaction scope; nested transactions. Transactions.|
|**[[6.4 Context Managers]]**|Session as context manager; automatic cleanup; error handling. Context pattern.|
|**[[6.5 Scoped Sessions]]**|scoped_session(); thread-local; request scope; web application pattern. Scoped sessions.|
|**[[6.6 Flush vs Commit]]**|flush(); commit(); difference; when to use; auto-flush. Flush/commit.|
|**[[6.7 Session Events]]**|Event listeners; before_flush; after_commit; session events. Events.|
|**[[6.8 Project: Session Patterns]]**|Implementing session management; transactions; error handling. Session project.|

### **[[07 Async SQLAlchemy]]**

Master async SQLAlchemy for high-performance applications. Learn async engine, sessions, and FastAPI integration. Async is essential for modern Python backends.

|Topic|Focus & Purpose|
|---|---|
|**[[7.1 Async Basics]]**|AsyncEngine; create_async_engine(); async drivers; asyncpg; aiosqlite. Async setup.|
|**[[7.2 Async Session]]**|AsyncSession; async_sessionmaker(); async context managers. Async sessions.|
|**[[7.3 Async Queries]]**|await session.execute(); scalars(); async iteration; result handling. Async querying.|
|**[[7.4 Async Relationships]]**|Lazy loading issues; selectinload(); awaitable relationships. Async relationships.|
|**[[7.5 Connection Pooling]]**|Async pool; pool configuration; connection management. Async pooling.|
|**[[7.6 FastAPI Integration]]**|Dependency injection; session per request; lifespan events. FastAPI.|
|**[[7.7 Project: Async API]]**|Building async API; FastAPI; async queries; performance. Async project.|

### **[[08 Migrations with Alembic]]**

Master database migrations with Alembic. Learn version control, auto-generation, and deployment. Migrations are essential for evolving database schemas.

|Topic|Focus & Purpose|
|---|---|
|**[[8.1 Alembic Introduction]]**|What is Alembic; migration concept; version control; installation. Migration basics.|
|**[[8.2 Alembic Setup]]**|alembic init; configuration; env.py; alembic.ini; project setup. Setup.|
|**[[8.3 Creating Migrations]]**|alembic revision; upgrade(); downgrade(); migration scripts. Creating migrations.|
|**[[8.4 Auto-Generation]]**|--autogenerate; model comparison; automatic migration creation. Auto-generation.|
|**[[8.5 Running Migrations]]**|alembic upgrade; alembic downgrade; head; base; specific versions. Running.|
|**[[8.6 Migration Best Practices]]**|Naming; testing migrations; data migrations; production safety. Best practices.|
|**[[8.7 Project: Schema Evolution]]**|Managing schema changes; migrations; rollback; deployment. Migration project.|

### **[[09 Advanced ORM Features]]**

Master advanced ORM capabilities for complex applications. Learn inheritance, events, and hybrid properties. Advanced features enable sophisticated data modeling.

|Topic|Focus & Purpose|
|---|---|
|**[[9.1 Table Inheritance]]**|Single table; joined table; concrete table; polymorphism. Inheritance patterns.|
|**[[9.2 Hybrid Properties]]**|@hybrid_property; @hybrid_method; SQL/Python dual behavior. Hybrid attributes.|
|**[[9.3 Custom Types]]**|TypeDecorator; custom column types; serialization; encryption. Custom types.|
|**[[9.4 Events & Hooks]]**|event.listen(); before_insert; after_update; model lifecycle. Event system.|
|**[[9.5 Mixins]]**|Model mixins; shared columns; timestamp mixin; reusable patterns. Mixins.|
|**[[9.6 Validators]]**|@validates; attribute validation; constraint enforcement. Validation.|
|**[[9.7 Project: Advanced Models]]**|Implementing advanced patterns; inheritance; events; validation. Advanced project.|

### **[[10 Query Optimization]]**

Master query optimization for database performance. Learn execution analysis, indexing, and efficient patterns. Optimization is critical for production applications.

|Topic|Focus & Purpose|
|---|---|
|**[[10.1 N+1 Problem]]**|Understanding N+1; detection; lazy loading issues; solutions. N+1 queries.|
|**[[10.2 Loading Strategies]]**|selectinload; joinedload; subqueryload; raiseload; strategy selection. Loading options.|
|**[[10.3 Query Execution]]**|echo=True; query compilation; execution analysis; debugging. Query analysis.|
|**[[10.4 Bulk Operations]]**|Bulk insert; bulk update; bulk delete; bypassing ORM. Bulk operations.|
|**[[10.5 Connection Pooling]]**|Pool configuration; pool_size; max_overflow; connection reuse. Pooling.|
|**[[10.6 Caching]]**|Query caching; result caching; dogpile.cache; caching patterns. Caching.|
|**[[10.7 Indexing]]**|Index creation; index selection; compound indexes; query optimization. Indexes.|
|**[[10.8 Project: Performance Tuning]]**|Optimizing slow queries; loading; pooling; benchmarks. Optimization project.|

### **[[11 Testing]]**

Master testing SQLAlchemy applications. Learn fixtures, factories, and test databases. Testing ensures reliable database code.

|Topic|Focus & Purpose|
|---|---|
|**[[11.1 Test Database Setup]]**|Test database; in-memory SQLite; test configuration; isolation. Test setup.|
|**[[11.2 Fixtures]]**|pytest fixtures; session fixtures; database fixtures; cleanup. Test fixtures.|
|**[[11.3 Factory Libraries]]**|factory_boy; model factories; test data generation; relationships. Factories.|
|**[[11.4 Transaction Rollback]]**|Test transaction; rollback after test; isolation; speed. Transaction testing.|
|**[[11.5 Mocking]]**|Mocking queries; mock session; unit testing; isolation. Mocking.|
|**[[11.6 Integration Tests]]**|Full database tests; migration testing; realistic testing. Integration.|
|**[[11.7 Project: Test Suite]]**|Complete test setup; fixtures; factories; coverage. Testing project.|

### **[[12 Security & Best Practices]]**

Master secure SQLAlchemy usage. Learn SQL injection prevention, sensitive data handling, and production patterns. Security is critical for database applications.

|Topic|Focus & Purpose|
|---|---|
|**[[12.1 SQL Injection Prevention]]**|Parameterized queries; bound parameters; safe patterns; text(). Injection prevention.|
|**[[12.2 Connection Security]]**|SSL connections; credential management; connection strings. Secure connections.|
|**[[12.3 Sensitive Data]]**|Encryption; hashing; column-level encryption; PII handling. Data protection.|
|**[[12.4 Error Handling]]**|IntegrityError; OperationalError; exception handling; recovery. Error handling.|
|**[[12.5 Logging]]**|Query logging; connection logging; debugging; production logging. Logging.|
|**[[12.6 Production Configuration]]**|Connection pooling; timeout settings; health checks; resilience. Production config.|
|**[[12.7 Project: Secure Application]]**|Implementing security; best practices; production-ready code. Security project.|

### **[[13 Framework Integration]]**

Master SQLAlchemy integration with Python frameworks. Learn Flask, FastAPI, and Django integration patterns. Integration enables SQLAlchemy in various application contexts.

|Topic|Focus & Purpose|
|---|---|
|**[[13.1 FastAPI Integration]]**|Dependency injection; async sessions; Pydantic integration; patterns. FastAPI.|
|**[[13.2 Flask Integration]]**|Flask-SQLAlchemy; application factory; request context. Flask.|
|**[[13.3 Starlette Integration]]**|Middleware; database middleware; async patterns. Starlette.|
|**[[13.4 Pydantic Integration]]**|Model to Pydantic; serialization; validation; SQLModel. Pydantic.|
|**[[13.5 Celery Integration]]**|Background tasks; session per task; connection handling. Celery.|
|**[[13.6 Project: Web Application]]**|Complete web app; framework integration; patterns. Integration project.|

### **[[14 Real-World Projects]]**

Master building production SQLAlchemy applications. Build impressive portfolio pieces demonstrating database expertise. Real projects are essential for landing Python backend positions.

|Topic|Focus & Purpose|
|---|---|
|**[[14.1 CRUD API]]**|Complete REST API; models; relationships; CRUD operations. API project.|
|**[[14.2 E-Commerce Database]]**|Products; orders; users; transactions; complex schema. E-commerce.|
|**[[14.3 Multi-Tenant Application]]**|Tenant isolation; schema per tenant; row-level security. Multi-tenancy.|
|**[[14.4 Analytics System]]**|Time series; aggregations; reporting; large datasets. Analytics.|
|**[[14.5 Blog/CMS Backend]]**|Posts; categories; comments; users; full-text search. CMS.|
|**[[14.6 Task Management]]**|Projects; tasks; assignments; notifications; audit logging. Task management.|
|**[[14.7 Authentication Service]]**|Users; roles; permissions; tokens; secure auth. Auth service.|
|**[[14.8 Production Application]]**|Complete production app; optimization; security; deployment. Portfolio project.|
