### **[[01 Apache Kafka Fundamentals]]**

Master Apache Kafka as the industry-standard distributed streaming platform. Learn why Kafka powers real-time data pipelines at LinkedIn, Netflix, Uber, and Airbnb. Understand event streaming, message queuing, and the publish-subscribe model that processes trillions of events daily. Kafka developers earn $120k-$170k annually with exceptional demand in data engineering and backend roles. Essential for building scalable, real-time data architectures.

|Topic|Focus & Purpose|
|---|---|
|**[[1.1 Kafka Introduction]]**|What is Kafka; event streaming; message broker vs streaming platform; use cases; market demand; job landscape. Industry context.|
|**[[1.2 Core Concepts]]**|Events/messages; topics; partitions; brokers; clusters; ZooKeeper/KRaft; terminology. Core architecture.|
|**[[1.3 Kafka Architecture]]**|Distributed system; broker architecture; controller; leader/follower; replication; fault tolerance. System design.|
|**[[1.4 Environment Setup]]**|Local installation; Docker setup; Confluent Platform; cloud options; CLI tools. Professional setup.|
|**[[1.5 Kafka CLI]]**|kafka-topics; kafka-console-producer; kafka-console-consumer; kafka-configs; essential commands. Command line.|
|**[[1.6 Kafka vs Alternatives]]**|Kafka vs RabbitMQ; vs AWS SQS/SNS; vs Pulsar; vs Redis Streams; comparison. Platform comparison.|
|**[[1.7 Project: First Kafka Setup]]**|Installing Kafka; creating topics; producing/consuming messages; CLI exploration. First project.|

### **[[02 Topics & Partitions]]**

Master Kafka topics and partitions for data organization. Learn partitioning strategies, replication, and topic management. Topic design is fundamental to Kafka performance and scalability.

|Topic|Focus & Purpose|
|---|---|
|**[[2.1 Topics Deep Dive]]**|Topic concept; topic naming; topic configuration; log-based storage; retention. Topic fundamentals.|
|**[[2.2 Partitions]]**|Partition concept; ordering guarantees; partition count; parallelism; partition strategy. Partition basics.|
|**[[2.3 Partition Keys]]**|Message keys; key-based partitioning; hash partitioning; ordering within partition. Key strategy.|
|**[[2.4 Replication]]**|Replication factor; leader/follower replicas; ISR (In-Sync Replicas); durability. Data redundancy.|
|**[[2.5 Topic Configuration]]**|Retention policies; cleanup policies (delete/compact); segment size; configuration options. Topic settings.|
|**[[2.6 Log Compaction]]**|Compaction concept; compacted topics; key/value retention; use cases; configuration. Data compaction.|
|**[[2.7 Topic Operations]]**|Creating topics; altering topics; deleting topics; describing topics; partition reassignment. Topic management.|
|**[[2.8 Project: Topic Design]]**|Designing topic architecture; partitioning strategy; replication; configuration. Topic project.|

### **[[03 Producers]]**

Master Kafka producers for publishing messages. Learn producer configuration, serialization, and delivery guarantees. Producer skills are essential for sending data to Kafka.

|Topic|Focus & Purpose|
|---|---|
|**[[3.1 Producer Basics]]**|Producer concept; producer API; sending messages; synchronous vs asynchronous. Producer fundamentals.|
|**[[3.2 Producer Configuration]]**|Key configurations; acks; retries; batch.size; linger.ms; buffer.memory. Producer tuning.|
|**[[3.3 Serialization]]**|Key serializers; value serializers; StringSerializer; JSON; Avro; custom serializers. Data serialization.|
|**[[3.4 Partitioning Strategy]]**|Default partitioner; round-robin; key-based; sticky partitioner; custom partitioners. Message routing.|
|**[[3.5 Acknowledgments]]**|acks=0; acks=1; acks=all; durability vs performance; delivery semantics. Delivery guarantees.|
|**[[3.6 Idempotent Producers]]**|Idempotent producer; enable.idempotence; exactly-once semantics; producer ID. Exactly-once.|
|**[[3.7 Error Handling]]**|Retriable errors; non-retriable errors; callbacks; error handling patterns. Producer errors.|
|**[[3.8 Project: Producer Application]]**|Building producer; configuration; serialization; error handling; performance. Producer project.|

