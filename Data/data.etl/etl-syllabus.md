### **[[01 ETL Fundamentals]]**

Master ETL (Extract, Transform, Load) as the foundation of data engineering. Learn why ETL pipelines power analytics at Netflix, Airbnb, Spotify, and every data-driven company. Understand data integration, pipeline architecture, and the processes that transform raw data into actionable insights. ETL engineers earn $100k-$160k, while senior data engineers earn $140k-$200k. Essential for data engineering, analytics engineering, and business intelligence careers.

|Topic|Focus & Purpose|
|---|---|
|**[[1.1 ETL Introduction]]**|What is ETL; data integration; data pipelines; ETL vs ELT; modern data stack; market demand. Industry context.|
|**[[1.2 ETL Architecture]]**|Source systems; staging; transformation; target systems; pipeline design; batch vs streaming. Architecture.|
|**[[1.3 Data Warehousing Concepts]]**|Data warehouse; data lake; data lakehouse; OLTP vs OLAP; dimensional modeling. Warehouse basics.|
|**[[1.4 ETL Tools Landscape]]**|Apache Airflow; dbt; Fivetran; Talend; AWS Glue; tool comparison. Tool ecosystem.|
|**[[1.5 ETL vs ELT]]**|Traditional ETL; modern ELT; cloud transformation; compute location; when to use each. ETL/ELT comparison.|
|**[[1.6 Data Quality Fundamentals]]**|Data quality dimensions; accuracy; completeness; consistency; timeliness. Quality basics.|
|**[[1.7 Project: ETL Concept Design]]**|Designing first pipeline; source to target mapping; transformation logic. First project.|

### **[[02 Extraction]]**

Master data extraction from diverse sources. Learn database extraction, API calls, file processing, and change data capture. Extraction is the first step in moving data into analytical systems.

|Topic|Focus & Purpose|
|---|---|
|**[[2.1 Extraction Basics]]**|Full extraction; incremental extraction; extraction patterns; source impact. Extraction concepts.|
|**[[2.2 Database Extraction]]**|SQL queries; JDBC/ODBC; database connectors; connection pooling; extraction queries. Database sources.|
|**[[2.3 API Extraction]]**|REST APIs; pagination; rate limiting; authentication; error handling. API sources.|
|**[[2.4 File Extraction]]**|CSV; JSON; XML; Parquet; Excel; file parsing; encoding handling. File sources.|
|**[[2.5 Change Data Capture]]**|CDC concept; Debezium; log-based CDC; trigger-based; timestamp-based. CDC.|
|**[[2.6 Streaming Extraction]]**|Kafka; real-time sources; event streams; streaming patterns. Stream sources.|
|**[[2.7 Incremental Loading]]**|Watermarks; high-water mark; delta detection; incremental strategies. Incremental.|
|**[[2.8 Project: Multi-Source Extraction]]**|Extracting from databases; APIs; files; consolidation. Extraction project.|

### **[[03 Transformation]]**

Master data transformation for analytical needs. Learn cleaning, standardization, aggregation, and enrichment. Transformation converts raw data into valuable analytical assets.

|Topic|Focus & Purpose|
|---|---|
|**[[3.1 Transformation Basics]]**|Transformation types; row-level; aggregation; join; data conversion. Transformation concepts.|
|**[[3.2 Data Cleaning]]**|Null handling; deduplication; outlier treatment; data quality fixes. Cleaning.|
|**[[3.3 Data Standardization]]**|Date formats; naming conventions; type conversion; normalization. Standardization.|
|**[[3.4 Data Enrichment]]**|Lookups; joins; external data; derived columns; calculated fields. Enrichment.|
|**[[3.5 Aggregations]]**|Grouping; summarization; rollups; metrics calculation; fact table creation. Aggregations.|
|**[[3.6 Complex Transformations]]**|Pivoting; unpivoting; window functions; conditional logic. Advanced transforms.|
|**[[3.7 Schema Evolution]]**|Schema changes; backward compatibility; type evolution; migration. Schema handling.|
|**[[3.8 Project: Transformation Pipeline]]**|Building transformation logic; cleaning; enrichment; aggregation. Transform project.|

### **[[04 Loading]]**

Master data loading into target systems. Learn bulk loading, upserts, and data warehouse loading patterns. Loading delivers transformed data to its destination.

