### **[[01 Express.js Fundamentals & Setup]]**

Master Express.js as the most popular Node.js web framework powering millions of applications. Learn why Express.js is the backbone of companies like IBM, Uber, and Accenture. Understand middleware architecture, routing, and the minimalist philosophy that makes Express the go-to choice for APIs and web applications. Express.js developers earn $90k-$130k annually with exceptional demand. Essential for backend JavaScript development and full-stack careers.

|Topic|Focus & Purpose|
|---|---|
|**[[1.1 Express.js Introduction]]**|What is Express.js; framework philosophy; Express vs other frameworks; ecosystem overview; market demand; job landscape. Industry context.|
|**[[1.2 Environment Setup]]**|Node.js setup; npm init; installing Express; project structure; nodemon; VS Code configuration; debugging setup. Professional setup.|
|**[[1.3 First Express Server]]**|Creating app; app.listen; basic routing; request/response objects; running server; testing endpoints. Getting started.|
|**[[1.4 Express Application Object]]**|app object; app methods; app settings; app.locals; application lifecycle. Core Express object.|
|**[[1.5 HTTP Methods]]**|GET; POST; PUT; PATCH; DELETE; HEAD; OPTIONS; method routing; RESTful basics. HTTP handling.|
|**[[1.6 Development Workflow]]**|Nodemon; environment variables; dotenv; debugging; error messages; development best practices. Dev experience.|
|**[[1.7 Project: Hello World API]]**|Building first API; multiple routes; JSON responses; testing with Postman/Thunder Client. First project.|

### **[[02 Routing]]**

Master Express routing for handling application URLs. Learn route parameters, query strings, and route organization. Routing is fundamental for building any Express application and structuring your API endpoints.

|Topic|Focus & Purpose|
|---|---|
|**[[2.1 Basic Routing]]**|Route methods; route paths; route handlers; route matching; multiple handlers. Route basics.|
|**[[2.2 Route Parameters]]**|:param syntax; req.params; multiple parameters; optional parameters; regex patterns. Dynamic routes.|
|**[[2.3 Query Strings]]**|req.query; parsing query parameters; filtering; sorting; pagination parameters. Query handling.|
|**[[2.4 Route Paths]]**|String paths; string patterns; regex paths; path matching rules; wildcards. Path patterns.|
|**[[2.5 express.Router]]**|Router object; modular routes; route mounting; router middleware; code organization. Modular routing.|
|**[[2.6 Route Chaining]]**|app.route(); chained handlers; multiple methods; route grouping. Efficient routing.|
|**[[2.7 Route Organization]]**|File structure; route modules; controller pattern; separating concerns; scalable routing. Architecture.|
|**[[2.8 Project: Blog Routes]]**|Building blog API routes; CRUD endpoints; nested resources; organized structure. Routing project.|

### **[[03 Middleware]]**

Master Express middleware as the core architectural pattern. Learn middleware execution, built-in middleware, and custom middleware creation. Middleware understanding is essential for all Express development and the most tested concept in interviews.

|Topic|Focus & Purpose|
|---|---|
|**[[3.1 Middleware Concept]]**|What is middleware; request-response cycle; next function; middleware chain; execution order. Core concept.|
|**[[3.2 Application Middleware]]**|app.use(); path-specific middleware; mounting; middleware ordering; global middleware. App-level middleware.|
|**[[3.3 Router Middleware]]**|router.use(); scoped middleware; route-specific; middleware isolation. Router-level middleware.|
|**[[3.4 Built-in Middleware]]**|express.json(); express.urlencoded(); express.static(); express.raw(); configuration. Express middleware.|
|**[[3.5 Third-Party Middleware]]**|cors; helmet; morgan; compression; cookie-parser; essential packages. Popular middleware.|
|**[[3.6 Custom Middleware]]**|Creating middleware; request modification; logging; timing; validation middleware. Building middleware.|
|**[[3.7 Error Middleware]]**|Error-handling middleware; four-argument signature; async errors; error propagation. Error handling.|
|**[[3.8 Project: Middleware Stack]]**|Building complete middleware stack; logging; auth; validation; error handling. Middleware project.|

### **[[04 Request & Response]]**

Master Express request and response objects for HTTP handling. Learn all request properties, response methods, and data handling. Request/response mastery is critical for building robust APIs.

