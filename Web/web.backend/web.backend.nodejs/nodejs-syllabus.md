### **[[01 Node.js Fundamentals & Environment]]**

Master Node.js as the industry-standard JavaScript runtime for server-side development. Learn why Node.js powers backends for Netflix, LinkedIn, PayPal, and Uber. Understand event-driven architecture and non-blocking I/O that make Node.js ideal for scalable applications. Node.js developers earn $95k-$140k annually with exceptional demand. Essential for full-stack JavaScript and backend development careers. This module builds the foundation for production-ready Node.js skills.

|Topic|Focus & Purpose|
|---|---|
|**[[1.1 Node.js Introduction]]**|What is Node.js; V8 engine; JavaScript runtime; Node.js vs browser JS; event-driven architecture; market demand; job landscape. Industry context.|
|**[[1.2 Environment Setup]]**|Node.js installation; NVM (Node Version Manager); npm vs yarn vs pnpm; VS Code setup; debugging configuration; terminal setup. Professional setup.|
|**[[1.3 Node.js Architecture]]**|Event loop; single-threaded model; non-blocking I/O; libuv; call stack; callback queue; microtasks. Core concepts.|
|**[[1.4 Node.js REPL]]**|REPL environment; interactive debugging; executing scripts; module testing; quick prototyping. Development tool.|
|**[[1.5 Global Objects]]**|global object; process; __dirname; __filename; Buffer; setTimeout; setInterval; console. Built-in globals.|
|**[[1.6 Command Line Arguments]]**|process.argv; parsing arguments; CLI tools basics; environment variables; process.env. Script inputs.|
|**[[1.7 Project: CLI Calculator]]**|Building first Node.js app; command line input; basic operations; error handling; user feedback. First project.|

### **[[02 Modules & Package Management]]**

Master Node.js module system and npm ecosystem. Learn CommonJS, ES Modules, package management, and dependency handling. Module mastery is fundamental for all Node.js development and code organization in production applications.

|Topic|Focus & Purpose|
|---|---|
|**[[2.1 CommonJS Modules]]**|require() function; module.exports; exports object; module caching; circular dependencies. Traditional modules.|
|**[[2.2 ES Modules]]**|import/export syntax; .mjs files; package.json type; named exports; default exports; dynamic imports. Modern modules.|
|**[[2.3 Built-in Modules]]**|Core modules overview; path; os; url; util; querystring; crypto; module exploration. Standard library.|
|**[[2.4 npm Fundamentals]]**|npm init; package.json; installing packages; local vs global; scripts; npx; npm registry. Package management.|
|**[[2.5 Dependency Management]]**|Semantic versioning; package-lock.json; dependencies vs devDependencies; peer dependencies; version ranges. Version control.|
|**[[2.6 Creating npm Packages]]**|Package structure; publishing to npm; private packages; scoped packages; versioning; documentation. Publishing modules.|
|**[[2.7 Project: Utility Library]]**|Building reusable module; multiple exports; testing; documentation; npm publishing preparation. Module project.|

### **[[03 Asynchronous Programming]]**

Master asynchronous patterns critical for Node.js performance. Learn callbacks, Promises, async/await, and error handling. Async programming is the most important concept for Node.js developers and tested in every backend interview.

|Topic|Focus & Purpose|
|---|---|
|**[[3.1 Callback Pattern]]**|Callback functions; error-first callbacks; callback hell; nested callbacks; callback conventions. Traditional async.|
|**[[3.2 Promises]]**|Promise creation; resolve/reject; then/catch; Promise chaining; Promise.all; Promise.race; Promise.allSettled. Modern async.|
|**[[3.3 Async/Await]]**|async functions; await keyword; error handling; sequential vs parallel; top-level await. Clean async code.|
|**[[3.4 Event Emitter]]**|EventEmitter class; on/emit methods; custom events; once; removing listeners; error events. Event-driven patterns.|
|**[[3.5 Timers & Scheduling]]**|setTimeout; setInterval; setImmediate; process.nextTick; timer patterns; scheduling tasks. Timing operations.|
|**[[3.6 Error Handling]]**|Try/catch with async; uncaughtException; unhandledRejection; error propagation; error recovery; graceful shutdown. Robust error handling.|
|**[[3.7 Project: Async Task Queue]]**|Building task queue; Promise handling; concurrent execution; rate limiting; progress tracking. Async patterns project.|

### **[[04 File System & Streams]]**

Master file operations and streaming for efficient data processing. Learn fs module, streams, buffers, and large file handling. File system skills are essential for backend applications, data processing, and server operations.

