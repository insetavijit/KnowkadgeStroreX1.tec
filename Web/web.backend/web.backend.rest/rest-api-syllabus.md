### **[[01 REST API Fundamentals]]**

Master REST API concepts as the foundation of modern web services. Learn why RESTful APIs power applications at Google, Amazon, Twitter, and virtually every tech company. Understand architectural constraints, HTTP methods, and resource design that form the backbone of web communication. API developers earn $90k-$150k annually with exceptional demand. Essential for backend development, full-stack roles, and system integration careers.

|Topic|Focus & Purpose|
|---|---|
|**[[1.1 REST Introduction]]**|What is REST; RESTful architecture; API concept; web services; client-server model; industry importance. Core concepts.|
|**[[1.2 REST Constraints]]**|Statelessness; client-server; cacheable; uniform interface; layered system; code on demand. Architectural principles.|
|**[[1.3 HTTP Protocol]]**|HTTP basics; request/response; headers; body; HTTP versions; HTTPS; connection lifecycle. Protocol foundation.|
|**[[1.4 HTTP Methods]]**|GET; POST; PUT; PATCH; DELETE; HEAD; OPTIONS; method semantics; idempotency; safety. Request methods.|
|**[[1.5 Status Codes]]**|2xx success; 3xx redirection; 4xx client errors; 5xx server errors; common codes; code selection. Response codes.|
|**[[1.6 REST vs Other Styles]]**|REST vs SOAP; vs GraphQL; vs gRPC; comparison; when to use REST. API paradigms.|
|**[[1.7 Project: API Design Document]]**|Designing first API; resources; endpoints; documentation sketch. Design project.|

### **[[02 Resource Design]]**

Master resource-oriented API design for intuitive APIs. Learn URI patterns, resource modeling, and naming conventions. Resource design is fundamental to creating clean, maintainable APIs.

|Topic|Focus & Purpose|
|---|---|
|**[[2.1 Resources & URIs]]**|Resource concept; nouns vs verbs; URI structure; path design; resource identification. Resource basics.|
|**[[2.2 Naming Conventions]]**|Plural nouns; lowercase; hyphens vs underscores; consistency; naming best practices. URI naming.|
|**[[2.3 Resource Hierarchies]]**|Nested resources; parent-child relationships; collection/item pattern; hierarchy depth. Resource relationships.|
|**[[2.4 Resource Relationships]]**|Related resources; linking; sub-resources vs separate endpoints; relationship modeling. Modeling relations.|
|**[[2.5 Singleton Resources]]**|Singleton pattern; current user; settings; single-instance resources. Special resources.|
|**[[2.6 Action Resources]]**|Non-CRUD operations; action endpoints; when to break REST conventions; pragmatic design. Actions.|
|**[[2.7 Query Parameters]]**|Filtering; searching; query vs path; parameter conventions; query design. Query patterns.|
|**[[2.8 Project: Resource Model]]**|Designing complete resource model; e-commerce API; relationships; URIs. Design project.|

### **[[03 Request Design]]**

Master API request design for client-friendly interfaces. Learn request body formats, headers, and input handling. Request design impacts API usability and consistency.

|Topic|Focus & Purpose|
|---|---|
|**[[3.1 Content Types]]**|Content-Type header; application/json; form data; multipart; content negotiation. Media types.|
|**[[3.2 Request Body]]**|JSON body; structure; nested objects; arrays; request format standards. Body format.|
|**[[3.3 Request Headers]]**|Standard headers; Accept; Authorization; custom headers; header conventions. Header usage.|
|**[[3.4 Query Parameters Design]]**|Filter parameters; sort; pagination params; search; parameter naming. Query design.|
|**[[3.5 Path Parameters]]**|Path variables; required parameters; parameter types; encoding. Path parameters.|
|**[[3.6 Request Validation]]**|Input validation; required fields; type validation; constraints; error responses. Validation.|
|**[[3.7 File Uploads]]**|Multipart requests; file handling; upload patterns; chunked uploads. File requests.|
|**[[3.8 Project: Request Specification]]**|Complete request specs; all inputs documented; validation rules. Request project.|

### **[[04 Response Design]]**

Master API response design for consistent, informative outputs. Learn response formats, envelope patterns, and error design. Response design ensures predictable API behavior.