|Topic|Focus & Purpose|
|---|---|
|**[[4.1 Request Object]]**|req properties; req.body; req.params; req.query; req.headers; req.cookies; req.ip. Request data.|
|**[[4.2 Request Body Parsing]]**|JSON parsing; URL-encoded; raw body; text body; content-type handling; body limits. Input parsing.|
|**[[4.3 Response Object]]**|res methods; res.send(); res.json(); res.status(); res.set(); method chaining. Response sending.|
|**[[4.4 Response Types]]**|JSON responses; HTML; files; streams; downloads; redirects; response formats. Output types.|
|**[[4.5 Headers]]**|Request headers; response headers; content-type; custom headers; CORS headers. HTTP headers.|
|**[[4.6 Cookies]]**|res.cookie(); req.cookies; cookie options; signed cookies; cookie security. Cookie handling.|
|**[[4.7 Content Negotiation]]**|Accept headers; res.format(); content types; media types; response formatting. Content types.|
|**[[4.8 Project: Request Handler]]**|Complete request handling; all input types; various responses; headers; cookies. Request project.|

### **[[05 Template Engines & Views]]**

Master server-side rendering with Express template engines. Learn EJS, Pug, Handlebars, and view configuration. Template skills are valuable for full-stack applications and traditional web development.

|Topic|Focus & Purpose|
|---|---|
|**[[5.1 View Engine Setup]]**|app.set('view engine'); app.set('views'); configuration; multiple engines. View configuration.|
|**[[5.2 EJS Templating]]**|EJS syntax; <% %>; interpolation; conditionals; loops; partials; includes. EJS templates.|
|**[[5.3 Pug Templating]]**|Pug syntax; indentation; attributes; conditionals; loops; mixins; inheritance. Pug templates.|
|**[[5.4 Handlebars]]**|Handlebars setup; expressions; helpers; partials; layouts; logic-less templates. Handlebars templates.|
|**[[5.5 Passing Data to Views]]**|res.render(); local variables; res.locals; app.locals; dynamic data. Data binding.|
|**[[5.6 Layouts & Partials]]**|Layout patterns; header/footer partials; template inheritance; reusable components. Template structure.|
|**[[5.7 Project: Blog Frontend]]**|Building blog UI; template engine; layouts; partials; dynamic rendering. Template project.|

### **[[06 Static Files & Assets]]**

Master serving static files in Express applications. Learn express.static, asset optimization, and CDN integration. Static file handling is essential for web applications with frontend assets.

|Topic|Focus & Purpose|
|---|---|
|**[[6.1 express.static Basics]]**|Static middleware; serving directory; virtual paths; options; index files. Static serving.|
|**[[6.2 Multiple Directories]]**|Multiple static paths; precedence; public folder; assets organization. Directory structure.|
|**[[6.3 Cache Control]]**|maxAge option; cache headers; ETags; cache strategies; production caching. Cache optimization.|
|**[[6.4 Asset Organization]]**|CSS; JavaScript; images; fonts; folder structure; naming conventions. Asset management.|
|**[[6.5 File Downloads]]**|res.download(); content-disposition; streaming; large files; download handling. File delivery.|
|**[[6.6 CDN Integration]]**|CDN concepts; asset URLs; environment-based paths; production assets. CDN usage.|
|**[[6.7 Project: Static Website]]**|Serving complete frontend; assets; optimization; caching; production setup. Static project.|

### **[[07 Error Handling]]**

Master error handling for robust Express applications. Learn error middleware, async errors, and error responses. Proper error handling is crucial for production applications and debugging.

|Topic|Focus & Purpose|
|---|---|
|**[[7.1 Error Handling Basics]]**|Error types; throwing errors; error propagation; try-catch; error-first callbacks. Error fundamentals.|
|**[[7.2 Error Middleware]]**|Four-argument signature; error handler placement; multiple error handlers; error response. Error middleware.|
|**[[7.3 Async Error Handling]]**|Async/await errors; express-async-handler; wrapper functions; Promise rejections. Async errors.|
|**[[7.4 Custom Error Classes]]**|Error classes; AppError; status codes; operational errors; error inheritance. Error types.|
|**[[7.5 Error Responses]]**|Error response format; stack traces; production vs development; client-friendly errors. Error output.|
|**[[7.6 404 Handling]]**|Not found middleware; custom 404 pages; route not found; catch-all routes. Missing routes.|
|**[[7.7 Centralized Error Handler]]**|Global error handler; error logging; error reporting; Sentry integration. Unified handling.|
|**[[7.8 Project: Robust Error System]]**|Complete error handling; custom errors; logging; production-ready errors. Error project.|

### **[[08 Database Integration]]**

Master database connectivity in Express applications. Learn MongoDB, PostgreSQL, ORMs, and query patterns. Database integration is essential for all data-driven Express applications.