|Topic|Focus & Purpose|
|---|---|
|**[[4.1 File System Basics]]**|fs module; sync vs async methods; reading files; writing files; file stats; file existence. Basic file operations.|
|**[[4.2 Directory Operations]]**|Creating directories; reading directories; recursive operations; watching directories; temp directories. Directory handling.|
|**[[4.3 File Paths]]**|path module; path.join; path.resolve; path.dirname; path.basename; path.extname; cross-platform paths. Path manipulation.|
|**[[4.4 Streams Introduction]]**|Stream concept; readable streams; writable streams; stream events; pipe method; stream advantages. Streaming basics.|
|**[[4.5 Stream Types]]**|Readable; Writable; Duplex; Transform streams; creating custom streams; stream modes. Stream varieties.|
|**[[4.6 Buffer & Binary Data]]**|Buffer class; creating buffers; buffer operations; encoding; binary data handling; buffer performance. Binary processing.|
|**[[4.7 Large File Processing]]**|Streaming large files; memory efficiency; CSV processing; line-by-line reading; progress tracking. Scalable file handling.|
|**[[4.8 Project: File Manager CLI]]**|Building file manager; copy/move/delete; directory traversal; search; streaming; progress display. File system project.|

### **[[05 HTTP & Web Servers]]**

Master HTTP fundamentals and web server creation. Learn the http module, request/response handling, and server architecture. Building web servers is the core skill for Node.js backend development and web API creation.

|Topic|Focus & Purpose|
|---|---|
|**[[5.1 HTTP Module Basics]]**|http.createServer; request object; response object; status codes; headers; content types. Server foundation.|
|**[[5.2 Routing]]**|URL parsing; method routing; route handlers; query parameters; route organization; 404 handling. Request routing.|
|**[[5.3 Request Body Parsing]]**|Parsing POST data; JSON body; form data; multipart handling; body size limits; content-type handling. Input processing.|
|**[[5.4 Response Handling]]**|Sending responses; JSON responses; HTML responses; file serving; redirects; streaming responses. Output handling.|
|**[[5.5 HTTPS & Security]]**|https module; SSL certificates; creating HTTPS server; security headers; secure cookies. Secure servers.|
|**[[5.6 Static File Serving]]**|Serving static files; MIME types; caching headers; directory listing; security considerations. Asset serving.|
|**[[5.7 Server Events]]**|Server events; connection handling; error events; server lifecycle; graceful shutdown. Server management.|
|**[[5.8 Project: REST API Server]]**|Building REST API; CRUD operations; routing; error handling; validation; documentation. Vanilla Node.js API.|

### **[[06 Express.js Framework]]**

Master Express.js as the most popular Node.js web framework. Learn middleware, routing, error handling, and best practices. Express.js is required knowledge for 90% of Node.js job postings and essential for professional backend development.

|Topic|Focus & Purpose|
|---|---|
|**[[6.1 Express Fundamentals]]**|Express setup; app object; basic routing; route methods; route paths; response methods. Framework basics.|
|**[[6.2 Middleware]]**|Middleware concept; app.use; next function; request modification; middleware ordering; third-party middleware. Core Express pattern.|
|**[[6.3 Routing]]**|Router object; route parameters; query strings; route grouping; route modules; RESTful routes. URL handling.|
|**[[6.4 Request & Response]]**|req object; res object; request properties; response methods; chaining; content negotiation. HTTP handling.|
|**[[6.5 Error Handling]]**|Error middleware; async errors; error classes; centralized error handling; error responses; production errors. Robust applications.|
|**[[6.6 Template Engines]]**|View engines; EJS; Pug; Handlebars; rendering views; passing data; partials; layouts. Server-side rendering.|
|**[[6.7 Static Files & Assets]]**|express.static; multiple directories; virtual paths; caching; compression; serving optimization. Asset delivery.|
|**[[6.8 Project: Blog Backend]]**|Building blog API; full CRUD; middleware stack; error handling; validation; structured codebase. Express project.|

### **[[07 Database Integration]]**

Master database connections and operations in Node.js. Learn SQL (PostgreSQL/MySQL) and NoSQL (MongoDB) databases with ORMs. Database skills are essential for all backend positions and data-driven applications.