### **[[04 Consumers]]**

Master Kafka consumers for reading messages. Learn consumer groups, offsets, and consumption patterns. Consumer skills are essential for processing data from Kafka.

|Topic|Focus & Purpose|
|---|---|
|**[[4.1 Consumer Basics]]**|Consumer concept; consumer API; polling; subscribing; message consumption. Consumer fundamentals.|
|**[[4.2 Consumer Groups]]**|Group concept; group coordination; partition assignment; consumer rebalancing. Consumer groups.|
|**[[4.3 Offset Management]]**|Offset concept; committed offsets; auto-commit; manual commit; offset reset. Offset tracking.|
|**[[4.4 Consumer Configuration]]**|Key configurations; fetch.min.bytes; max.poll.records; session.timeout; heartbeat. Consumer tuning.|
|**[[4.5 Deserialization]]**|Key deserializers; value deserializers; StringDeserializer; JSON; Avro; custom. Data deserialization.|
|**[[4.6 Rebalancing]]**|Rebalance triggers; rebalance protocol; cooperative rebalancing; sticky assignor. Group dynamics.|
|**[[4.7 Consumer Patterns]]**|At-least-once; at-most-once; exactly-once; idempotent consumers; patterns. Consumption semantics.|
|**[[4.8 Project: Consumer Application]]**|Building consumer; groups; offset management; error handling; scaling. Consumer project.|

### **[[05 Kafka with Java]]**

Master Kafka Java client for production applications. Learn producer/consumer APIs, configuration, and best practices. Java is the primary language for Kafka development.

|Topic|Focus & Purpose|
|---|---|
|**[[5.1 Java Client Setup]]**|Maven/Gradle dependencies; kafka-clients; project setup; configuration. Java setup.|
|**[[5.2 Java Producer]]**|KafkaProducer; ProducerRecord; send(); callbacks; Future; configuration. Java producer.|
|**[[5.3 Java Consumer]]**|KafkaConsumer; subscribe(); poll(); ConsumerRecords; commit; configuration. Java consumer.|
|**[[5.4 Serialization]]**|Serializer interface; Deserializer interface; custom implementations; JSON; Avro. Java serialization.|
|**[[5.5 Error Handling]]**|Exception handling; retries; dead letter topics; error recovery; resilience. Java error handling.|
|**[[5.6 Testing]]**|Unit testing; MockProducer; MockConsumer; integration testing; Testcontainers. Java testing.|
|**[[5.7 Spring Kafka]]**|Spring Boot integration; @KafkaListener; KafkaTemplate; configuration; Spring patterns. Spring integration.|
|**[[5.8 Project: Java Application]]**|Building complete Java Kafka app; producer; consumer; Spring Boot; testing. Java project.|

### **[[06 Kafka with Python]]**

Master Kafka Python clients for data engineering. Learn kafka-python and confluent-kafka for Python applications. Python is essential for data engineering and ML pipelines.

|Topic|Focus & Purpose|
|---|---|
|**[[6.1 Python Client Options]]**|kafka-python; confluent-kafka-python; comparison; installation; when to use. Python clients.|
|**[[6.2 confluent-kafka Producer]]**|Producer class; produce(); flush(); callbacks; configuration. Confluent producer.|
|**[[6.3 confluent-kafka Consumer]]**|Consumer class; subscribe(); poll(); commit(); configuration. Confluent consumer.|
|**[[6.4 kafka-python]]**|KafkaProducer; KafkaConsumer; usage patterns; comparison with confluent. Alternative client.|
|**[[6.5 Serialization]]**|JSON serialization; Avro with Python; schema handling; custom serializers. Python serialization.|
|**[[6.6 Async Processing]]**|Async producers; consumer threading; concurrent processing; batch handling. Async patterns.|
|**[[6.7 FastAPI Integration]]**|Kafka with FastAPI; event-driven APIs; async consumers; webhooks. API integration.|
|**[[6.8 Project: Python Pipeline]]**|Building data pipeline; producer; consumer; processing; FastAPI events. Python project.|