|Topic|Focus & Purpose|
|---|---|
|**[[4.1 Loading Strategies]]**|Full load; incremental load; append; merge; truncate-load. Loading patterns.|
|**[[4.2 Bulk Loading]]**|Bulk insert; COPY command; staging tables; performance optimization. Bulk operations.|
|**[[4.3 Upsert (Merge)]]**|Insert or update; MERGE statement; conflict resolution; SCD handling. Upsert patterns.|
|**[[4.4 Slowly Changing Dimensions]]**|SCD Type 1; Type 2; Type 3; historical tracking; dimension handling. SCDs.|
|**[[4.5 Data Warehouse Loading]]**|Fact tables; dimension tables; star schema loading; incremental facts. Warehouse loading.|
|**[[4.6 Data Lake Loading]]**|Partitioning; file formats; Delta Lake; Iceberg; catalog management. Lake loading.|
|**[[4.7 Validation & Verification]]**|Row counts; checksums; data validation; reconciliation; quality gates. Load validation.|
|**[[4.8 Project: Complete Load Process]]**|Implementing loading; staging; SCDs; validation. Loading project.|

### **[[05 Apache Airflow]]**

Master Apache Airflow for workflow orchestration. Learn DAGs, operators, and scheduling. Airflow is the industry standard for orchestrating ETL pipelines.

|Topic|Focus & Purpose|
|---|---|
|**[[5.1 Airflow Introduction]]**|What is Airflow; workflow orchestration; use cases; architecture. Airflow basics.|
|**[[5.2 DAGs]]**|Directed Acyclic Graphs; DAG definition; Python DAGs; dependencies. DAG concepts.|
|**[[5.3 Operators]]**|PythonOperator; BashOperator; SqlOperator; sensor operators; custom operators. Operators.|
|**[[5.4 Task Dependencies]]**|Upstream/downstream; bitshift operators; cross-DAG dependencies. Dependencies.|
|**[[5.5 Scheduling]]**|Cron expressions; schedule_interval; catchup; backfill; timing. Scheduling.|
|**[[5.6 XComs]]**|Task communication; pushing/pulling data; XCom limitations. Inter-task data.|
|**[[5.7 Connections & Variables]]**|Connection management; secrets; variables; configuration. Configuration.|
|**[[5.8 Project: Airflow Pipeline]]**|Building complete ETL DAG; operators; scheduling; monitoring. Airflow project.|

### **[[06 dbt (Data Build Tool)]]**

Master dbt for transformation workflows. Learn models, tests, and documentation. dbt has become the standard for ELT transformations in the modern data stack.

|Topic|Focus & Purpose|
|---|---|
|**[[6.1 dbt Introduction]]**|What is dbt; analytics engineering; transformation layer; dbt Cloud vs Core. dbt basics.|
|**[[6.2 dbt Project Structure]]**|Project layout; models; sources; tests; macros; documentation. Project structure.|
|**[[6.3 Models]]**|SQL models; model materialization; table; view; incremental; ephemeral. dbt models.|
|**[[6.4 Sources & Refs]]**|Source definitions; ref function; DAG building; dependency management. References.|
|**[[6.5 Tests]]**|Schema tests; data tests; unique; not_null; custom tests; test coverage. Testing.|
|**[[6.6 Documentation]]**|Model documentation; column descriptions; doc blocks; dbt docs. Documentation.|
|**[[6.7 Macros & Jinja]]**|Jinja templating; macros; reusable SQL; DRY principles. Macros.|
|**[[6.8 Project: dbt Transformation]]**|Building dbt project; models; tests; documentation; deployment. dbt project.|

### **[[07 Data Quality]]**

Master data quality management for reliable pipelines. Learn validation, monitoring, and quality metrics. Data quality ensures trustworthy analytics and decisions.

|Topic|Focus & Purpose|
|---|---|
|**[[7.1 Quality Dimensions]]**|Accuracy; completeness; consistency; timeliness; validity; uniqueness. Quality measures.|
|**[[7.2 Data Validation]]**|Schema validation; business rules; constraint checking; validation frameworks. Validation.|
|**[[7.3 Quality Tools]]**|Great Expectations; dbt tests; Soda; quality platforms; tool comparison. Quality tools.|
|**[[7.4 Data Profiling]]**|Automated profiling; statistics; pattern detection; anomaly detection. Profiling.|
|**[[7.5 Quality Monitoring]]**|Continuous monitoring; alerting; dashboards; quality metrics. Monitoring.|
|**[[7.6 Quality Gates]]**|Pipeline gates; quality thresholds; failure handling; data quarantine. Quality gates.|
|**[[7.7 Data Observability]]**|Observability platforms; lineage; freshness; volume; schema tracking. Observability.|
|**[[7.8 Project: Quality Framework]]**|Implementing quality checks; monitoring; alerting; reporting. Quality project.|