|Topic|Focus & Purpose|
|---|---|
|**[[7.1 Database Options]]**|SQL vs NoSQL; PostgreSQL; MySQL; MongoDB; SQLite; database selection criteria; hosted solutions. Choosing databases.|
|**[[7.2 MongoDB & Mongoose]]**|MongoDB setup; Mongoose ODM; schemas; models; CRUD operations; queries; validation; indexes. NoSQL database.|
|**[[7.3 PostgreSQL & Sequelize]]**|PostgreSQL setup; Sequelize ORM; models; migrations; associations; queries; transactions. SQL database.|
|**[[7.4 Prisma ORM]]**|Prisma setup; schema definition; Prisma Client; migrations; relations; type safety; queries. Modern ORM.|
|**[[7.5 Query Building]]**|Complex queries; filtering; sorting; pagination; aggregation; joins; optimization. Advanced queries.|
|**[[7.6 Database Relationships]]**|One-to-one; one-to-many; many-to-many; foreign keys; population; eager loading. Data relationships.|
|**[[7.7 Connection Pooling]]**|Pool management; connection limits; pool configuration; error handling; performance tuning. Connection optimization.|
|**[[7.8 Project: E-Commerce Database]]**|Building complete schema; products; users; orders; relationships; queries; seeding. Database project.|

### **[[08 Authentication & Security]]**

Master authentication implementation and security best practices. Learn JWT, sessions, OAuth, password hashing, and security headers. Authentication is required for almost all production applications and frequently tested in interviews.

|Topic|Focus & Purpose|
|---|---|
|**[[8.1 Authentication Basics]]**|Authentication vs authorization; session vs token based; security fundamentals; threat models. Auth concepts.|
|**[[8.2 Password Security]]**|Password hashing; bcrypt; argon2; salt; secure comparison; password policies; storage best practices. Credential security.|
|**[[8.3 JWT Authentication]]**|JWT structure; signing tokens; verifying tokens; token expiration; refresh tokens; token storage. Token-based auth.|
|**[[8.4 Session Authentication]]**|Express sessions; session stores (Redis, MongoDB); session configuration; secure sessions. Session-based auth.|
|**[[8.5 OAuth 2.0 & Passport]]**|Passport.js; strategies; Google OAuth; GitHub OAuth; social login; strategy configuration. Third-party auth.|
|**[[8.6 Authorization & RBAC]]**|Role-based access; permissions; middleware guards; resource authorization; policy patterns. Access control.|
|**[[8.7 Security Best Practices]]**|Helmet.js; CORS; rate limiting; input sanitization; SQL injection; XSS prevention; CSRF protection. Security hardening.|
|**[[8.8 Project: Auth System]]**|Complete auth system; JWT + refresh tokens; password reset; email verification; protected routes. Auth project.|

### **[[09 API Design & Development]]**

Master RESTful API design and implementation. Learn API conventions, documentation, versioning, and best practices. API development is the primary job function for Node.js backend developers.

|Topic|Focus & Purpose|
|---|---|
|**[[9.1 REST API Principles]]**|REST constraints; resource design; HTTP methods; status codes; HATEOAS; API conventions. API architecture.|
|**[[9.2 Request Validation]]**|Input validation; Joi; express-validator; Zod; schema validation; sanitization; error messages. Data validation.|
|**[[9.3 Response Formatting]]**|Response structure; JSON:API; envelope pattern; pagination; filtering; sorting; error responses. Consistent responses.|
|**[[9.4 API Versioning]]**|Versioning strategies; URL versioning; header versioning; deprecation; backward compatibility. API evolution.|
|**[[9.5 API Documentation]]**|Swagger/OpenAPI; JSDoc; API documentation tools; interactive docs; schema generation. Documentation.|
|**[[9.6 Rate Limiting & Throttling]]**|Rate limiting implementation; express-rate-limit; Redis-based limiting; API quotas; abuse prevention. Traffic control.|
|**[[9.7 GraphQL Introduction]]**|GraphQL basics; queries; mutations; resolvers; Apollo Server; GraphQL vs REST; when to use. Alternative API.|
|**[[9.8 Project: RESTful API]]**|Building production API; full CRUD; validation; documentation; versioning; testing. Complete API project.|

### **[[10 Real-Time Communication]]**

Master real-time features with WebSockets and Socket.io. Learn bidirectional communication, rooms, and event handling. Real-time skills are essential for chat applications, notifications, and collaborative tools.

|Topic|Focus & Purpose|
|---|---|
|**[[10.1 WebSocket Fundamentals]]**|WebSocket protocol; ws library; handshake; messages; connection lifecycle; binary data. Raw WebSockets.|
|**[[10.2 Socket.io Basics]]**|Socket.io setup; emit/on; namespaces; acknowledgments; connection events. Popular WebSocket library.|
|**[[10.3 Rooms & Broadcasting]]**|Joining rooms; leaving rooms; room broadcasting; private messaging; group communication. Room management.|
|**[[10.4 Real-Time Events]]**|Custom events; event patterns; typing indicators; presence; offline handling; reconnection. Event handling.|
|**[[10.5 Socket Authentication]]**|Socket.io auth middleware; JWT with sockets; session integration; secure connections. Authenticated sockets.|
|**[[10.6 Scaling WebSockets]]**|Socket.io Redis adapter; sticky sessions; horizontal scaling; load balancing; cluster mode. Scalable real-time.|
|**[[10.7 Project: Chat Application]]**|Building real-time chat; rooms; private messages; typing indicators; message history; online status. Real-time project.|