### **[[07 Schema Registry & Avro]]**

Master Schema Registry for data governance. Learn Avro schemas, schema evolution, and compatibility. Schema management is critical for production Kafka deployments.

|Topic|Focus & Purpose|
|---|---|
|**[[7.1 Schema Registry Basics]]**|What is Schema Registry; purpose; architecture; schema storage; clients. Registry fundamentals.|
|**[[7.2 Avro Introduction]]**|Apache Avro; schema definition; primitive types; complex types; benefits. Avro basics.|
|**[[7.3 Avro Schemas]]**|Record schemas; fields; defaults; nullables; nested schemas; schema files. Schema definition.|
|**[[7.4 Schema Evolution]]**|Backward compatibility; forward compatibility; full compatibility; breaking changes. Schema changes.|
|**[[7.5 Producer with Schema]]**|Avro serializer; schema registration; producer configuration; auto-registration. Schema producer.|
|**[[7.6 Consumer with Schema]]**|Avro deserializer; schema retrieval; consumer configuration; schema reading. Schema consumer.|
|**[[7.7 Schema Management]]**|Schema subjects; versioning; compatibility settings; schema deletion; governance. Schema lifecycle.|
|**[[7.8 Project: Schema-Driven Pipeline]]**|Building Avro pipeline; schemas; evolution; registry management. Schema project.|

### **[[08 Kafka Connect]]**

Master Kafka Connect for data integration. Learn connectors, source/sink patterns, and data pipelines. Kafka Connect is essential for integrating Kafka with databases and external systems.

|Topic|Focus & Purpose|
|---|---|
|**[[8.1 Connect Fundamentals]]**|Kafka Connect concept; source connectors; sink connectors; Connect clusters. Connect basics.|
|**[[8.2 Connect Architecture]]**|Workers; standalone vs distributed; tasks; converters; transforms. Connect architecture.|
|**[[8.3 Source Connectors]]**|Database sources; JDBC source; Debezium CDC; file sources; custom sources. Data ingestion.|
|**[[8.4 Sink Connectors]]**|Database sinks; Elasticsearch; S3; HDFS; file sinks; custom sinks. Data egress.|
|**[[8.5 Connector Configuration]]**|Connector properties; tasks.max; topic naming; error handling; DLQ. Connector setup.|
|**[[8.6 Transforms (SMT)]]**|Single Message Transforms; built-in transforms; routing; filtering; custom SMTs. Data transformation.|
|**[[8.7 Connect Operations]]**|REST API; connector management; monitoring; scaling; troubleshooting. Connect management.|
|**[[8.8 Project: Data Pipeline]]**|Building Connect pipeline; database ingestion; transformations; sink. Connect project.|

### **[[09 Kafka Streams]]**

Master Kafka Streams for stream processing. Learn stream/table duality, transformations, and stateful processing. Kafka Streams is essential for real-time data processing.

|Topic|Focus & Purpose|
|---|---|
|**[[9.1 Streams Introduction]]**|Kafka Streams library; stream processing concepts; KStream; KTable. Streams basics.|
|**[[9.2 Streams Architecture]]**|Topology; processors; state stores; threading; parallelism; scaling. Streams architecture.|
|**[[9.3 Stream Operations]]**|map(); filter(); flatMap(); branch(); merge(); transformations. Stream transformations.|
|**[[9.4 Table Operations]]**|KTable operations; aggregations; reduce(); groupBy(); materialized views. Table processing.|
|**[[9.5 Joins]]**|KStream-KStream joins; KStream-KTable joins; KTable-KTable joins; window joins. Stream joins.|
|**[[9.6 Windowing]]**|Tumbling windows; hopping windows; sliding windows; session windows; grace period. Time windows.|
|**[[9.7 State Management]]**|State stores; RocksDB; queryable state; interactive queries; state restoration. Stateful processing.|
|**[[9.8 Project: Streaming Application]]**|Building stream processor; aggregations; joins; windowing; state queries. Streams project.|