|Topic|Focus & Purpose|
|---|---|
|**[[4.1 Response Structure]]**|JSON response format; data property; metadata; consistency; response conventions. Format standards.|
|**[[4.2 Envelope Pattern]]**|Response envelope; data wrapping; metadata; pagination info; success/error. Envelope design.|
|**[[4.3 Resource Representation]]**|Resource format; field naming; camelCase vs snake_case; date formats; conventions. Representation.|
|**[[4.4 Partial Responses]]**|Field selection; sparse fieldsets; include/exclude; query parameters. Partial data.|
|**[[4.5 HATEOAS]]**|Hypermedia; links; discoverability; self-describing APIs; HAL format. Hypermedia.|
|**[[4.6 Error Responses]]**|Error format; error codes; messages; details; validation errors; consistency. Error design.|
|**[[4.7 Response Headers]]**|Standard response headers; caching headers; custom headers; rate limit headers. Headers.|
|**[[4.8 Project: Response Specification]]**|Complete response specs; success/error formats; documentation. Response project.|

### **[[05 Pagination, Filtering & Sorting]]**

Master data retrieval patterns for large datasets. Learn pagination strategies, filtering, and sorting. These patterns are essential for production APIs with significant data.

|Topic|Focus & Purpose|
|---|---|
|**[[5.1 Pagination Basics]]**|Why pagination; page-based; offset-based; cursor-based; comparison. Pagination concepts.|
|**[[5.2 Offset Pagination]]**|Offset/limit; page/per_page; implementation; pros and cons; performance. Offset approach.|
|**[[5.3 Cursor Pagination]]**|Cursor-based; before/after; keyset pagination; performance benefits; implementation. Cursor approach.|
|**[[5.4 Pagination Response]]**|Pagination metadata; total count; links; next/prev; page info. Response format.|
|**[[5.5 Filtering]]**|Filter parameters; operators (eq, gt, lt); multiple filters; filter syntax. Filtering data.|
|**[[5.6 Searching]]**|Search parameter; full-text search; search fields; search vs filter. Search patterns.|
|**[[5.7 Sorting]]**|Sort parameter; ascending/descending; multiple fields; sort syntax. Ordering results.|
|**[[5.8 Project: Query System]]**|Implementing pagination; filtering; sorting; complete query system. Query project.|

### **[[06 Authentication & Authorization]]**

Master API security for protected resources. Learn authentication methods, authorization patterns, and security best practices. Security is critical for all production APIs.

|Topic|Focus & Purpose|
|---|---|
|**[[6.1 Auth Concepts]]**|Authentication vs authorization; identity verification; access control. Security basics.|
|**[[6.2 API Keys]]**|API key authentication; header vs query; key management; use cases. API key auth.|
|**[[6.3 Basic Authentication]]**|HTTP Basic Auth; base64 encoding; limitations; when to use. Basic auth.|
|**[[6.4 JWT Authentication]]**|JSON Web Tokens; Bearer token; token structure; stateless auth. JWT auth.|
|**[[6.5 OAuth 2.0]]**|OAuth flows; authorization code; client credentials; access tokens. OAuth.|
|**[[6.6 Authorization]]**|Role-based access; permissions; resource-level auth; scopes. Authorization.|
|**[[6.7 Security Headers]]**|CORS; security headers; HTTPS; security best practices. Security headers.|
|**[[6.8 Project: Secure API]]**|Implementing authentication; authorization; protected endpoints. Security project.|

### **[[07 Error Handling]]**

Master error handling for robust APIs. Learn error formats, HTTP codes, and error consistency. Good error handling improves API usability and debugging.

|Topic|Focus & Purpose|
|---|---|
|**[[7.1 Error Design Philosophy]]**|User-friendly errors; consistent format; actionable messages; debugging info. Error philosophy.|
|**[[7.2 HTTP Status Codes]]**|Correct status code usage; 4xx vs 5xx; common codes; code selection. Status codes.|
|**[[7.3 Error Response Format]]**|Error structure; code; message; details; type; format standards. Error format.|
|**[[7.4 Validation Errors]]**|Field validation errors; multiple errors; field-specific messages; array format. Validation format.|
|**[[7.5 Business Logic Errors]]**|Domain errors; error codes; categorization; custom error types. Business errors.|
|**[[7.6 Rate Limit Errors]]**|429 status; rate limit headers; retry-after; client guidance. Rate limiting.|
|**[[7.7 Error Localization]]**|Internationalized messages; error codes for i18n; language support. Localization.|
|**[[7.8 Project: Error System]]**|Complete error handling; consistent format; documentation. Error project.|

### **[[08 Versioning]]**

Master API versioning for long-term maintenance. Learn versioning strategies, deprecation, and backward compatibility. Versioning enables API evolution without breaking clients.