### **[[08 Python ETL]]**

Master Python for ETL development. Learn Pandas, PyArrow, and ETL patterns. Python is the primary language for ETL development and automation.

|Topic|Focus & Purpose|
|---|---|
|**[[8.1 Pandas for ETL]]**|Read/write operations; transformations; data manipulation; performance. Pandas ETL.|
|**[[8.2 PyArrow & Parquet]]**|Columnar format; Arrow tables; Parquet read/write; performance. Arrow/Parquet.|
|**[[8.3 SQL in Python]]**|SQLAlchemy; database operations; query execution; connection management. Python SQL.|
|**[[8.4 API Integration]]**|requests library; API pagination; retry logic; rate limiting. API handling.|
|**[[8.5 File Processing]]**|CSV; JSON; Excel; XML; file handling patterns; encoding. File processing.|
|**[[8.6 Parallel Processing]]**|multiprocessing; concurrent.futures; Dask; parallel ETL. Parallelization.|
|**[[8.7 Error Handling]]**|Exception handling; retry patterns; logging; failure recovery. Error handling.|
|**[[8.8 Project: Python ETL Pipeline]]**|Complete Python ETL; extraction; transformation; loading. Python project.|

### **[[09 Cloud ETL Services]]**

Master cloud-native ETL services for scalable pipelines. Learn AWS Glue, Azure Data Factory, and GCP Dataflow. Cloud services enable managed, scalable data processing.

|Topic|Focus & Purpose|
|---|---|
|**[[9.1 AWS Glue]]**|Glue crawlers; Glue jobs; Spark; catalog; serverless ETL. AWS Glue.|
|**[[9.2 Azure Data Factory]]**|Pipelines; activities; datasets; linked services; data flows. Azure ADF.|
|**[[9.3 GCP Dataflow]]**|Apache Beam; batch and stream; templates; managed service. GCP Dataflow.|
|**[[9.4 Serverless ETL]]**|AWS Lambda; Azure Functions; event-driven; cost optimization. Serverless.|
|**[[9.5 Managed Ingestion]]**|Fivetran; Airbyte; Stitch; managed connectors; replication. Managed tools.|
|**[[9.6 Cloud Data Warehouses]]**|Snowflake; BigQuery; Redshift; warehouse loading patterns. Cloud warehouses.|
|**[[9.7 Project: Cloud Pipeline]]**|Building cloud ETL; managed services; serverless; monitoring. Cloud project.|

### **[[10 Streaming ETL]]**

Master real-time data processing for streaming pipelines. Learn Kafka, Spark Streaming, and real-time patterns. Streaming enables near-real-time analytics and actions.

|Topic|Focus & Purpose|
|---|---|
|**[[10.1 Streaming Fundamentals]]**|Batch vs streaming; real-time; event time; processing time. Streaming basics.|
|**[[10.2 Apache Kafka]]**|Kafka for ETL; topics; consumers; producers; Kafka Connect. Kafka.|
|**[[10.3 Stream Processing]]**|Kafka Streams; Flink; Spark Streaming; stream processing patterns. Processing.|
|**[[10.4 Windowing]]**|Tumbling; sliding; session windows; watermarks; late data. Windowing.|
|**[[10.5 Change Data Capture]]**|Debezium; CDC patterns; real-time replication; event sourcing. CDC streaming.|
|**[[10.6 Lambda Architecture]]**|Batch + stream; speed layer; serving layer; architecture patterns. Lambda.|
|**[[10.7 Project: Streaming Pipeline]]**|Real-time ETL; Kafka; stream processing; analytics. Streaming project.|

### **[[11 Data Modeling]]**

Master dimensional modeling for analytics. Learn star schemas, fact tables, and warehouse design. Data modeling is essential for analytical database design.

