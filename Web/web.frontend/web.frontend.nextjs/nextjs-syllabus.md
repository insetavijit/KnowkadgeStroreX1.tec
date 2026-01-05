### **[[01 Next.js Fundamentals & Setup]]**

Master Next.js 15 as the leading React framework for production. Learn why Next.js is used by companies like Netflix, Uber, Twitch, and TikTok. Understand that Next.js powers modern web applications with server-side rendering, static generation, and edge computing. Next.js developers earn $121k-$145k annually with growing demand. Essential for modern full-stack development and React mastery. This module builds the foundation for job-ready Next.js skills.

|Topic|Focus & Purpose|
|---|---|
|**[[1.1 Next.js Introduction]]**|What is Next.js; React vs Next.js; SSR vs CSR; why Next.js; market demand; job landscape; ecosystem overview. Industry context.|
|**[[1.2 Environment Setup]]**|Node.js 20.9+; create-next-app; VS Code setup; TypeScript configuration; ESLint; Prettier; Git; project structure. Professional setup.|
|**[[1.3 Project Structure]]**|App Router vs Pages Router; app directory; folder conventions; routing basics; layout structure; page hierarchy. File organization.|
|**[[1.4 First Next.js App]]**|Creating pages; React Server Components; client components; basic routing; layouts; navigation basics. Building foundation.|
|**[[1.5 TypeScript Integration]]**|TypeScript setup; type safety; interfaces; component types; props typing; TypeScript best practices. Type-safe development.|
|**[[1.6 Development Workflow]]**|Dev server; fast refresh; hot reload; error handling; debugging in Next.js; DevTools usage. Development experience.|
|**[[1.7 Next.js vs Other Frameworks]]**|Next.js vs Create React App; vs Gatsby; vs Remix; when to use Next.js; framework comparison. Informed decisions.|
|**[[1.8 Project: Portfolio Landing]]**|Building first Next.js site; multiple pages; navigation; layouts; TypeScript; responsive design. First complete project.|

### **[[02 App Router & Routing]]**

Master the modern App Router (Next.js 13+) for file-system based routing. Learn nested routes, dynamic segments, route groups, and parallel routes. Build sophisticated navigation systems. App Router knowledge is essential for all modern Next.js jobs and replaces the legacy Pages Router.

|Topic|Focus & Purpose|
|---|---|
|**[[2.1 App Router Fundamentals]]**|App directory structure; file conventions; page.tsx; layout.tsx; route segments; nested routing. Modern routing.|
|**[[2.2 Dynamic Routes]]**|[slug] syntax; dynamic segments; generateStaticParams; catch-all routes; optional catch-all; params prop. Dynamic pages.|
|**[[2.3 Route Groups]]**|(folder) syntax; grouping routes; multiple layouts; organizing routes; URL structure control. Route organization.|
|**[[2.4 Parallel Routes]]**|@folder syntax; simultaneous rendering; modal patterns; independent loading states; slots. Advanced routing.|
|**[[2.5 Intercepting Routes]]**|(..) syntax; soft navigation; modal routes; preserving context; route interception patterns. Complex navigation.|
|**[[2.6 Loading & Error States]]**|loading.tsx; error.tsx; not-found.tsx; streaming; suspense; error boundaries. User experience.|
|**[[2.7 Navigation & Links]]**|Link component; useRouter; usePathname; useSearchParams; programmatic navigation; prefetching. Client navigation.|
|**[[2.8 Project: Blog Platform Routing]]**|Building blog with dynamic routes; categories; tags; nested layouts; loading states; error handling. Production routing.|

### **[[03 Server Components & Client Components]]**

Master React Server Components (RSC) and the fundamental shift in Next.js architecture. Learn when to use server vs client components, data fetching patterns, and component composition. This is the most important concept in modern Next.js and critical for all job interviews.

