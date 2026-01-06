### **[[AS1 Astro Fundamentals & Setup]]**

Master Astro as the revolutionary web framework for content-focused websites. Learn why Astro ships zero JavaScript by default and achieves exceptional performance. Understand content collections, islands architecture, and why companies choose Astro for blogs, documentation, and marketing sites. Astro developers are increasingly sought for performance-critical projects. Essential for modern static site generation and content-driven web development.

|Topic|Focus & Purpose|
|---|---|
|**[[AS1.1 Astro Introduction]]**|What is Astro; islands architecture; zero-JS by default; content-focused design; Astro vs Next.js vs Gatsby; use cases. Industry context.|
|**[[AS1.2 react-Environment Setup]]**|Node.js requirements; create astro; npm create astro@latest; VS Code Astro extension; project templates. Professional setup.|
|**[[AS1.3 Project Structure]]**|src directory; pages; components; layouts; public folder; astro.config.mjs; folder conventions. File organization.|
|**[[AS1.4 Astro Components]]**|.astro file syntax; component script; component template; frontmatter; expressions; component imports. Core building blocks.|
|**[[AS1.5 Pages & Routing]]**|File-based routing; page components; dynamic routes; 404 pages; route parameters. Page creation.|
|**[[AS1.6 Development Server]]**|astro dev; hot reload; error overlay; preview command; development workflow. Dev experience.|
|**[[AS1.7 Project: First Astro Site]]**|Building landing page; components; pages; styling; deployment basics. First project.|

### **[[AS2 Components & Templating]]**

Master Astro component system for building reusable UI. Learn component syntax, props, slots, and composition patterns. Component mastery is fundamental for all Astro development and code organization.

|Topic|Focus & Purpose|
|---|---|
|**[[AS2.1 Component Anatomy]]**|Frontmatter section; template section; component script; imports; exports; file structure. Component structure.|
|**[[AS2.2 Props]]**|Defining props; Astro.props; TypeScript props; default values; prop destructuring; prop validation. Component inputs.|
|**[[AS2.3 Slots]]**|Default slot; named slots; slot fallbacks; conditional slots; slot composition. Content insertion.|
|**[[AS2.4 Component Composition]]**|Nesting components; layout components; component patterns; separation of concerns. Building UI.|
|**[[AS2.5 Expressions & Control Flow]]**|Template expressions; conditionals; loops; mapping arrays; fragments; dynamic content. Template logic.|
|**[[AS2.6 CSS & Styling]]**|Scoped styles; global styles; class:list directive; CSS variables; inline styles. Component styling.|
|**[[AS2.7 Project: Component Library]]**|Building reusable components; props; slots; documentation; composition patterns. Component project.|

### **[[AS3 Layouts & Page Structure]]**

Master Astro layouts for consistent page structure. Learn layout patterns, head management, and page composition. Layouts are essential for maintainable multi-page websites.

|Topic|Focus & Purpose|
|---|---|
|**[[AS3.1 Layout Basics]]**|Layout components; slot usage; wrapping pages; layout props; layout hierarchy. Page wrappers.|
|**[[AS3.2 Head Management]]**|<head> content; title; meta tags; link tags; script tags; canonical URLs. SEO fundamentals.|
|**[[AS3.3 Nested Layouts]]**|Multiple layouts; layout composition; layout inheritance; conditional layouts. Complex layouts.|
|**[[AS3.4 ViewTransitions Integration]]**|View Transitions API; page transitions; animation persistence; transition directives. Smooth navigation.|
|**[[AS3.5 Common Layout Patterns]]**|Header/footer layouts; sidebar layouts; auth layouts; documentation layouts. Layout patterns.|
|**[[AS3.6 SEO Component]]**|Reusable SEO component; Open Graph; Twitter cards; structured data; dynamic meta. SEO optimization.|
|**[[AS3.7 Project: Multi-Layout Site]]**|Building site with layouts; headers; footers; navigation; transitions. Layout project.|

### **[[AS4 Content Collections]]**

Master Astro Content Collections for managing structured content. Learn schemas, querying, and content validation. Content Collections are the cornerstone of content-driven Astro sites like blogs and documentation.