### **[[10 ksqlDB]]**

Master ksqlDB for SQL-based stream processing. Learn stream queries, tables, and real-time analytics. ksqlDB enables SQL developers to work with streaming data.

|Topic|Focus & Purpose|
|---|---|
|**[[10.1 ksqlDB Introduction]]**|What is ksqlDB; SQL for streams; use cases; architecture; deployment. ksqlDB basics.|
|**[[10.2 Streams & Tables]]**|CREATE STREAM; CREATE TABLE; stream vs table semantics; DDL statements. Data structures.|
|**[[10.3 Queries]]**|SELECT statements; push queries; pull queries; filtering; projections. ksqlDB queries.|
|**[[10.4 Aggregations]]**|GROUP BY; COUNT; SUM; AVG; windowed aggregations; HAVING. Aggregation queries.|
|**[[10.5 Joins]]**|Stream-stream joins; stream-table joins; join windows; join types. ksqlDB joins.|
|**[[10.6 Functions]]**|Built-in functions; custom functions (UDFs); type conversions; string functions. ksqlDB functions.|
|**[[10.7 Materialized Views]]**|Persistent queries; materialized views; queryable tables; use cases. Persistent processing.|
|**[[10.8 Project: Real-time Analytics]]**|Building analytics; streams; aggregations; dashboards; live queries. ksqlDB project.|

### **[[11 Security]]**

Master Kafka security for production deployments. Learn authentication, authorization, and encryption. Security is critical for enterprise Kafka deployments.

|Topic|Focus & Purpose|
|---|---|
|**[[11.1 Security Overview]]**|Security layers; authentication; authorization; encryption; security model. Security fundamentals.|
|**[[11.2 SSL/TLS Encryption]]**|TLS setup; certificates; keystores; truststores; client-broker encryption. Data encryption.|
|**[[11.3 SASL Authentication]]**|SASL mechanisms; PLAIN; SCRAM; GSSAPI (Kerberos); OAUTHBEARER. Authentication.|
|**[[11.4 ACL Authorization]]**|Access Control Lists; kafka-acls; permissions; principals; resource types. Authorization.|
|**[[11.5 Kerberos Integration]]**|Kerberos setup; principals; keytabs; GSSAPI configuration; enterprise auth. Kerberos.|
|**[[11.6 RBAC (Confluent)]]**|Role-Based Access Control; Confluent RBAC; roles; role bindings. Enterprise RBAC.|
|**[[11.7 Audit Logging]]**|Audit logs; event tracking; compliance; monitoring security events. Audit trail.|
|**[[11.8 Project: Secure Cluster]]**|Implementing security; TLS; SASL; ACLs; testing secure access. Security project.|

### **[[12 Operations & Monitoring]]**

Master Kafka operations for production infrastructure. Learn monitoring, metrics, and cluster management. Operations skills are essential for running Kafka at scale.

|Topic|Focus & Purpose|
|---|---|
|**[[12.1 Metrics Overview]]**|JMX metrics; broker metrics; producer metrics; consumer metrics; key metrics. Metrics basics.|
|**[[12.2 Monitoring Tools]]**|Prometheus; Grafana; Confluent Control Center; Kafka Manager; monitoring stack. Monitoring tools.|
|**[[12.3 Key Metrics]]**|Under-replicated partitions; consumer lag; request latency; throughput; disk usage. Critical metrics.|
|**[[12.4 Consumer Lag Monitoring]]**|Lag concept; monitoring lag; kafka-consumer-groups; lag alerting. Consumer monitoring.|
|**[[12.5 Cluster Operations]]**|Rolling restarts; broker replacement; partition reassignment; scaling clusters. Cluster management.|
|**[[12.6 Log Management]]**|Log retention; log cleanup; disk management; tiered storage; S3 integration. Storage management.|
|**[[12.7 Troubleshooting]]**|Common issues; debugging; log analysis; performance issues; recovery. Problem solving.|
|**[[12.8 Project: Monitoring Stack]]**|Building monitoring; Prometheus; Grafana dashboards; alerting; SLOs. Monitoring project.|