|Topic|Focus & Purpose|
|---|---|
|**[[8.1 Why Version]]**|Breaking changes; evolution; stability; versioning need; strategy importance. Versioning rationale.|
|**[[8.2 URL Versioning]]**|Path versioning (/v1/); major version in URL; pros and cons. URL approach.|
|**[[8.3 Header Versioning]]**|Custom header; Accept header; content negotiation; implementation. Header approach.|
|**[[8.4 Query Parameter]]**|Version in query string; flexibility; considerations. Query approach.|
|**[[8.5 Version Strategy Selection]]**|Comparing strategies; choosing approach; popular practices. Decision making.|
|**[[8.6 Deprecation]]**|Deprecation notices; sunset header; timeline; communication; graceful sunsetting. Deprecation.|
|**[[8.7 Backward Compatibility]]**|Non-breaking changes; additive changes; maintaining compatibility. Compatibility.|
|**[[8.8 Project: Versioned API]]**|Implementing versioning; migration path; documentation. Versioning project.|

### **[[09 Documentation]]**

Master API documentation for developer experience. Learn OpenAPI/Swagger, documentation tools, and best practices. Documentation is critical for API adoption and usability.

|Topic|Focus & Purpose|
|---|---|
|**[[9.1 Documentation Importance]]**|Developer experience; adoption; support reduction; self-service. Why document.|
|**[[9.2 OpenAPI Specification]]**|OpenAPI/Swagger; specification format; YAML/JSON; schema definition. OpenAPI.|
|**[[9.3 Documentation Tools]]**|Swagger UI; ReDoc; Stoplight; documentation generators. Doc tools.|
|**[[9.4 Endpoint Documentation]]**|Request/response; parameters; examples; descriptions; completeness. Endpoint docs.|
|**[[9.5 Code Examples]]**|Language examples; cURL; SDK snippets; copy-paste ready. Code samples.|
|**[[9.6 Authentication Documentation]]**|Auth instructions; obtaining tokens; header formats. Auth docs.|
|**[[9.7 Interactive Documentation]]**|Try-it-out; test consoles; sandbox environments; developer portal. Interactive docs.|
|**[[9.8 Project: Complete Documentation]]**|Full API documentation; OpenAPI; examples; portal. Documentation project.|

### **[[10 Rate Limiting & Throttling]]**

Master rate limiting for API protection and fair usage. Learn limiting strategies, response headers, and implementation. Rate limiting is essential for production API stability.

|Topic|Focus & Purpose|
|---|---|
|**[[10.1 Rate Limiting Concepts]]**|Why rate limit; abuse prevention; fair usage; throttling vs limiting. Basics.|
|**[[10.2 Rate Limit Strategies]]**|Fixed window; sliding window; token bucket; leaky bucket; algorithm selection. Algorithms.|
|**[[10.3 Rate Limit Headers]]**|X-RateLimit headers; remaining; limit; reset; client information. Response headers.|
|**[[10.4 Rate Limit Response]]**|429 status; retry-after; error message; client guidance. Error response.|
|**[[10.5 User-Based Limits]]**|Per-user limits; API key limits; tier-based limits; quotas. User limits.|
|**[[10.6 Endpoint-Based Limits]]**|Per-endpoint limits; resource-specific; dynamic limits. Endpoint limits.|
|**[[10.7 Implementation]]**|Redis; in-memory; distributed rate limiting; middleware. Implementation.|
|**[[10.8 Project: Rate Limiter]]**|Implementing rate limiting; headers; tiers; monitoring. Rate limit project.|

### **[[11 Caching]]**

Master API caching for performance optimization. Learn HTTP caching, cache headers, and caching strategies. Caching dramatically improves API performance and reduces load.

|Topic|Focus & Purpose|
|---|---|
|**[[11.1 Caching Basics]]**|Why cache; cache benefits; cache types; HTTP caching model. Caching concepts.|
|**[[11.2 Cache Headers]]**|Cache-Control; max-age; no-cache; no-store; private/public; headers. Cache control.|
|**[[11.3 ETags]]**|Entity tags; conditional requests; If-None-Match; 304 response; validation. ETags.|
|**[[11.4 Last-Modified]]**|Last-Modified header; If-Modified-Since; conditional GET; validation. Last-Modified.|
|**[[11.5 Cache Strategies]]**|Time-based; validation-based; cache invalidation; strategy selection. Strategies.|
|**[[11.6 CDN Caching]]**|CDN integration; edge caching; cache keys; purging. CDN.|
|**[[11.7 Server-Side Caching]]**|Response caching; Redis; in-memory; cache layers. Server caching.|
|**[[11.8 Project: Cached API]]**|Implementing caching; headers; CDN; performance testing. Caching project.|

### **[[12 Testing APIs]]**

Master API testing for reliable services. Learn testing strategies, tools, and test automation. Testing ensures API quality and prevents regressions.

