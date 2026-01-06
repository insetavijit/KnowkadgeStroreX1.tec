### **[[01 Laravel Fundamentals & Setup]]**

Master Laravel as the most popular PHP framework for web application development. Learn why Laravel powers applications for companies like Disney, Twitch, The New York Times, and BBC. Understand the elegant syntax, powerful features, and developer experience that made Laravel the framework of choice for PHP developers. Laravel developers earn $75k-$120k annually with strong demand. Essential for PHP web development and full-stack careers.

|Topic|Focus & Purpose|
|---|---|
|**[[1.1 Laravel Introduction]]**|What is Laravel; PHP framework landscape; Laravel philosophy; ecosystem overview; market demand; job opportunities. Industry context.|
|**[[1.2 Environment Setup]]**|PHP 8.1+; Composer; Laravel installer; Herd/Valet/Homestead; VS Code extensions; XAMPP alternative. Professional setup.|
|**[[1.3 Project Structure]]**|Directory structure; app folder; routes; config; resources; storage; folder conventions. File organization.|
|**[[1.4 First Laravel App]]**|Creating project; artisan commands; development server; welcome page; basic routing. Getting started.|
|**[[1.5 Artisan CLI]]**|Artisan commands; make commands; tinker; custom commands; command options. CLI tooling.|
|**[[1.6 Configuration]]**|.env file; config files; environment detection; configuration caching; app settings. Configuration.|
|**[[1.7 Project: Hello Laravel]]**|Building first Laravel app; routes; views; styling; development workflow. First project.|

### **[[02 Routing]]**

Master Laravel routing for handling application URLs. Learn route parameters, named routes, and route groups. Routing is fundamental for all Laravel web and API development.

|Topic|Focus & Purpose|
|---|---|
|**[[2.1 Basic Routing]]**|Route methods; GET/POST/PUT/DELETE; closures; controller actions; route files. Route basics.|
|**[[2.2 Route Parameters]]**|Required parameters; optional parameters; regex constraints; parameter validation. Dynamic routes.|
|**[[2.3 Named Routes]]**|Route naming; URL generation; route() helper; redirects; named route benefits. Route naming.|
|**[[2.4 Route Groups]]**|Grouping; middleware; prefix; namespace; subdomain routing; group attributes. Route organization.|
|**[[2.5 Route Model Binding]]**|Implicit binding; explicit binding; custom keys; scoping; missing model handling. Model binding.|
|**[[2.6 Resource Routes]]**|Route::resource; CRUD routes; partial resources; nested resources; API resources. RESTful routes.|
|**[[2.7 API Routes]]**|api.php; stateless routes; API versioning; rate limiting; API prefix. API routing.|
|**[[2.8 Project: Blog Routes]]**|Building blog routing; resources; nested; named routes; organized structure. Routing project.|

### **[[03 Controllers]]**

Master Laravel controllers for organizing application logic. Learn controller types, dependency injection, and resource controllers. Controllers are the heart of Laravel application architecture.

|Topic|Focus & Purpose|
|---|---|
|**[[3.1 Controller Basics]]**|Creating controllers; single action; methods; returning responses; artisan make. Controller creation.|
|**[[3.2 Resource Controllers]]**|Resource controller methods; index/create/store/show/edit/update/destroy; conventions. RESTful controllers.|
|**[[3.3 Dependency Injection]]**|Constructor injection; method injection; service container; type-hinting. DI in controllers.|
|**[[3.4 Request Handling]]**|Request object; input retrieval; files; headers; request methods. Handling input.|
|**[[3.5 Response Types]]**|View responses; JSON; redirects; downloads; streaming; response macros. Response handling.|
|**[[3.6 Controller Middleware]]**|Applying middleware; constructor; only/except; middleware parameters. Controller middleware.|
|**[[3.7 Invokable Controllers]]**|Single action; __invoke; when to use; simplicity; route binding. Single action.|
|**[[3.8 Project: CRUD Controller]]**|Building complete controller; resource methods; validation; responses. Controller project.|