|Topic|Focus & Purpose|
|---|---|
|**[[AS4.1 Collections Basics]]**|Content directory; collection configuration; config.ts; content folder structure. Collection setup.|
|**[[AS4.2 Defining Schemas]]**|Zod schemas; field types; optional fields; default values; nested schemas; validation. Content schemas.|
|**[[AS4.3 Querying Content]]**|getCollection; getEntry; filtering; sorting; type safety; async queries. Content retrieval.|
|**[[AS4.4 Markdown Content]]**|Markdown files; frontmatter; MDX support; custom components in Markdown; processing. Markdown handling.|
|**[[AS4.5 Content References]]**|Reference fields; related content; content relationships; resolving references. Content relations.|
|**[[AS4.6 Dynamic Pages from Collections]]**|getStaticPaths; generating pages; slugs; pagination; content-driven routing. Dynamic generation.|
|**[[AS4.7 Data Collections]]**|JSON/YAML collections; data schemas; global data; reusable data. Non-content data.|
|**[[AS4.8 Project: Blog Platform]]**|Building blog; content collections; categories; tags; pagination; RSS feed. Content project.|

### **[[AS5 Islands Architecture & Interactivity]]**

Master Astro's islands architecture for selective hydration. Learn client directives, framework components, and performance optimization. Islands architecture is what makes Astro uniquely performant.

|Topic|Focus & Purpose|
|---|---|
|**[[AS5.1 Islands Concept]]**|Islands architecture; partial hydration; zero-JS default; selective interactivity; performance benefits. Core concept.|
|**[[AS5.2 Client Directives]]**|client:load; client:idle; client:visible; client:media; client:only; hydration strategies. Loading strategies.|
|**[[AS5.3 React in Astro]]**|@astrojs/react integration; React components; hydration; state management; hooks. React islands.|
|**[[AS5.4 Vue in Astro]]**|@astrojs/vue integration; Vue components; composition API; reactivity; Vue features. Vue islands.|
|**[[AS5.5 Svelte in Astro]]**|@astrojs/svelte integration; Svelte components; reactivity; transitions. Svelte islands.|
|**[[AS5.6 Multiple Frameworks]]**|Using multiple frameworks; framework selection; shared state; interoperability. Mixed frameworks.|
|**[[AS5.7 State Management]]**|nanostores; cross-framework state; persistent state; global stores. Island state.|
|**[[AS5.8 Project: Interactive Dashboard]]**|Building dashboard; React/Vue components; selective hydration; performance. Islands project.|

### **[[AS6 Styling & Assets]]**

Master styling approaches in Astro. Learn scoped CSS, Tailwind, CSS frameworks, and asset handling. Styling skills are essential for building polished, professional websites.

|Topic|Focus & Purpose|
|---|---|
|**[[AS6.1 Scoped Styles]]**|Component styles; :global directive; style inheritance; is:global; specificity. Astro styling.|
|**[[AS6.2 Tailwind CSS]]**|@astrojs/tailwind integration; configuration; dark mode; plugins; best practices. Utility-first styling.|
|**[[AS6.3 CSS Preprocessors]]**|Sass/SCSS; Less; Stylus; PostCSS; preprocessor configuration. Advanced CSS.|
|**[[AS6.4 CSS Frameworks]]**|Bootstrap; Bulma; component libraries; framework integration; customization. Pre-built styles.|
|**[[AS6.5 Images]]**|Built-in Image component; optimization; responsive images; remote images; formats. Image handling.|
|**[[AS6.6 Fonts]]**|Local fonts; Google Fonts; @fontsource; font optimization; preloading. Typography assets.|
|**[[AS6.7 Public Assets]]**|Public folder; static assets; referencing assets; asset organization. Static files.|
|**[[AS6.8 Project: Styled Portfolio]]**|Building portfolio; Tailwind; images; fonts; responsive design; animations. Styling project.|

### **[[AS7 Data Fetching & APIs]]**

Master data fetching in Astro for dynamic content. Learn fetch, endpoints, and external data integration. Data fetching connects your static site to dynamic content sources.