|Topic|Focus & Purpose|
|---|---|
|**[[8.1 Database Options]]**|SQL vs NoSQL; MongoDB; PostgreSQL; MySQL; SQLite; database selection. Database choice.|
|**[[8.2 MongoDB & Mongoose]]**|Mongoose setup; schemas; models; CRUD operations; validation; indexes. MongoDB integration.|
|**[[8.3 PostgreSQL & Sequelize]]**|Sequelize setup; models; migrations; associations; queries; transactions. SQL integration.|
|**[[8.4 Prisma ORM]]**|Prisma setup; schema; migrations; Prisma Client; type safety; queries. Modern ORM.|
|**[[8.5 Connection Management]]**|Connection strings; connection pooling; error handling; reconnection; environment config. Connection handling.|
|**[[8.6 Query Patterns]]**|CRUD operations; filtering; sorting; pagination; aggregation; optimization. Data queries.|
|**[[8.7 Transactions]]**|Transaction basics; ACID; MongoDB transactions; SQL transactions; rollback. Data integrity.|
|**[[8.8 Project: Database API]]**|Building CRUD API; database integration; relationships; queries; validation. Database project.|

### **[[09 Authentication & Security]]**

Master authentication and security for Express applications. Learn JWT, sessions, Passport.js, and security best practices. Authentication is required for most production applications and frequently tested in interviews.

|Topic|Focus & Purpose|
|---|---|
|**[[9.1 Authentication Concepts]]**|Authentication vs authorization; session vs token; security fundamentals. Auth concepts.|
|**[[9.2 Password Handling]]**|bcrypt; password hashing; salt; comparison; password policies; security. Credential security.|
|**[[9.3 JWT Authentication]]**|jsonwebtoken library; signing; verifying; expiration; refresh tokens. Token-based auth.|
|**[[9.4 Session Authentication]]**|express-session; session stores; Redis; configuration; session security. Session-based auth.|
|**[[9.5 Passport.js]]**|Passport setup; strategies; local strategy; OAuth strategies; serialization. Auth framework.|
|**[[9.6 OAuth Implementation]]**|OAuth 2.0; Google OAuth; GitHub OAuth; social login flows; callback handling. Social auth.|
|**[[9.7 Security Middleware]]**|Helmet; CORS; rate limiting; sanitization; XSS prevention; CSRF protection. Security hardening.|
|**[[9.8 Project: Auth System]]**|Complete auth system; JWT; refresh tokens; protected routes; OAuth. Auth project.|

### **[[10 API Development]]**

Master RESTful API development with Express. Learn API design, documentation, versioning, and best practices. API development is the primary use case for Express in modern applications.

|Topic|Focus & Purpose|
|---|---|
|**[[10.1 REST Principles]]**|REST architecture; resources; HTTP methods; status codes; HATEOAS. API design.|
|**[[10.2 API Response Format]]**|JSON responses; response structure; envelope pattern; error format; consistency. Response design.|
|**[[10.3 Input Validation]]**|Joi; express-validator; Zod; schema validation; error messages; sanitization. Data validation.|
|**[[10.4 Pagination]]**|Offset pagination; cursor pagination; limit/skip; page numbers; metadata. Paginated results.|
|**[[10.5 Filtering & Sorting]]**|Query parameters; filtering logic; sort fields; order direction; complex filters. Data filtering.|
|**[[10.6 API Versioning]]**|URL versioning; header versioning; version management; deprecation. API evolution.|
|**[[10.7 API Documentation]]**|Swagger/OpenAPI; swagger-jsdoc; swagger-ui-express; API documentation. Documentation.|
|**[[10.8 Project: RESTful API]]**|Complete REST API; validation; documentation; pagination; versioning. API project.|

### **[[11 File Upload & Handling]]**

Master file uploads in Express applications. Learn Multer, file validation, storage, and cloud integration. File handling is common in production applications with user-generated content.

|Topic|Focus & Purpose|
|---|---|
|**[[11.1 Multer Basics]]**|Multer setup; single file; multiple files; file fields; memory storage. Upload handling.|
|**[[11.2 Storage Configuration]]**|Disk storage; destination; filename; storage engines; custom storage. File storage.|
|**[[11.3 File Validation]]**|File type validation; file size limits; MIME types; custom validators. Upload security.|
|**[[11.4 Image Processing]]**|Sharp library; resizing; format conversion; thumbnails; image optimization. Image handling.|
|**[[11.5 Cloud Storage]]**|AWS S3; Cloudinary; Google Cloud Storage; cloud upload patterns. Cloud integration.|
|**[[11.6 Streaming Uploads]]**|Stream handling; large files; progress tracking; chunked uploads. Large files.|
|**[[11.7 Project: Upload System]]**|Complete upload system; validation; processing; cloud storage; thumbnails. Upload project.|

### **[[12 Testing Express Applications]]**

Master testing for Express applications. Learn Jest, Supertest, and testing strategies. Testing skills are essential for production-quality code and professional development.