### **[[04 Blade Templating]]**

Master Blade as Laravel's powerful templating engine. Learn template inheritance, components, and directives. Blade skills are essential for building Laravel web applications.

|Topic|Focus & Purpose|
|---|---|
|**[[4.1 Blade Basics]]**|{{ }} syntax; escaping; comments; PHP in Blade; blade files. Template basics.|
|**[[4.2 Control Structures]]**|@if/@else; @foreach; @for; @while; @switch; loop variable. Blade directives.|
|**[[4.3 Template Inheritance]]**|@extends; @section; @yield; @parent; master layouts; content sections. Layout system.|
|**[[4.4 Components]]**|Blade components; x-component; props; slots; anonymous components; class components. Component system.|
|**[[4.5 Including Views]]**|@include; @includeIf; @includeWhen; @each; view partials. View composition.|
|**[[4.6 Forms & CSRF]]**|@csrf; @method; form handling; old input; error display. Form helpers.|
|**[[4.7 Custom Directives]]**|Blade::directive; custom directives; directive registration; reusable logic. Extending Blade.|
|**[[4.8 Project: Blog Frontend]]**|Building blog UI; layouts; components; forms; styling. Blade project.|

### **[[05 Database & Eloquent]]**

Master Laravel's Eloquent ORM for database operations. Learn models, relationships, and query building. Eloquent is the core of Laravel data handling and tested in every interview.

|Topic|Focus & Purpose|
|---|---|
|**[[5.1 Database Configuration]]**|Database connections; .env settings; multiple databases; connection switching. Database setup.|
|**[[5.2 Migrations]]**|Creating migrations; schema building; columns; indexes; foreign keys; rollback. Schema management.|
|**[[5.3 Eloquent Models]]**|Model creation; conventions; table naming; primary keys; timestamps; mass assignment. Model basics.|
|**[[5.4 CRUD Operations]]**|Creating; reading; updating; deleting; firstOrCreate; updateOrCreate; upsert. Data operations.|
|**[[5.5 Query Builder]]**|Eloquent queries; where clauses; ordering; grouping; aggregates; raw queries. Query building.|
|**[[5.6 Relationships]]**|hasOne; hasMany; belongsTo; belongsToMany; morphMany; polymorphic. Model relationships.|
|**[[5.7 Eager Loading]]**|N+1 problem; with(); load(); eager loading constraints; lazy loading. Performance.|
|**[[5.8 Project: Blog Database]]**|Building database; posts; categories; comments; users; relationships. Database project.|

### **[[06 Eloquent Advanced]]**

Master advanced Eloquent features for complex applications. Learn scopes, accessors, mutators, and advanced queries. Advanced Eloquent skills separate junior from senior Laravel developers.

|Topic|Focus & Purpose|
|---|---|
|**[[6.1 Scopes]]**|Local scopes; global scopes; dynamic scopes; scope parameters; reusable queries. Query scopes.|
|**[[6.2 Accessors & Mutators]]**|Attribute casting; get/set accessors; appending attributes; virtual attributes. Data transformation.|
|**[[6.3 Collections]]**|Eloquent collections; collection methods; mapping; filtering; custom collections. Data manipulation.|
|**[[6.4 Soft Deletes]]**|SoftDeletes trait; deleted_at; withTrashed; restore; forceDelete. Soft deletion.|
|**[[6.5 Events & Observers]]**|Model events; creating/updating hooks; observers; event subscribers. Model lifecycle.|
|**[[6.6 Factories & Seeders]]**|Model factories; database seeding; fake data; testing data. Test data.|
|**[[6.7 API Resources]]**|JsonResource; ResourceCollection; transforming data; nested resources. API transformation.|
|**[[6.8 Project: Advanced Models]]**|Building complex models; scopes; events; resources; optimization. Advanced project.|