|Topic|Focus & Purpose|
|---|---|
|**[[3.1 Server Components Fundamentals]]**|What are Server Components; default behavior; advantages; async components; server-side data fetching. Core concept.|
|**[[3.2 Client Components]]**|'use client' directive; interactivity; hooks; event handlers; state management; when to use client. Interactive features.|
|**[[3.3 Component Composition]]**|Server + Client composition; passing Server Components as children; composition patterns; component boundaries. Architecture.|
|**[[3.4 Data Fetching in Server Components]]**|Async fetch; server-only functions; database queries; API calls; data fetching patterns. Server-side data.|
|**[[3.5 Client Component Boundaries]]**|'use client' boundaries; prop drilling; context providers; minimizing client JavaScript. Optimization.|
|**[[3.6 Streaming & Suspense]]**|React Suspense; streaming server rendering; loading UI; progressive rendering; skeleton screens. Performance.|
|**[[3.7 Server vs Client Decision Tree]]**|When to use each; decision flowchart; performance implications; SEO considerations; best practices. Making choices.|
|**[[3.8 Project: E-commerce Product Page]]**|Building product page; server data fetching; client interactivity; cart system; composition patterns. Real-world example.|

### **[[04 Data Fetching & Caching]]**

Master Next.js data fetching with the new fetch API, caching strategies, and revalidation. Learn incremental static regeneration (ISR), on-demand revalidation, and data mutation patterns. Proper data fetching is crucial for performance and user experience in production apps.

|Topic|Focus & Purpose|
|---|---|
|**[[4.1 Fetch API & Caching]]**|Extended fetch API; cache options (force-cache, no-store); request deduplication; caching strategies. Data fetching.|
|**[[4.2 Revalidation Strategies]]**|Time-based revalidation; on-demand revalidation; revalidatePath; revalidateTag; cache invalidation. Cache management.|
|**[[4.3 Incremental Static Regeneration]]**|ISR fundamentals; revalidate option; stale-while-revalidate; background regeneration; use cases. Dynamic static content.|
|**[[4.4 Server Actions]]**|Server Actions basics; 'use server' directive; form actions; data mutations; progressive enhancement. Modern forms.|
|**[[4.5 Data Mutation Patterns]]**|POST requests; Server Actions; optimistic updates; error handling; form validation. Writing data.|
|**[[4.6 Parallel Data Fetching]]**|Multiple fetch requests; Promise.all; parallel loading; waterfall prevention; performance optimization. Efficient loading.|
|**[[4.7 Request Memoization]]**|React cache(); automatic deduplication; request memoization patterns; performance benefits. Request optimization.|
|**[[4.8 Project: News Aggregator]]**|Building news site; ISR; multiple data sources; caching strategies; revalidation; real-time updates. Data-intensive app.|

### **[[05 Database Integration & ORMs]]**

Master database integration with Prisma, Drizzle, or PostgreSQL. Learn schema design, migrations, queries, and database best practices. Build production-ready apps with persistent data. Database skills are essential for full-stack Next.js positions.

|Topic|Focus & Purpose|
|---|---|
|**[[5.1 Database Options]]**|PostgreSQL; MySQL; MongoDB; Supabase; PlanetScale; database selection; hosted solutions. Choosing databases.|
|**[[5.2 Prisma ORM]]**|Prisma setup; schema definition; migrations; Prisma Client; type safety; database queries. Modern ORM.|
|**[[5.3 Drizzle ORM]]**|Drizzle setup; schema; queries; migrations; TypeScript-first ORM; performance benefits. Alternative ORM.|
|**[[5.4 Database Schema Design]]**|Schema modeling; relationships; indexes; constraints; normalization; best practices. Data modeling.|
|**[[5.5 CRUD Operations]]**|Create operations; Read queries; Update statements; Delete operations; transaction handling. Database operations.|
|**[[5.6 Database Migrations]]**|Migration strategies; version control; schema changes; production migrations; rollback procedures. Schema management.|
|**[[5.7 Connection Pooling]]**|Connection management; pooling strategies; Prisma connection pooling; edge databases; optimization. Performance.|
|**[[5.8 Project: Task Management System]]**|Building full CRUD app; database schema; Prisma integration; Server Actions; data validation. Database-driven app.|

### **[[06 Authentication & Authorization]]**

Master authentication with NextAuth.js (Auth.js), Clerk, or custom solutions. Learn OAuth, JWT, session management, and protected routes. Build secure applications with user management. Authentication is required for almost all production Next.js applications.