|Topic|Focus & Purpose|
|---|---|
|**[[AS7.1 Fetching in Components]]**|Fetch in frontmatter; async components; data at build time; static data. Component data.|
|**[[AS7.2 API Endpoints]]**|src/pages/api; GET/POST handlers; JSON responses; dynamic endpoints. Server endpoints.|
|**[[AS7.3 External APIs]]**|Fetching third-party APIs; API keys; environment variables; error handling. External data.|
|**[[AS7.4 Headless CMS]]**|Contentful; Sanity; Strapi; Storyblok; CMS integration patterns. CMS integration.|
|**[[AS7.5 Database Connection]]**|Turso/LibSQL; Prisma; database queries; data layer; persistence. Database access.|
|**[[AS7.6 GraphQL]]**|GraphQL queries; Apollo; URQL; GraphQL CMS; typed queries. GraphQL integration.|
|**[[AS7.7 Project: Data-Driven Site]]**|Building with external data; CMS integration; API endpoints; caching. Data project.|

### **[[AS8 Server-Side Rendering]]**

Master Astro SSR for dynamic server-rendered pages. Learn adapters, hybrid rendering, and server features. SSR extends Astro beyond static sites for dynamic applications.

|Topic|Focus & Purpose|
|---|---|
|**[[AS8.1 SSR Basics]]**|SSR vs SSG; output: 'server'; dynamic pages; request handling; server context. SSR fundamentals.|
|**[[AS8.2 Adapters]]**|Node adapter; Vercel adapter; Netlify adapter; Cloudflare adapter; adapter configuration. Deployment targets.|
|**[[AS8.3 Hybrid Rendering]]**|output: 'hybrid'; prerender directive; selective SSR; static + dynamic mixing. Flexible rendering.|
|**[[AS8.4 Server Context]]**|Astro.request; Astro.cookies; headers; URL; server-side data. Request handling.|
|**[[AS8.5 Authentication]]**|Session handling; cookies; auth middleware; protected routes; login flows. User auth.|
|**[[AS8.6 Middleware]]**|Middleware concept; request/response; authentication; redirects; logging. Request processing.|
|**[[AS8.7 Project: Dynamic Application]]**|Building SSR app; authentication; dynamic data; server features. SSR project.|

### **[[AS9 Integrations & Ecosystem]]**

Master Astro integrations for extended functionality. Learn official integrations, community packages, and custom integrations. Integrations unlock advanced features and third-party tools.

|Topic|Focus & Purpose|
|---|---|
|**[[AS9.1 Integration Basics]]**|Adding integrations; astro add; configuration; integration types. Integration system.|
|**[[AS9.2 UI Framework Integrations]]**|React; Vue; Svelte; Solid; Preact; Lit; multiple frameworks. Framework support.|
|**[[AS9.3 SSR Adapters]]**|Node; Vercel; Netlify; Cloudflare; Deno; deployment adapters. Platform adapters.|
|**[[AS9.4 MDX Integration]]**|@astrojs/mdx; components in Markdown; MDX configuration; custom components. Enhanced Markdown.|
|**[[AS9.5 Sitemap & RSS]]**|@astrojs/sitemap; @astrojs/rss; SEO automation; feed generation. SEO integrations.|
|**[[AS9.6 Image Services]]**|Sharp; Squoosh; image optimization; custom image services. Image processing.|
|**[[AS9.7 Custom Integrations]]**|Integration API; hooks; creating integrations; publishing integrations. Building integrations.|
|**[[AS9.8 Project: Fully Integrated Site]]**|Building site with integrations; MDX; sitemap; RSS; optimizations. Integration project.|

### **[[AS10 Performance & Optimization]]**

Master Astro performance optimization. Learn bundle analysis, loading optimization, and Core Web Vitals. Performance is Astro's primary advantage and key selling point.

|Topic|Focus & Purpose|
|---|---|
|**[[AS10.1 Zero-JS Philosophy]]**|Default behavior; when to add JavaScript; minimal hydration; performance mindset. Core philosophy.|
|**[[AS10.2 Bundle Analysis]]**|Analyzing builds; JavaScript audit; hydration audit; bundle size tracking. Build analysis.|
|**[[AS10.3 Image Optimization]]**|Built-in optimization; formats (WebP, AVIF); lazy loading; responsive images. Image performance.|
|**[[AS10.4 Font Optimization]]**|Font loading; font-display; subsetting; preloading; performance impact. Font handling.|
|**[[AS10.5 Core Web Vitals]]**|LCP; FID/INP; CLS; measurement; optimization strategies; Lighthouse. Performance metrics.|
|**[[AS10.6 Preloading & Prefetching]]**|Resource hints; prefetch; preload; link preload; navigation optimization. Loading optimization.|
|**[[AS10.7 Project: Performance Audit]]**|Optimizing site; performance testing; achieving 100 Lighthouse; documentation. Optimization project.|