|Topic|Focus & Purpose|
|---|---|
|**[[11.1 Dimensional Modeling]]**|Kimball methodology; dimensional design; business process modeling. Modeling basics.|
|**[[11.2 Fact Tables]]**|Measures; grain; transaction facts; periodic snapshots; accumulating. Fact tables.|
|**[[11.3 Dimension Tables]]**|Attributes; hierarchies; conformed dimensions; role-playing dimensions. Dimensions.|
|**[[11.4 Star Schema]]**|Star schema design; simplicity; query performance; denormalization. Star schema.|
|**[[11.5 Snowflake Schema]]**|Normalized dimensions; when to use; performance tradeoffs. Snowflake schema.|
|**[[11.6 Slowly Changing Dimensions]]**|SCD types; history tracking; implementation patterns. SCD design.|
|**[[11.7 Advanced Patterns]]**|Bridge tables; many-to-many; large dimensions; heterogeneous products. Advanced.|
|**[[11.8 Project: Data Model]]**|Designing complete warehouse model; facts; dimensions; schema. Modeling project.|

### **[[12 Monitoring & Operations]]**

Master ETL operations and monitoring. Learn logging, alerting, and pipeline maintenance. Operations ensure reliable, maintainable data pipelines.

|Topic|Focus & Purpose|
|---|---|
|**[[12.1 Logging]]**|Structured logging; log levels; log aggregation; pipeline logging. Logging.|
|**[[12.2 Monitoring Metrics]]**|Pipeline metrics; latency; throughput; success rates; error rates. Metrics.|
|**[[12.3 Alerting]]**|Alert configuration; thresholds; escalation; on-call; incident response. Alerting.|
|**[[12.4 Data Lineage]]**|Lineage tracking; impact analysis; dependency graphs; lineage tools. Lineage.|
|**[[12.5 Pipeline Debugging]]**|Troubleshooting; log analysis; data inspection; common issues. Debugging.|
|**[[12.6 Performance Optimization]]**|Query optimization; parallelization; partitioning; resource tuning. Performance.|
|**[[12.7 Project: Operations Setup]]**|Implementing monitoring; alerting; dashboards; runbooks. Operations project.|

### **[[13 Testing & CI/CD]]**

Master ETL testing and deployment automation. Learn testing strategies, CI/CD, and deployment patterns. Testing ensures reliable pipeline delivery.

|Topic|Focus & Purpose|
|---|---|
|**[[13.1 ETL Testing Types]]**|Unit tests; integration tests; data tests; regression tests. Testing types.|
|**[[13.2 Unit Testing]]**|Testing transformations; mocking; pytest; test fixtures. Unit tests.|
|**[[13.3 Data Testing]]**|Great Expectations; dbt tests; data validation; quality testing. Data tests.|
|**[[13.4 Integration Testing]]**|End-to-end tests; test data; test environments; validation. Integration.|
|**[[13.5 CI/CD for ETL]]**|Pipeline deployment; GitHub Actions; automated testing; promotion. CI/CD.|
|**[[13.6 Environment Management]]**|Dev/staging/prod; configuration management; secrets; promotion. Environments.|
|**[[13.7 Project: CI/CD Pipeline]]**|Automated testing; deployment; promotion; rollback. CI/CD project.|

### **[[14 Real-World Projects]]**

Master building production ETL solutions. Build impressive portfolio pieces demonstrating data engineering expertise. Real projects are essential for landing data engineering positions.

|Topic|Focus & Purpose|
|---|---|
|**[[14.1 Sales Analytics Pipeline]]**|Sales data; aggregations; KPIs; dashboards; reporting. Sales analytics.|
|**[[14.2 Customer 360]]**|Customer data; integration; deduplication; master data; enrichment. Customer data.|
|**[[14.3 Log Analytics]]**|Log ingestion; parsing; aggregation; metrics; monitoring. Log processing.|
|**[[14.4 Marketing Attribution]]**|Touchpoint data; attribution models; campaign analytics. Marketing analytics.|
|**[[14.5 Financial Reporting]]**|Financial data; reconciliation; compliance; audit trails. Financial ETL.|
|**[[14.6 IoT Data Pipeline]]**|Sensor data; time-series; aggregation; anomaly detection. IoT analytics.|
|**[[14.7 Real-Time Dashboard]]**|Streaming ETL; real-time metrics; live dashboards. Real-time.|
|**[[14.8 Production Pipeline]]**|Complete production ETL; monitoring; quality; documentation. Portfolio project.|