### **[[07 Authentication & Authorization]]**

Master Laravel authentication and authorization. Learn Breeze, Sanctum, policies, and gates. Auth skills are essential for building secure Laravel applications.

|Topic|Focus & Purpose|
|---|---|
|**[[7.1 Auth Overview]]**|Laravel auth options; Breeze; Jetstream; Fortify; UI packages. Auth packages.|
|**[[7.2 Laravel Breeze]]**|Installing Breeze; Blade/React/Vue; login; register; password reset. Quick auth setup.|
|**[[7.3 Sanctum]]**|API tokens; SPA authentication; token abilities; mobile auth. API authentication.|
|**[[7.4 Guards & Providers]]**|Auth guards; user providers; custom guards; multiple auth. Auth architecture.|
|**[[7.5 Authorization Gates]]**|Gate::define; Gate::allows; Gate::denies; inline authorization. Gate-based auth.|
|**[[7.6 Policies]]**|Policy classes; policy methods; policy registration; resource authorization. Policy-based auth.|
|**[[7.7 Middleware]]**|Auth middleware; guest middleware; verified middleware; custom auth middleware. Route protection.|
|**[[7.8 Project: Auth System]]**|Building complete auth; login; register; roles; permissions; protected routes. Auth project.|

### **[[08 Validation]]**

Master Laravel validation for data integrity. Learn validation rules, form requests, and custom validators. Validation is critical for secure and reliable applications.

|Topic|Focus & Purpose|
|---|---|
|**[[8.1 Validation Basics]]**|validate() method; validation rules; error messages; validation response. Basic validation.|
|**[[8.2 Form Requests]]**|Creating form requests; rules method; authorize; custom messages. Request validation.|
|**[[8.3 Validation Rules]]**|Built-in rules; required; email; unique; exists; regex; conditionals. Rule reference.|
|**[[8.4 Custom Rules]]**|Rule objects; custom validation; closure rules; implicit rules. Custom validation.|
|**[[8.5 Error Display]]**|@error directive; $errors bag; named error bags; error formatting. Error presentation.|
|**[[8.6 Array Validation]]**|Array rules; nested validation; wildcard; array indexes. Complex validation.|
|**[[8.7 File Validation]]**|File rules; mimes; size; dimensions; image validation. Upload validation.|
|**[[8.8 Project: Validated Forms]]**|Building forms; form requests; custom rules; comprehensive validation. Validation project.|

### **[[09 API Development]]**

Master building APIs with Laravel. Learn API resources, versioning, authentication, and best practices. API development is a primary use case for Laravel in modern applications.

|Topic|Focus & Purpose|
|---|---|
|**[[9.1 API Basics]]**|API routes; JSON responses; status codes; headers; API conventions. API fundamentals.|
|**[[9.2 API Resources]]**|Resource classes; collections; conditional attributes; nested resources; pagination. Response formatting.|
|**[[9.3 API Authentication]]**|Sanctum tokens; passport; API guards; token management; abilities. API auth.|
|**[[9.4 Rate Limiting]]**|RateLimiter; throttle middleware; rate limit responses; custom limiters. Traffic control.|
|**[[9.5 API Versioning]]**|URL versioning; route groups; version management; deprecation. API evolution.|
|**[[9.6 API Documentation]]**|Scribe; L5-Swagger; OpenAPI; automated documentation. API docs.|
|**[[9.7 Error Handling]]**|API exceptions; JSON errors; error format; debugging. API errors.|
|**[[9.8 Project: REST API]]**|Building complete API; CRUD; authentication; documentation. API project.|

### **[[10 File Storage]]**

Master file handling in Laravel. Learn storage system, uploads, cloud storage, and file management. File handling is common in production applications.