### **[[AS11 SEO & Marketing]]**

Master SEO for Astro sites. Learn meta tags, structured data, sitemaps, and marketing features. SEO skills are essential for content-focused sites to achieve visibility.

|Topic|Focus & Purpose|
|---|---|
|**[[AS11.1 Meta Tags]]**|Title; description; robots; viewport; canonical; Open Graph; Twitter Cards. Essential meta.|
|**[[AS11.2 Structured Data]]**|JSON-LD; Schema.org; article schema; breadcrumbs; rich snippets. Search enhancements.|
|**[[AS11.3 Sitemaps]]**|@astrojs/sitemap; dynamic sitemaps; configuration; submission. Search discovery.|
|**[[AS11.4 RSS Feeds]]**|@astrojs/rss; feed generation; customization; feed readers. Content syndication.|
|**[[AS11.5 Robots.txt]]**|Robots configuration; crawl rules; sitemap reference. Crawler control.|
|**[[AS11.6 Analytics Integration]]**|Google Analytics; Plausible; Fathom; privacy-focused analytics. Traffic tracking.|
|**[[AS11.7 Project: SEO-Optimized Blog]]**|Building SEO blog; all meta; structured data; sitemaps; analytics. SEO project.|

### **[[AS12 Deployment & Hosting]]**

Master deploying Astro sites to production. Learn hosting platforms, CI/CD, and deployment configuration. Deployment skills are essential for shipping real-world websites.

|Topic|Focus & Purpose|
|---|---|
|**[[AS12.1 Static Deployment]]**|Building static; static hosting; GitHub Pages; Surge; basic deployment. Static hosting.|
|**[[AS12.2 Vercel Deployment]]**|Vercel adapter; automatic deployment; environment variables; preview deployments. Vercel hosting.|
|**[[AS12.3 Netlify Deployment]]**|Netlify adapter; build settings; forms; functions; edge functions. Netlify hosting.|
|**[[AS12.4 Cloudflare Pages]]**|Cloudflare adapter; Workers; edge rendering; global deployment. Cloudflare hosting.|
|**[[AS12.5 Docker & Self-Hosting]]**|Docker setup; Node server; PM2; Nginx; self-hosted SSR. Self-hosting.|
|**[[AS12.6 CI/CD Pipelines]]**|GitHub Actions; automated builds; testing; preview deployments. Automation.|
|**[[AS12.7 Project: Production Deployment]]**|Complete deployment; CI/CD; monitoring; environment configuration. Deployment project.|

### **[[AS13 Real-World Projects]]**

Master building production-grade Astro websites. Build impressive portfolio pieces that demonstrate job-ready skills. Real projects are essential for landing Astro positions and freelance work.

|Topic|Focus & Purpose|
|---|---|
|**[[AS13.1 Documentation Site]]**|Starlight theme; sidebar; search; versioning; code blocks; MDX. Technical docs.|
|**[[AS13.2 Marketing Website]]**|Landing pages; CTAs; testimonials; pricing; animations; conversion. Business site.|
|**[[AS13.3 Blog Platform]]**|Content collections; categories; authors; comments; pagination; RSS. Content platform.|
|**[[AS13.4 Portfolio Site]]**|Project showcase; case studies; about; contact; animations; responsive. Personal branding.|
|**[[AS13.5 E-Commerce Storefront]]**|Product pages; cart (Snipcart); checkout; Stripe; product data. E-commerce.|
|**[[AS13.6 SaaS Landing Page]]**|Feature sections; pricing tables; FAQ; testimonials; CTA sections. SaaS marketing.|
|**[[AS13.7 Agency Website]]**|Services; portfolio; team; contact; case studies; animations. Agency site.|
|**[[AS13.8 Production Website]]**|Complete production site; all features; optimization; deployment. Portfolio centerpiece.|