### **[[11 Testing Node.js Applications]]**

Master testing strategies for Node.js applications. Learn unit testing, integration testing, and API testing. Testing skills are increasingly required for senior positions and essential for production-quality code.

|Topic|Focus & Purpose|
|---|---|
|**[[11.1 Testing Fundamentals]]**|Testing pyramid; unit vs integration vs E2E; TDD vs BDD; test organization; when to test. Testing strategy.|
|**[[11.2 Jest Fundamentals]]**|Jest setup; test functions; expect assertions; describe blocks; beforeEach/afterEach; mocking. Test framework.|
|**[[11.3 Unit Testing]]**|Testing pure functions; mocking dependencies; testing classes; isolation; code coverage. Unit tests.|
|**[[11.4 Integration Testing]]**|Testing with database; supertest; API testing; test database; setup/teardown; fixtures. Integration tests.|
|**[[11.5 Mocking & Stubbing]]**|Jest mocks; mocking modules; spy functions; stub implementations; mock database; external services. Test doubles.|
|**[[11.6 API Testing]]**|Supertest library; testing endpoints; authentication in tests; response validation; edge cases. HTTP testing.|
|**[[11.7 Test Coverage]]**|Code coverage reports; coverage thresholds; identifying gaps; meaningful coverage; CI integration. Coverage analysis.|
|**[[11.8 Project: Tested API]]**|Building fully tested API; unit tests; integration tests; 80%+ coverage; CI pipeline. Testing project.|

### **[[12 Error Handling & Logging]]**

Master error handling and logging for production applications. Learn error management, logging strategies, and debugging. Proper error handling is crucial for maintainable applications and production stability.

|Topic|Focus & Purpose|
|---|---|
|**[[12.1 Error Types]]**|Operational vs programmer errors; custom error classes; error inheritance; error codes. Error classification.|
|**[[12.2 Centralized Error Handling]]**|Error handling middleware; async error handling; error wrapper functions; global error handlers. Error architecture.|
|**[[12.3 Logging Basics]]**|Console methods; Winston logger; log levels (error, warn, info, debug); log formatting. Logging fundamentals.|
|**[[12.4 Production Logging]]**|Log files; log rotation; structured logging (JSON); correlation IDs; request logging. Production logs.|
|**[[12.5 Monitoring & Alerting]]**|Error tracking (Sentry); APM (New Relic, DataDog); alerting; health checks; uptime monitoring. Observability.|
|**[[12.6 Debugging Techniques]]**|Node.js debugger; Chrome DevTools; debugging async code; memory debugging; performance profiling. Debugging.|
|**[[12.7 Project: Logging System]]**|Implementing production logging; Winston setup; log rotation; error tracking integration. Logging project.|

### **[[13 Performance & Optimization]]**

Master Node.js performance optimization techniques. Learn profiling, memory management, caching, and scaling. Performance skills are critical for handling production traffic and frequently tested in senior interviews.

|Topic|Focus & Purpose|
|---|---|
|**[[13.1 Performance Profiling]]**|Node.js profiler; Chrome DevTools profiling; flame graphs; identifying bottlenecks; benchmarking. Performance analysis.|
|**[[13.2 Memory Management]]**|V8 memory model; garbage collection; memory leaks; heap snapshots; memory optimization. Memory efficiency.|
|**[[13.3 Caching Strategies]]**|In-memory caching; Redis caching; cache invalidation; cache patterns; HTTP caching. Cache optimization.|
|**[[13.4 Clustering]]**|Cluster module; worker processes; load distribution; zero-downtime restarts; PM2 cluster mode. Multi-core usage.|
|**[[13.5 Worker Threads]]**|Worker threads module; CPU-intensive tasks; thread communication; thread pools; when to use. Parallel processing.|
|**[[13.6 Database Optimization]]**|Query optimization; indexing; connection pooling; N+1 problems; query caching; slow query logging. Database performance.|
|**[[13.7 Load Testing]]**|Artillery; Apache JMeter; load testing strategies; stress testing; capacity planning; benchmarks. Performance testing.|
|**[[13.8 Project: Performance Audit]]**|Optimizing existing app; profiling; caching; database optimization; measuring improvements. Optimization project.|