|Topic|Focus & Purpose|
|---|---|
|**[[6.1 Authentication Basics]]**|Authentication vs authorization; session vs token; OAuth 2.0; JWT; security fundamentals; best practices. Auth concepts.|
|**[[6.2 NextAuth.js (Auth.js)]]**|NextAuth.js v5 setup; providers (Google, GitHub, Credentials); callbacks; sessions; JWT strategy. Popular auth solution.|
|**[[6.3 Clerk Authentication]]**|Clerk setup; user management; social logins; middleware; webhook handling; embeddable UI. Modern auth platform.|
|**[[6.4 Protected Routes]]**|Route protection; middleware; authentication guards; redirect logic; unauthorized handling. Secure routes.|
|**[[6.5 Role-Based Access Control]]**|RBAC implementation; permissions; roles; authorization middleware; protecting resources. Authorization.|
|**[[6.6 Session Management]]**|Session storage; session cookies; refresh tokens; session expiration; security best practices. Managing sessions.|
|**[[6.7 Custom Authentication]]**|Building custom auth; password hashing (bcrypt); JWT implementation; secure cookies; token management. Custom solution.|
|**[[6.8 Project: SaaS Authentication]]**|Complete auth system; social logins; email/password; protected dashboard; role management. Production auth.|

### **[[07 Styling & UI Development]]**

Master modern styling approaches for Next.js. Learn Tailwind CSS, CSS Modules, CSS-in-JS, and component libraries. Build beautiful, responsive UIs efficiently. Styling skills are essential for front-end focused Next.js positions.

|Topic|Focus & Purpose|
|---|---|
|**[[7.1 Tailwind CSS Integration]]**|Tailwind setup; utility classes; responsive design; dark mode; customization; best practices. Most popular approach.|
|**[[7.2 CSS Modules]]**|CSS Modules basics; scoped styles; composition; naming conventions; when to use CSS Modules. Traditional approach.|
|**[[7.3 Component Libraries]]**|shadcn/ui; Material-UI; Chakra UI; Radix UI; component integration; customization. Pre-built components.|
|**[[7.4 Responsive Design]]**|Mobile-first design; breakpoints; responsive utilities; container queries; modern responsive patterns. Cross-device support.|
|**[[7.5 Dark Mode]]**|Dark mode implementation; next-themes; system preference; toggle UI; persistence; color schemes. Theme switching.|
|**[[7.6 Animation Libraries]]**|Framer Motion; animation patterns; page transitions; scroll animations; interactive elements. Motion design.|
|**[[7.7 Icon Libraries]]**|Lucide React; Heroicons; React Icons; icon usage; optimization; best practices. Icon integration.|
|**[[7.8 Project: Modern Dashboard UI]]**|Building dashboard; Tailwind; shadcn/ui; dark mode; responsive design; animations; charts. Complete UI project.|

### **[[08 API Routes & Backend]]**

Master building APIs with Next.js Route Handlers. Learn RESTful API design, middleware, error handling, and API security. Build full-stack applications with Next.js backend. API development skills are crucial for full-stack Next.js positions.

|Topic|Focus & Purpose|
|---|---|
|**[[8.1 Route Handlers Basics]]**|app/api folder; route.ts files; HTTP methods (GET, POST, PUT, DELETE); Request/Response; route handlers. Backend fundamentals.|
|**[[8.2 RESTful API Design]]**|REST principles; resource design; URL structure; HTTP methods; status codes; API conventions. API architecture.|
|**[[8.3 Request & Response Handling]]**|NextRequest; NextResponse; headers; cookies; searching params; JSON responses; error responses. HTTP handling.|
|**[[8.4 API Middleware]]**|Middleware concept; authentication middleware; rate limiting; CORS; request validation; error handling. API protection.|
|**[[8.5 Error Handling]]**|Error types; try-catch; error responses; status codes; validation errors; custom error classes. Robust APIs.|
|**[[8.6 API Validation]]**|Input validation; Zod; schema validation; sanitization; error messages; request validation. Data validation.|
|**[[8.7 External API Integration]]**|Fetching external APIs; API keys; rate limiting; error handling; caching; proxy patterns. Third-party integration.|
|**[[8.8 Project: REST API Backend]]**|Building complete API; CRUD endpoints; authentication; validation; error handling; documentation. Full API project.|