### **[[13 Cloud & Managed Kafka]]**

Master managed Kafka services for cloud deployments. Learn Confluent Cloud, AWS MSK, and cloud patterns. Cloud Kafka reduces operational overhead for production deployments.

|Topic|Focus & Purpose|
|---|---|
|**[[13.1 Managed Kafka Options]]**|Confluent Cloud; AWS MSK; Azure Event Hubs; cloud comparison; when to use. Cloud options.|
|**[[13.2 Confluent Cloud]]**|Confluent Cloud setup; clusters; connectors; ksqlDB; Schema Registry; pricing. Confluent platform.|
|**[[13.3 AWS MSK]]**|MSK setup; cluster configuration; provisioned vs serverless; VPC; IAM. Amazon MSK.|
|**[[13.4 Cloud Connect]]**|Managed connectors; cloud connect; source/sink in cloud; self-managed. Cloud integration.|
|**[[13.5 Multi-Region]]**|Cluster linking; multi-region replication; disaster recovery; global deployments. Geographic distribution.|
|**[[13.6 Cost Optimization]]**|Pricing models; throughput optimization; storage costs; right-sizing. Cost management.|
|**[[13.7 Project: Cloud Deployment]]**|Deploying to cloud; managed Kafka; connectors; monitoring; production. Cloud project.|

### **[[14 Advanced Patterns]]**

Master advanced Kafka patterns for complex architectures. Learn event sourcing, CQRS, and microservices patterns. Advanced patterns are required for senior and architect positions.

|Topic|Focus & Purpose|
|---|---|
|**[[14.1 Event Sourcing]]**|Event sourcing pattern; event stores; replay; audit trail; Kafka as event store. Event sourcing.|
|**[[14.2 CQRS]]**|Command Query Responsibility Segregation; read/write separation; materialized views. CQRS pattern.|
|**[[14.3 Saga Pattern]]**|Distributed transactions; choreography; orchestration; compensating actions. Distributed patterns.|
|**[[14.4 Outbox Pattern]]**|Transactional outbox; database + Kafka; Debezium; reliable publishing. Reliability pattern.|
|**[[14.5 Dead Letter Topics]]**|DLT concept; error handling; poison pills; retry patterns; monitoring. Error handling.|
|**[[14.6 Exactly-Once Processing]]**|Transactions; idempotent producers; transactional consumers; end-to-end. Exactly-once.|
|**[[14.7 Microservices Integration]]**|Event-driven microservices; service communication; choreography; shared state. Microservices.|
|**[[14.8 Project: Event-Driven System]]**|Building event-driven architecture; patterns; reliability; scalability. Architecture project.|

### **[[15 Real-World Projects]]**

Master building production Kafka solutions. Build impressive portfolio pieces that demonstrate Kafka expertise. Real projects are essential for landing data engineering and backend positions.

|Topic|Focus & Purpose|
|---|---|
|**[[15.1 Real-Time Analytics]]**|Stream processing; aggregations; dashboards; real-time metrics. Analytics platform.|
|**[[15.2 Log Aggregation]]**|Centralized logging; log collection; processing; Elasticsearch sink. Log pipeline.|
|**[[15.3 Change Data Capture]]**|Debezium CDC; database replication; event streaming; sync systems. CDC pipeline.|
|**[[15.4 IoT Data Pipeline]]**|Sensor data; high-throughput ingestion; time-series processing. IoT streaming.|
|**[[15.5 E-Commerce Events]]**|Order events; inventory updates; notifications; event-driven commerce. E-commerce.|
|**[[15.6 Fraud Detection]]**|Real-time detection; stream processing; pattern matching; alerts. Fraud system.|
|**[[15.7 ETL Pipeline]]**|Extract, Transform, Load; data warehouse loading; batch + stream. ETL system.|
|**[[15.8 Production System]]**|Complete production deployment; monitoring; security; scalability. Portfolio centerpiece.|