|Topic|Focus & Purpose|
|---|---|
|**[[10.1 Storage Basics]]**|Storage facade; local disk; configuration; file operations. Storage fundamentals.|
|**[[10.2 File Uploads]]**|Upload handling; store(); storeAs(); validation; security. Upload processing.|
|**[[10.3 Storage Disks]]**|Disk configuration; local; public; s3; custom disks. Storage configuration.|
|**[[10.4 Cloud Storage]]**|AWS S3; DigitalOcean Spaces; configuration; cloud operations. Cloud storage.|
|**[[10.5 File Downloads]]**|download(); streaming; temporary URLs; signed URLs. File serving.|
|**[[10.6 Image Processing]]**|Intervention Image; resizing; manipulation; thumbnails. Image handling.|
|**[[10.7 Project: Media Library]]**|Building file system; uploads; cloud storage; thumbnails; management. Storage project.|

### **[[11 Queues & Jobs]]**

Master Laravel queues for background processing. Learn job creation, queue drivers, and job handling. Queue skills are essential for scalable Laravel applications.

|Topic|Focus & Purpose|
|---|---|
|**[[11.1 Queue Basics]]**|Queue concept; queue drivers; configuration; when to use queues. Queue fundamentals.|
|**[[11.2 Creating Jobs]]**|Job classes; handle method; constructor; dispatch; job data. Job creation.|
|**[[11.3 Dispatching Jobs]]**|dispatch(); dispatchSync(); delay; chain; batch. Job dispatch.|
|**[[11.4 Queue Workers]]**|queue:work; supervisor; process management; worker options. Running workers.|
|**[[11.5 Job Middleware]]**|Rate limiting; unique jobs; throttling; job middleware. Job control.|
|**[[11.6 Failed Jobs]]**|Failed job handling; retry; failed_jobs table; monitoring. Error handling.|
|**[[11.7 Queue Events]]**|Job events; before/after hooks; job listeners; monitoring. Job lifecycle.|
|**[[11.8 Project: Background Processing]]**|Building job system; email sending; image processing; reporting. Queue project.|

### **[[12 Events & Notifications]]**

Master Laravel events and notifications. Learn event-driven architecture, listeners, and multi-channel notifications. Event skills enable decoupled, scalable applications.

|Topic|Focus & Purpose|
|---|---|
|**[[12.1 Events Basics]]**|Event classes; event dispatching; event data; when to use events. Event fundamentals.|
|**[[12.2 Listeners]]**|Listener classes; handle method; queued listeners; listener registration. Event handling.|
|**[[12.3 Event Discovery]]**|Auto-discovery; EventServiceProvider; event-listener mapping. Registration.|
|**[[12.4 Notifications]]**|Notification classes; via(); toMail(); toDatabase(); toArray(). Notification system.|
|**[[12.5 Mail Notifications]]**|Mail channel; MailMessage; customization; markdown mail. Email notifications.|
|**[[12.6 Database Notifications]]**|Database channel; notification table; reading notifications; marking read. Stored notifications.|
|**[[12.7 Broadcasting]]**|WebSocket events; Pusher; Laravel Echo; private channels; presence. Real-time events.|
|**[[12.8 Project: Notification System]]**|Building notifications; multi-channel; real-time; user preferences. Notification project.|

### **[[13 Testing]]**

Master Laravel testing for reliable applications. Learn PHPUnit, feature tests, and database testing. Testing skills are essential for professional Laravel development.

|Topic|Focus & Purpose|
|---|---|
|**[[13.1 Testing Basics]]**|PHPUnit; test setup; running tests; test organization; artisan test. Testing fundamentals.|
|**[[13.2 Feature Tests]]**|HTTP tests; get/post/put; response assertions; authentication. HTTP testing.|
|**[[13.3 Unit Tests]]**|Unit testing; mocking; isolation; testing services. Unit tests.|
|**[[13.4 Database Testing]]**|RefreshDatabase; DatabaseTransactions; factories; seeders; assertions. Database tests.|
|**[[13.5 Mocking]]**|Facades; Mockery; faking services; Mail::fake(); Queue::fake(). Test doubles.|
|**[[13.6 Browser Testing]]**|Laravel Dusk; browser automation; screenshots; authentication. E2E testing.|
|**[[13.7 Test Coverage]]**|Code coverage; coverage reports; CI integration; thresholds. Coverage.|
|**[[13.8 Project: Tested Application]]**|Complete test suite; feature tests; unit tests; coverage. Testing project.|