### **[[09 Forms & Data Validation]]**

Master form handling with Server Actions, React Hook Form, and validation libraries. Learn progressive enhancement, optimistic updates, and error handling. Build production-grade forms with excellent UX. Form mastery is critical for interactive applications.

|Topic|Focus & Purpose|
|---|---|
|**[[9.1 Server Actions for Forms]]**|Server Actions basics; form actions; FormData; progressive enhancement; no-JS forms; revalidation. Modern form handling.|
|**[[9.2 React Hook Form]]**|React Hook Form setup; useForm hook; controlled inputs; field validation; form submission; performance. Client-side forms.|
|**[[9.3 Zod Validation]]**|Zod schema; type inference; validation rules; error messages; server-side validation; client-side validation. Type-safe validation.|
|**[[9.4 Form UI Components]]**|Form inputs; select dropdowns; checkboxes; radio buttons; file uploads; accessible forms. Form elements.|
|**[[9.5 Optimistic Updates]]**|useOptimistic hook; optimistic UI; rollback handling; pending states; user experience. Instant feedback.|
|**[[9.6 File Uploads]]**|File upload handling; image uploads; cloud storage (S3, Cloudinary); validation; progress indicators. Handling files.|
|**[[9.7 Multi-Step Forms]]**|Wizard forms; step management; data persistence; progress indicators; validation per step. Complex forms.|
|**[[9.8 Project: Contact & Onboarding]]**|Building contact form; multi-step onboarding; validation; Server Actions; file uploads; email integration. Production forms.|

### **[[10 Image & Media Optimization]]**

Master Next.js Image component and media optimization. Learn responsive images, lazy loading, image formats, and CDN integration. Build fast-loading, optimized applications. Image optimization is crucial for performance and SEO.

|Topic|Focus & Purpose|
|---|---|
|**[[10.1 Next.js Image Component]]**|Image component basics; src attribute; width/height; priority; loading; responsive images. Optimized images.|
|**[[10.2 Image Optimization]]**|Automatic optimization; WebP/AVIF formats; resizing; quality settings; caching; optimization strategies. Performance.|
|**[[10.3 Responsive Images]]**|Responsive sizes; fill property; object-fit; art direction; mobile optimization. Cross-device images.|
|**[[10.4 Image Loaders]]**|Custom loaders; Cloudinary; Imgix; S3; CDN integration; remote patterns. External images.|
|**[[10.5 Lazy Loading]]**|Lazy loading images; intersection observer; loading priority; above-the-fold; performance impact. Loading strategy.|
|**[[10.6 Video Optimization]]**|Video element; streaming; formats; compression; lazy loading video; video hosting. Video content.|
|**[[10.7 Font Optimization]]**|next/font; Google Fonts; custom fonts; font display; loading strategies; performance. Typography optimization.|
|**[[10.8 Project: Media Gallery]]**|Building image gallery; Image component; lazy loading; lightbox; responsive images; optimization. Media showcase.|

### **[[11 SEO & Metadata]]**

Master SEO optimization in Next.js. Learn metadata API, dynamic SEO, Open Graph, structured data, and sitemap generation. Build SEO-friendly applications that rank well. SEO skills are essential for content-focused and marketing applications.