### **[[14 Deployment & DevOps]]**

Master Node.js deployment and DevOps practices. Learn Docker, cloud platforms, CI/CD, and production management. Deployment knowledge is essential for all backend developers and frequently tested in interviews.

|Topic|Focus & Purpose|
|---|---|
|**[[14.1 Production Preparation]]**|Environment configuration; secrets management; security hardening; dependency audit; production checklist. Production readiness.|
|**[[14.2 Docker & Containers]]**|Dockerfile for Node.js; multi-stage builds; docker-compose; container best practices; production images. Containerization.|
|**[[14.3 Cloud Deployment]]**|AWS (EC2, ECS, Lambda); Google Cloud; Heroku; DigitalOcean; Railway; Render; platform comparison. Cloud hosting.|
|**[[14.4 PM2 & Process Management]]**|PM2 setup; process management; clustering; logs; monitoring; zero-downtime reload; ecosystem file. Process manager.|
|**[[14.5 CI/CD Pipelines]]**|GitHub Actions; GitLab CI; automated testing; build pipelines; deployment automation; rollback strategies. CI/CD.|
|**[[14.6 Nginx & Reverse Proxy]]**|Nginx configuration; reverse proxy; load balancing; SSL termination; caching; security. Web server.|
|**[[14.7 Monitoring & Health]]**|Health check endpoints; liveness/readiness probes; metrics collection; Prometheus; Grafana. Production monitoring.|
|**[[14.8 Project: Production Deployment]]**|Complete deployment; Docker; CI/CD; Nginx; SSL; monitoring; zero-downtime. Deployment project.|

### **[[15 Advanced Patterns & Architecture]]**

Master advanced Node.js patterns and architectures. Learn microservices, event-driven architecture, and enterprise patterns. Advanced patterns are required for senior-level positions and large-scale applications.

|Topic|Focus & Purpose|
|---|---|
|**[[15.1 Clean Architecture]]**|Layered architecture; separation of concerns; dependency injection; SOLID principles; code organization. Code architecture.|
|**[[15.2 Microservices Basics]]**|Microservices concept; service decomposition; communication patterns; service boundaries; when to use. Distributed systems.|
|**[[15.3 Message Queues]]**|RabbitMQ; Redis Pub/Sub; Bull queue; async communication; job processing; event sourcing. Async messaging.|
|**[[15.4 Event-Driven Architecture]]**|Event patterns; event emitters; domain events; event sourcing; CQRS basics; decoupling. Event architecture.|
|**[[15.5 API Gateway Pattern]]**|Gateway concept; request routing; aggregation; rate limiting; authentication; Kong; Express gateway. Gateway pattern.|
|**[[15.6 Cron Jobs & Scheduling]]**|Node-cron; agenda; scheduled tasks; recurring jobs; job persistence; distributed scheduling. Task scheduling.|
|**[[15.7 Background Processing]]**|Background jobs; job queues; Bull; Agenda; worker processes; job retries; failure handling. Async processing.|
|**[[15.8 Project: Microservices App]]**|Building microservices; API gateway; message queue; service communication; deployment. Architecture project.|

### **[[16 Real-World Projects]]**

Master building production-grade Node.js applications. Learn complete project workflows from design to deployment. Build impressive portfolio pieces that demonstrate job-ready backend skills. Real projects are essential for landing Node.js positions.

|Topic|Focus & Purpose|
|---|---|
|**[[16.1 REST API Backend]]**|Complete REST API; authentication; authorization; validation; documentation; testing; deployment. API project.|
|**[[16.2 E-Commerce Backend]]**|Product management; cart system; checkout; payment integration (Stripe); order processing; inventory. E-commerce backend.|
|**[[16.3 Social Media Backend]]**|User profiles; posts; comments; likes; follows; feed algorithm; notifications; media uploads. Social platform.|
|**[[16.4 SaaS Backend]]**|Multi-tenancy; subscription billing; usage tracking; admin dashboard API; webhooks; integrations. SaaS architecture.|
|**[[16.5 Real-Time Analytics]]**|Event ingestion; data processing; aggregation; real-time dashboards; WebSocket updates. Analytics system.|
|**[[16.6 Task Scheduler System]]**|Job scheduling; recurring tasks; webhook delivery; retry logic; monitoring; admin interface. Scheduling system.|
|**[[16.7 Content Management API]]**|Headless CMS; content modeling; media management; versioning; publishing workflow; API design. CMS backend.|
|**[[16.8 Production Backend]]**|Complete production system; all features; security; performance; monitoring; documentation. Portfolio centerpiece.|