|Topic|Focus & Purpose|
|---|---|
|**[[12.1 Testing Fundamentals]]**|Testing types; unit vs integration; testing strategy; test organization. Testing basics.|
|**[[12.2 Jest Setup]]**|Jest configuration; test scripts; watch mode; coverage; setup files. Test framework.|
|**[[12.3 Supertest]]**|HTTP testing; request chaining; response assertions; authentication in tests. HTTP testing.|
|**[[12.4 Unit Testing]]**|Testing middleware; testing utilities; mocking; isolation; pure functions. Unit tests.|
|**[[12.5 Integration Testing]]**|Route testing; database testing; test database; setup/teardown; fixtures. Integration tests.|
|**[[12.6 Mocking]]**|Jest mocks; mocking modules; database mocks; external services. Test doubles.|
|**[[12.7 Test Coverage]]**|Coverage reports; coverage thresholds; meaningful coverage; CI integration. Code coverage.|
|**[[12.8 Project: Tested API]]**|Complete test suite; unit tests; integration tests; coverage; CI. Testing project.|

### **[[13 Performance & Optimization]]**

Master Express performance optimization. Learn caching, compression, clustering, and monitoring. Performance skills are critical for handling production traffic.

|Topic|Focus & Purpose|
|---|---|
|**[[13.1 Response Compression]]**|compression middleware; gzip; deflate; configuration; when to compress. Response compression.|
|**[[13.2 Caching Strategies]]**|In-memory caching; Redis caching; HTTP caching; cache headers; invalidation. Cache optimization.|
|**[[13.3 Clustering]]**|Cluster module; worker processes; PM2; load distribution; scaling. Multi-core usage.|
|**[[13.4 Rate Limiting]]**|express-rate-limit; Redis-based limiting; API quotas; abuse prevention. Traffic control.|
|**[[13.5 Database Optimization]]**|Query optimization; indexing; connection pooling; N+1 problems. Database performance.|
|**[[13.6 Monitoring]]**|Morgan logging; request timing; APM tools; health checks; metrics. Observability.|
|**[[13.7 Project: Optimized API]]**|Performance optimization; caching; compression; monitoring; benchmarking. Performance project.|

### **[[14 Deployment & Production]]**

Master deploying Express applications to production. Learn hosting, Docker, CI/CD, and production configuration. Deployment knowledge is essential for shipping real-world applications.

|Topic|Focus & Purpose|
|---|---|
|**[[14.1 Production Preparation]]**|Environment variables; security; trust proxy; production dependencies. Production readiness.|
|**[[14.2 PM2]]**|PM2 setup; process management; clustering; logs; ecosystem file; monitoring. Process manager.|
|**[[14.3 Docker]]**|Dockerfile; multi-stage builds; docker-compose; container best practices. Containerization.|
|**[[14.4 Cloud Platforms]]**|Heroku; AWS (EC2, ECS, Lambda); DigitalOcean; Railway; Render. Cloud hosting.|
|**[[14.5 Nginx Reverse Proxy]]**|Nginx configuration; reverse proxy; SSL; load balancing; caching. Web server.|
|**[[14.6 CI/CD]]**|GitHub Actions; automated testing; deployment pipelines; rollback. Automation.|
|**[[14.7 Monitoring & Logging]]**|Winston; log management; error tracking; uptime monitoring; alerts. Production monitoring.|
|**[[14.8 Project: Production Deployment]]**|Complete deployment; Docker; CI/CD; Nginx; monitoring; SSL. Deployment project.|

### **[[15 Real-World Projects]]**

Master building production-grade Express applications. Build impressive portfolio pieces that demonstrate job-ready backend skills. Real projects are essential for landing Express/Node.js positions.

|Topic|Focus & Purpose|
|---|---|
|**[[15.1 REST API Backend]]**|Complete REST API; authentication; validation; documentation; testing. API project.|
|**[[15.2 E-Commerce API]]**|Products; cart; checkout; Stripe payments; orders; inventory. E-commerce backend.|
|**[[15.3 Social Media API]]**|Users; posts; comments; likes; follows; feed; notifications. Social platform.|
|**[[15.4 Real-Time Chat API]]**|Socket.io integration; messages; rooms; presence; history. Real-time features.|
|**[[15.5 Blog CMS API]]**|Posts; categories; comments; media; admin; publishing workflow. Content management.|
|**[[15.6 Authentication Service]]**|User management; OAuth; JWT; MFA; password reset; email verification. Auth service.|
|**[[15.7 Task Management API]]**|Projects; tasks; assignments; deadlines; notifications; collaboration. Project management.|
|**[[15.8 Production Backend]]**|Complete production API; all features; security; performance; documentation. Portfolio centerpiece.|