|Topic|Focus & Purpose|
|---|---|
|**[[11.1 Metadata API]]**|generateMetadata function; static metadata; dynamic metadata; metadata object; title templates. Modern SEO.|
|**[[11.2 Dynamic SEO]]**|Dynamic titles; descriptions; keywords; per-page metadata; blog post SEO; product SEO. Page-specific SEO.|
|**[[11.3 Open Graph & Twitter Cards]]**|OG tags; Twitter Card tags; social sharing; preview images; metadata for social. Social media SEO.|
|**[[11.4 Structured Data (JSON-LD)]]**|Schema.org; JSON-LD; rich snippets; structured data types; Google rich results. Search enhancements.|
|**[[11.5 Sitemap Generation]]**|sitemap.xml; dynamic sitemaps; sitemap generation; multiple sitemaps; XML sitemap. Search engine discovery.|
|**[[11.6 Robots.txt]]**|robots.txt file; crawling rules; disallow patterns; sitemap reference; robot directives. Crawler control.|
|**[[11.7 Canonical URLs]]**|Canonical tags; duplicate content; URL canonicalization; SEO best practices; implementation. URL management.|
|**[[11.8 Project: SEO-Optimized Blog]]**|Building blog with full SEO; metadata; Open Graph; structured data; sitemaps; performance. SEO showcase.|

### **[[12 Performance Optimization]]**

Master Next.js performance optimization techniques. Learn code splitting, lazy loading, caching strategies, and Core Web Vitals. Build blazing-fast applications. Performance optimization is critical for user experience and increasingly important for job interviews.

|Topic|Focus & Purpose|
|---|---|
|**[[12.1 Core Web Vitals]]**|LCP; FID; CLS; performance metrics; measurement; optimization strategies; real-world performance. User experience metrics.|
|**[[12.2 Code Splitting]]**|Automatic code splitting; dynamic imports; lazy loading components; bundle optimization; route-based splitting. Bundle management.|
|**[[12.3 Bundle Analysis]]**|@next/bundle-analyzer; bundle size analysis; optimization opportunities; tree shaking; dead code elimination. Analyzing bundles.|
|**[[12.4 Caching Strategies]]**|Cache-Control headers; CDN caching; browser caching; service workers; caching best practices. Cache optimization.|
|**[[12.5 Edge Functions]]**|Middleware at edge; geo-location; A/B testing; personalization; edge computing benefits. Edge optimization.|
|**[[12.6 Static Generation]]**|generateStaticParams; static export; static optimization; when to use static; build-time generation. Maximum performance.|
|**[[12.7 Streaming & Suspense]]**|Streaming SSR; React Suspense; progressive rendering; loading states; improving TTFB. Rendering optimization.|
|**[[12.8 Project: Performance Audit]]**|Performance optimization project; Lighthouse; analyzing metrics; implementing fixes; measuring improvements. Performance showcase.|

### **[[13 Testing Next.js Applications]]**

Master testing strategies for Next.js apps. Learn Jest, React Testing Library, Playwright, and Cypress. Build reliable, maintainable applications with comprehensive test coverage. Testing skills are increasingly required for senior Next.js positions.

|Topic|Focus & Purpose|
|---|---|
|**[[13.1 Testing Fundamentals]]**|Testing pyramid; unit tests; integration tests; E2E tests; testing philosophy; when to test. Testing strategy.|
|**[[13.2 Jest & React Testing Library]]**|Jest setup; React Testing Library; component testing; snapshot testing; mocking; assertions. Unit testing.|
|**[[13.3 Testing Server Components]]**|Server Component testing; async testing; data fetching mocks; testing patterns; best practices. Modern testing.|
|**[[13.4 Testing Server Actions]]**|Server Action testing; form testing; mutation testing; validation testing; error scenarios. Action testing.|
|**[[13.5 E2E Testing with Playwright]]**|Playwright setup; browser automation; E2E scenarios; visual testing; CI integration. End-to-end testing.|
|**[[13.6 Integration Testing]]**|API testing; database testing; integration scenarios; test databases; mocking external services. Integration tests.|
|**[[13.7 CI/CD & Testing]]**|GitHub Actions; automated testing; test pipelines; continuous integration; deployment gates. Automation.|
|**[[13.8 Project: Tested Application]]**|Building fully tested app; comprehensive test suite; unit tests; integration tests; E2E tests. Testing showcase.|

### **[[14 Deployment & Production]]**

Master deploying Next.js applications to production. Learn Vercel, Docker, AWS, and self-hosting. Build CI/CD pipelines and production workflows. Deployment knowledge is essential for all Next.js developers and frequently tested in interviews.