### **[[14 Security & Performance]]**

Master Laravel security and performance optimization. Learn security best practices, caching, and optimization. Security and performance are critical for production applications.

|Topic|Focus & Purpose|
|---|---|
|**[[14.1 Security Fundamentals]]**|CSRF; XSS prevention; SQL injection; mass assignment; security headers. Security basics.|
|**[[14.2 Encryption]]**|Encryption; Crypt facade; hashing; password hashing; encrypted data. Data encryption.|
|**[[14.3 Caching]]**|Cache drivers; Cache facade; cache tags; query caching; view caching. Cache system.|
|**[[14.4 Performance]]**|Route caching; config caching; view caching; OPcache; optimization. Performance tuning.|
|**[[14.5 Database Optimization]]**|Query optimization; indexing; eager loading; profiling; slow queries. Database performance.|
|**[[14.6 Logging]]**|Log channels; Monolog; log levels; custom channels; log rotation. Application logging.|
|**[[14.7 Project: Optimized App]]**|Performance audit; caching implementation; security hardening. Optimization project.|

### **[[15 Deployment & Production]]**

Master deploying Laravel applications to production. Learn hosting, CI/CD, and production configuration. Deployment skills are essential for shipping applications.

|Topic|Focus & Purpose|
|---|---|
|**[[15.1 Production Preparation]]**|Environment config; optimization commands; security checklist. Production readiness.|
|**[[15.2 Deployment Options]]**|Forge; Vapor; Ploi; traditional hosting; VPS; shared hosting. Hosting options.|
|**[[15.3 Laravel Forge]]**|Forge setup; server provisioning; deployments; SSL; monitoring. Managed deployment.|
|**[[15.4 Laravel Vapor]]**|Serverless deployment; AWS Lambda; Vapor configuration; scaling. Serverless.|
|**[[15.5 Docker]]**|Laravel Sail; Dockerfile; docker-compose; containerized deployment. Containerization.|
|**[[15.6 CI/CD]]**|GitHub Actions; automated testing; deployment pipelines; Envoyer. Automation.|
|**[[15.7 Server Management]]**|Nginx; supervisor; queue workers; cron; SSL certificates. Server config.|
|**[[15.8 Project: Production Deployment]]**|Complete deployment; CI/CD; monitoring; scaling. Deployment project.|

### **[[16 Real-World Projects]]**

Master building production-grade Laravel applications. Build impressive portfolio pieces that demonstrate job-ready PHP skills. Real projects are essential for landing Laravel positions.

|Topic|Focus & Purpose|
|---|---|
|**[[16.1 Blog Platform]]**|Full blog; posts; categories; comments; authentication; admin panel. Content platform.|
|**[[16.2 E-Commerce Store]]**|Products; cart; checkout; Stripe payments; orders; inventory. E-commerce.|
|**[[16.3 SaaS Application]]**|Multi-tenancy; subscriptions; Cashier; billing; team management. SaaS platform.|
|**[[16.4 REST API Backend]]**|Complete API; Sanctum; resources; documentation; testing. API backend.|
|**[[16.5 CRM System]]**|Contacts; companies; deals; tasks; pipeline; reporting. Business app.|
|**[[16.6 Admin Dashboard]]**|Filament/Nova; data management; charts; user management. Admin interface.|
|**[[16.7 Real-Time Chat]]**|Broadcasting; WebSockets; Pusher; presence; message history. Real-time app.|
|**[[16.8 Production Application]]**|Complete production app; all features; security; performance. Portfolio centerpiece.|