|Topic|Focus & Purpose|
|---|---|
|**[[12.1 Testing Types]]**|Unit tests; integration tests; contract tests; E2E tests; test pyramid. Test types.|
|**[[12.2 Testing Tools]]**|Postman; Insomnia; cURL; HTTPie; test clients. Testing tools.|
|**[[12.3 Unit Testing]]**|Controller tests; service tests; mocking; isolation. Unit tests.|
|**[[12.4 Integration Testing]]**|Full endpoint tests; database tests; test database; fixtures. Integration tests.|
|**[[12.5 Contract Testing]]**|Consumer-driven contracts; Pact; API compatibility; schema validation. Contract tests.|
|**[[12.6 Load Testing]]**|Performance testing; k6; Artillery; load simulation; benchmarks. Load testing.|
|**[[12.7 Automated Testing]]**|CI/CD integration; test pipelines; automated runs; regression testing. Automation.|
|**[[12.8 Project: Test Suite]]**|Complete API test suite; all test types; CI integration. Testing project.|

### **[[13 API Design Patterns]]**

Master common API design patterns for complex scenarios. Learn patterns for batch operations, long-running tasks, and more. Patterns solve recurring design challenges.

|Topic|Focus & Purpose|
|---|---|
|**[[13.1 Batch Operations]]**|Bulk create/update/delete; batch endpoints; request format; response format. Batch patterns.|
|**[[13.2 Long-Running Operations]]**|Async operations; polling; webhooks; status endpoints; job patterns. Async patterns.|
|**[[13.3 Webhooks]]**|Webhook design; payload format; signatures; retry; delivery. Webhooks.|
|**[[13.4 Search API]]**|Search endpoint design; query syntax; facets; filters; results format. Search patterns.|
|**[[13.5 Soft Delete]]**|Soft delete pattern; archive; restore; trash; implementation. Deletion pattern.|
|**[[13.6 Expand/Include]]**|Related resource inclusion; expand parameter; reducing round trips. Expansion pattern.|
|**[[13.7 Idempotency]]**|Idempotency keys; safe retries; duplicate prevention; implementation. Idempotency.|
|**[[13.8 Project: Pattern Implementation]]**|Implementing patterns; batch; async; webhooks. Patterns project.|

### **[[14 Monitoring & Analytics]]**

Master API monitoring and analytics for production operations. Learn logging, metrics, and observability. Monitoring ensures API health and enables optimization.

|Topic|Focus & Purpose|
|---|---|
|**[[14.1 Logging]]**|Request logging; response logging; log format; log levels; structured logs. Logging.|
|**[[14.2 Metrics]]**|Request count; latency; error rate; custom metrics; metrics collection. Metrics.|
|**[[14.3 Monitoring Tools]]**|Prometheus; Grafana; DataDog; New Relic; monitoring stack. Tools.|
|**[[14.4 Alerting]]**|Alert rules; thresholds; on-call; incident response; alert fatigue. Alerting.|
|**[[14.5 API Analytics]]**|Usage analytics; popular endpoints; user behavior; business insights. Analytics.|
|**[[14.6 Health Checks]]**|Health endpoints; liveness; readiness; dependency checks. Health checks.|
|**[[14.7 Distributed Tracing]]**|Request tracing; correlation IDs; trace context; Jaeger/Zipkin. Tracing.|
|**[[14.8 Project: Observability]]**|Implementing monitoring; dashboards; alerts; tracing. Monitoring project.|

### **[[15 Real-World Projects]]**

Master building production REST APIs. Build impressive portfolio pieces that demonstrate API expertise. Real projects are essential for landing backend and API positions.

|Topic|Focus & Purpose|
|---|---|
|**[[15.1 E-Commerce API]]**|Products; cart; orders; payments; inventory; complete commerce API. E-commerce.|
|**[[15.2 Social Media API]]**|Users; posts; comments; likes; follows; feed; notifications. Social platform.|
|**[[15.3 Blog/CMS API]]**|Posts; categories; tags; media; comments; publishing. Content API.|
|**[[15.4 Task Management API]]**|Projects; tasks; assignments; deadlines; collaboration. Productivity API.|
|**[[15.5 Authentication Service]]**|User management; registration; login; tokens; password reset. Auth service.|
|**[[15.6 Payment API Integration]]**|Stripe/PayPal; webhooks; transactions; refunds; invoices. Payment integration.|
|**[[15.7 Real-Time API]]**|WebSockets; SSE; real-time updates; notifications. Real-time.|
|**[[15.8 Production API]]**|Complete production API; security; monitoring; documentation. Portfolio centerpiece.|