|Topic|Focus & Purpose|
|---|---|
|**[[14.1 Vercel Deployment]]**|Vercel platform; automatic deployments; preview deployments; environment variables; production settings. Official platform.|
|**[[14.2 Docker & Containerization]]**|Docker basics; Dockerfile for Next.js; multi-stage builds; docker-compose; container best practices. Containerization.|
|**[[14.3 AWS Deployment]]**|AWS Amplify; EC2; ECS; Lambda; S3; CloudFront; AWS deployment strategies. AWS hosting.|
|**[[14.4 Self-Hosting]]**|Node.js server; PM2; Nginx; reverse proxy; SSL certificates; server management. Custom hosting.|
|**[[14.5 Environment Variables]]**|.env files; environment management; secrets; production vs development; best practices. Configuration.|
|**[[14.6 CI/CD Pipelines]]**|GitHub Actions; GitLab CI; automated deployment; testing in CI; deployment workflows. Automation pipelines.|
|**[[14.7 Monitoring & Analytics]]**|Error tracking (Sentry); analytics (Vercel Analytics); logging; performance monitoring; observability. Production monitoring.|
|**[[14.8 Project: Production Deployment]]**|Deploying complete app; CI/CD setup; monitoring; environment config; production best practices. Real deployment.|

### **[[15 Advanced Next.js Patterns]]**

Master advanced Next.js patterns and architectures. Learn middleware, internationalization, monorepos, and enterprise patterns. Build sophisticated, scalable applications. Advanced patterns are required for senior-level Next.js positions.

|Topic|Focus & Purpose|
|---|---|
|**[[15.1 Middleware]]**|Middleware fundamentals; request/response modification; authentication middleware; redirects; rewrites; geolocation. Edge middleware.|
|**[[15.2 Internationalization (i18n)]]**|Multi-language apps; next-intl; locale routing; translations; RTL support; i18n best practices. Global applications.|
|**[[15.3 Monorepo Setup]]**|Turborepo; monorepo architecture; shared packages; workspace management; monorepo benefits. Large-scale apps.|
|**[[15.4 Micro-Frontends]]**|Micro-frontend architecture; module federation; independent deployments; team scalability. Enterprise architecture.|
|**[[15.5 Rate Limiting]]**|Rate limiting implementation; Upstash; Redis; API protection; DDoS prevention. API security.|
|**[[15.6 Webhooks Integration]]**|Webhook handlers; signature verification; processing webhooks; error handling; retry logic. External integrations.|
|**[[15.7 Background Jobs]]**|Queue systems; cron jobs; scheduled tasks; background processing; job queues. Async processing.|
|**[[15.8 Project: Enterprise Application]]**|Building enterprise app; advanced patterns; scalability; monitoring; security; best practices. Professional project.|

### **[[16 Real-World Projects]]**

Master building production-grade Next.js applications. Learn complete project workflows from design to deployment. Build impressive portfolio pieces that demonstrate job-ready skills. Real projects are essential for landing Next.js positions.

|Topic|Focus & Purpose|
|---|---|
|**[[16.1 E-Commerce Platform]]**|Full e-commerce app; product catalog; shopping cart; checkout; payment (Stripe); order management. Commercial application.|
|**[[16.2 SaaS Application]]**|Multi-tenant SaaS; authentication; subscription billing; dashboard; team management; admin panel. SaaS architecture.|
|**[[16.3 Social Media Platform]]**|Social network features; posts; comments; likes; follows; real-time updates; media uploads. Social app.|
|**[[16.4 CMS & Blog Platform]]**|Content management system; rich text editor; media library; publishing; SEO; multi-user. Content platform.|
|**[[16.5 Real-Time Chat Application]]**|WebSocket integration; real-time messaging; presence; typing indicators; message history. Real-time features.|
|**[[16.6 Job Board Platform]]**|Job listings; applications; company profiles; search & filtering; admin panel; notifications. Marketplace application.|
|**[[16.7 Analytics Dashboard]]**|Data visualization; charts; real-time data; reports; filtering; export functionality. Dashboard application.|
|**[[16.8 Full-Stack Production App]]**|Complete production application; all features; deployment; monitoring; documentation; showcase project. Portfolio centerpiece.|
