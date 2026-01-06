### **[[01 Vite Fundamentals & Setup]]**

Master Vite as the next-generation frontend build tool that's revolutionizing web development. Learn why Vite is adopted by Vue, React, Svelte, and major companies for its lightning-fast development experience. Understand how Vite leverages native ES modules and esbuild for 10-100x faster builds than traditional bundlers. Vite skills are increasingly demanded as projects migrate from Webpack. Essential for modern frontend tooling mastery and developer productivity.

|Topic|Focus & Purpose|
|---|---|
|**[[1.1 Vite Introduction]]**|What is Vite; Vite vs Webpack vs Parcel; native ESM; dev server architecture; why Vite is fast; ecosystem overview. Industry context.|
|**[[1.2 Environment Setup]]**|Node.js requirements; create-vite; npm create vite@latest; VS Code integration; project templates; initial configuration. Professional setup.|
|**[[1.3 Project Structure]]**|Default structure; index.html as entry; src directory; public folder; assets handling; configuration files. File organization.|
|**[[1.4 Development Server]]**|Dev server features; hot module replacement (HMR); instant server start; on-demand compilation; dependency pre-bundling. Development experience.|
|**[[1.5 First Vite Project]]**|Creating vanilla project; understanding entry points; module imports; CSS imports; asset handling basics. Building foundation.|
|**[[1.6 Vite CLI]]**|vite command; vite build; vite preview; CLI options; scripts configuration; environment modes. Command line usage.|
|**[[1.7 Project: Vanilla Vite App]]**|Building first Vite app; JavaScript modules; CSS imports; assets; dev workflow. First project.|

### **[[02 Configuration & Customization]]**

Master Vite configuration for project customization. Learn vite.config.js, build options, and server configuration. Configuration knowledge is essential for adapting Vite to different project requirements and team standards.

|Topic|Focus & Purpose|
|---|---|
|**[[2.1 vite.config.js Basics]]**|Configuration file; defineConfig; IntelliSense; TypeScript config; configuration options overview. Config foundation.|
|**[[2.2 Server Configuration]]**|Port; host; proxy; HTTPS; CORS; headers; open browser; HMR options. Dev server customization.|
|**[[2.3 Build Configuration]]**|Output directory; asset handling; minification; source maps; target browsers; chunk splitting. Build options.|
|**[[2.4 Resolve Options]]**|Alias configuration; extensions; main fields; conditions; dedupe; module resolution. Path resolution.|
|**[[2.5 Environment Variables]]**|.env files; VITE_ prefix; import.meta.env; modes; environment modes; type definitions. Configuration by environment.|
|**[[2.6 Conditional Config]]**|Mode-based config; command detection; SSR config; library mode config; dynamic configuration. Advanced config.|
|**[[2.7 Project: Configured Build]]**|Complete configuration; aliases; proxy; environment variables; build optimization. Config project.|

### **[[03 Framework Integration]]**

Master Vite with popular frontend frameworks. Learn React, Vue, Svelte, and other framework integrations. Framework integration is the primary use case for Vite in production applications.

|Topic|Focus & Purpose|
|---|---|
|**[[3.1 React + Vite]]**|@vitejs/plugin-react; JSX support; Fast Refresh; React configuration; TypeScript with React. React projects.|
|**[[3.2 Vue + Vite]]**|@vitejs/plugin-vue; SFC support; Vue 3 features; script setup; Vue devtools. Vue projects.|
|**[[3.3 Svelte + Vite]]**|@sveltejs/vite-plugin-svelte; Svelte configuration; SvelteKit considerations; Svelte features. Svelte projects.|
|**[[3.4 TypeScript Integration]]**|TypeScript support; tsconfig.json; type checking; vite-plugin-checker; strict mode. Type-safe development.|
|**[[3.5 Preact + Vite]]**|Preact configuration; aliasing React; @preact/preset-vite; Preact signals. Lightweight React alternative.|
|**[[3.6 Solid.js + Vite]]**|vite-plugin-solid; Solid configuration; JSX transformation; Solid features. Solid projects.|
|**[[3.7 Multi-Framework Support]]**|Framework comparison; choosing frameworks; migration paths; framework-agnostic features. Framework decisions.|
|**[[3.8 Project: Framework Starter]]**|Building framework project; configuration; TypeScript; dev workflow; production build. Framework project.|

### **[[04 Asset Handling]]**

Master asset management in Vite projects. Learn static assets, CSS, images, fonts, and optimization. Asset handling is crucial for building performant web applications with proper resource management.

|Topic|Focus & Purpose|
|---|---|
|**[[4.1 Static Assets]]**|Importing assets; URL imports; public directory; asset references; raw imports. Asset basics.|
|**[[4.2 CSS Handling]]**|CSS imports; CSS Modules; preprocessors (Sass, Less, Stylus); PostCSS; CSS splitting. Stylesheet management.|
|**[[4.3 CSS Modules]]**|Module syntax; scoped styles; composition; naming conventions; TypeScript definitions. Scoped CSS.|
|**[[4.4 Image Optimization]]**|Image imports; small images as base64; image formats; vite-imagetools; responsive images. Image handling.|
|**[[4.5 Font Loading]]**|Font imports; @font-face; Google Fonts; local fonts; font optimization; preloading. Typography assets.|
|**[[4.6 JSON & Data]]**|JSON imports; named exports; data files; YAML/TOML plugins; static data handling. Data imports.|
|**[[4.7 WebAssembly]]**|WASM imports; initialization; helper patterns; WASM performance; use cases. WASM support.|
|**[[4.8 Project: Asset-Heavy Site]]**|Building media site; images; fonts; CSS Modules; optimization; lazy loading. Asset project.|

### **[[05 Plugins & Ecosystem]]**

Master Vite's plugin system and ecosystem. Learn official plugins, community plugins, and plugin development. Plugin knowledge extends Vite's capabilities for specialized project needs.

|Topic|Focus & Purpose|
|---|---|
|**[[5.1 Plugin Basics]]**|Plugin concept; using plugins; plugin ordering; plugin arrays; official plugins overview. Plugin fundamentals.|
|**[[5.2 Official Plugins]]**|@vitejs/plugin-react; @vitejs/plugin-vue; @vitejs/plugin-legacy; plugin configurations. Core plugins.|
|**[[5.3 Popular Community Plugins]]**|vite-plugin-pwa; unplugin-icons; vite-plugin-compression; essential plugins. Ecosystem plugins.|
|**[[5.4 Legacy Browser Support]]**|@vitejs/plugin-legacy; polyfills; target browsers; modern/legacy bundles. Browser compatibility.|
|**[[5.5 PWA Support]]**|vite-plugin-pwa; service workers; manifest; offline support; installability. Progressive web apps.|
|**[[5.6 Plugin Development]]**|Plugin API; hooks; virtual modules; transform hooks; building custom plugins. Creating plugins.|
|**[[5.7 Rollup Plugin Compatibility]]**|Rollup plugins in Vite; compatibility; plugin adaptation; when to use. Rollup ecosystem.|
|**[[5.8 Project: Plugin Integration]]**|Integrating multiple plugins; PWA; compression; icons; optimization. Plugin project.|

### **[[06 Build Optimization]]**

Master Vite build optimization for production. Learn code splitting, tree shaking, chunk optimization, and performance tuning. Build optimization is critical for production application performance.

|Topic|Focus & Purpose|
|---|---|
|**[[6.1 Production Builds]]**|vite build command; Rollup bundling; output analysis; build modes; production configuration. Build process.|
|**[[6.2 Code Splitting]]**|Dynamic imports; chunk splitting; manual chunks; vendor chunking; route-based splitting. Bundle optimization.|
|**[[6.3 Tree Shaking]]**|Tree shaking in Vite; side effects; sideEffects flag; optimizing imports; dead code elimination. Bundle size.|
|**[[6.4 Minification]]**|esbuild minification; terser option; CSS minification; HTML minification; minification options. Code compression.|
|**[[6.5 Bundle Analysis]]**|rollup-plugin-visualizer; analyzing bundles; identifying issues; optimization opportunities. Bundle inspection.|
|**[[6.6 Caching & Hashing]]**|File hashing; cache busting; asset fingerprinting; long-term caching; hash strategies. Caching strategy.|
|**[[6.7 Build Performance]]**|Build speed optimization; parallel builds; caching builds; CI optimization; build benchmarking. Build efficiency.|
|**[[6.8 Project: Optimized Build]]**|Full optimization; code splitting; analysis; performance testing; production-ready build. Optimization project.|

### **[[07 Development Features]]**

Master Vite's development features for optimal developer experience. Learn HMR, debugging, and development workflows. Development features maximize productivity during active development.

|Topic|Focus & Purpose|
|---|---|
|**[[7.1 Hot Module Replacement]]**|HMR mechanism; HMR API; module acceptance; HMR boundaries; framework HMR. Instant updates.|
|**[[7.2 Development Debugging]]**|Source maps; browser DevTools; VS Code debugging; error overlay; debugging strategies. Debug experience.|
|**[[7.3 Dependency Pre-Bundling]]**|Pre-bundling purpose; esbuild optimization; include/exclude; force re-bundling; dependency handling. Dependency optimization.|
|**[[7.4 Glob Imports]]**|import.meta.glob; eager vs lazy; import patterns; dynamic imports; file discovery. Bulk imports.|
|**[[7.5 Worker Support]]**|Web Workers; import syntax; worker options; shared workers; worker bundling. Workers in Vite.|
|**[[7.6 Server-Sent Events]]**|SSE for HMR; connection handling; custom SSE; development communication. Dev server features.|
|**[[7.7 Project: DX Optimized]]**|Maximum developer experience; fast HMR; debugging setup; development workflow. DX project.|

### **[[08 Testing Integration]]**

Master testing with Vite projects. Learn Vitest, component testing, and E2E testing integration. Testing is essential for production-quality applications and professional development.

|Topic|Focus & Purpose|
|---|---|
|**[[8.1 Vitest Introduction]]**|Vitest as Vite-native test runner; compatibility with Jest; configuration; watch mode. Vite testing.|
|**[[8.2 Vitest Configuration]]**|vitest.config.ts; test environment; globals; coverage; reporters; setup files. Test setup.|
|**[[8.3 Unit Testing]]**|Writing unit tests; assertions; mocking; test organization; TDD with Vitest. Unit tests.|
|**[[8.4 Component Testing]]**|Testing React/Vue components; @testing-library integration; mounting; queries. Component tests.|
|**[[8.5 Coverage Reports]]**|Code coverage; c8/istanbul; coverage thresholds; coverage reports; CI integration. Test coverage.|
|**[[8.6 E2E Integration]]**|Playwright with Vite; Cypress with Vite; E2E configuration; dev server integration. End-to-end testing.|
|**[[8.7 Project: Tested Application]]**|Complete test setup; unit tests; component tests; coverage; CI pipeline. Testing project.|

### **[[09 Server-Side Rendering]]**

Master SSR with Vite for universal applications. Learn SSR setup, streaming, and framework SSR integration. SSR skills are essential for SEO-critical and performance-focused applications.

|Topic|Focus & Purpose|
|---|---|
|**[[9.1 SSR Fundamentals]]**|SSR concept; Vite SSR support; development SSR; production SSR; SSR benefits. SSR basics.|
|**[[9.2 SSR Configuration]]**|SSR build; entry points; server/client builds; noExternal; SSR externals. SSR setup.|
|**[[9.3 React SSR]]**|React SSR with Vite; renderToString; hydration; streaming SSR; React 18 features. React server rendering.|
|**[[9.4 Vue SSR]]**|Vue SSR with Vite; renderToString; hydration; Nuxt comparison; Vue SSR patterns. Vue server rendering.|
|**[[9.5 Streaming SSR]]**|Streaming responses; progressive rendering; suspense boundaries; performance benefits. Modern SSR.|
|**[[9.6 SSR Frameworks]]**|SvelteKit; Astro; Remix; SSR framework comparison; when to use frameworks. Meta-frameworks.|
|**[[9.7 Project: SSR Application]]**|Building SSR app; server setup; hydration; production deployment. SSR project.|

### **[[10 Library Mode]]**

Master building libraries with Vite. Learn library configuration, output formats, and publishing. Library mode is essential for creating reusable packages and component libraries.

|Topic|Focus & Purpose|
|---|---|
|**[[10.1 Library Mode Basics]]**|build.lib configuration; entry points; library naming; output configuration. Library builds.|
|**[[10.2 Output Formats]]**|ES modules; UMD; CommonJS; format selection; multiple formats; bundling strategies. Module formats.|
|**[[10.3 External Dependencies]]**|Externalization; peer dependencies; rollupOptions.external; bundling decisions. Dependency handling.|
|**[[10.4 TypeScript Declarations]]**|Generating .d.ts files; vite-plugin-dts; declaration output; type bundling. Type support.|
|**[[10.5 CSS in Libraries]]**|CSS handling; CSS injection; separate CSS files; styled components libraries. Library styling.|
|**[[10.6 Publishing]]**|package.json configuration; npm publishing; exports field; module/main fields. Distribution.|
|**[[10.7 Project: Component Library]]**|Building reusable library; TypeScript; documentation; publishing preparation. Library project.|

### **[[11 Monorepo & Workspaces]]**

Master Vite in monorepo setups. Learn workspace configuration, shared dependencies, and multi-package management. Monorepo skills are essential for large-scale applications and team collaboration.

|Topic|Focus & Purpose|
|---|---|
|**[[11.1 Monorepo Basics]]**|Monorepo concept; npm/pnpm workspaces; package organization; shared dependencies. Monorepo fundamentals.|
|**[[11.2 Turborepo Integration]]**|Turborepo with Vite; task running; caching; pipeline configuration; build optimization. Build orchestration.|
|**[[11.3 Shared Configuration]]**|Shared vite.config; base configuration; extending configs; config packages. Config sharing.|
|**[[11.4 Internal Packages]]**|Package linking; TypeScript paths; development workflow; package references. Package development.|
|**[[11.5 Build Orchestration]]**|Build order; dependency builds; watch mode; development workflow; CI builds. Coordinated builds.|
|**[[11.6 Project: Monorepo Setup]]**|Complete monorepo; multiple apps; shared library; build pipeline; development workflow. Monorepo project.|

### **[[12 Deployment & DevOps]]**

Master deploying Vite applications. Learn hosting platforms, CI/CD, and production workflows. Deployment knowledge is essential for shipping real-world applications.

|Topic|Focus & Purpose|
|---|---|
|**[[12.1 Static Deployment]]**|Static hosting; Netlify; Vercel; GitHub Pages; Cloudflare Pages; deployment configuration. Static hosting.|
|**[[12.2 Docker Deployment]]**|Dockerfile for Vite; multi-stage builds; nginx configuration; container optimization. Containerization.|
|**[[12.3 CI/CD Pipelines]]**|GitHub Actions; GitLab CI; automated builds; preview deployments; deployment automation. CI/CD.|
|**[[12.4 Environment Configuration]]**|Production environment; environment variables; build-time vs runtime; secrets management. Environment handling.|
|**[[12.5 CDN & Caching]]**|CDN integration; cache headers; asset caching; cache invalidation; performance. Content delivery.|
|**[[12.6 Preview Deployments]]**|PR previews; branch deployments; review apps; preview environments. Collaborative deployment.|
|**[[12.7 Project: Production Pipeline]]**|Complete CI/CD; automated testing; preview deployments; production deployment. Deployment project.|

### **[[13 Migration & Integration]]**

Master migrating to Vite from other build tools. Learn migration strategies, compatibility, and integration patterns. Migration skills are valuable as teams move from legacy build systems.

|Topic|Focus & Purpose|
|---|---|
|**[[13.1 Webpack to Vite]]**|Migration strategy; configuration mapping; loader to plugin; common issues; migration path. Webpack migration.|
|**[[13.2 CRA to Vite]]**|Create React App migration; configuration changes; ejected CRA; smooth transition. CRA migration.|
|**[[13.3 Vue CLI to Vite]]**|Vue CLI migration; configuration mapping; plugin equivalents; Vue-specific considerations. Vue CLI migration.|
|**[[13.4 Compatibility Challenges]]**|CommonJS issues; require() handling; node builtins; polyfills; compatibility plugins. Solving issues.|
|**[[13.5 Incremental Migration]]**|Gradual migration; parallel builds; feature flags; testing migration; rollback strategies. Safe migration.|
|**[[13.6 Project: Migration Project]]**|Complete migration; from Webpack/CRA; testing; optimization; validation. Migration project.|

### **[[14 Advanced Patterns]]**

Master advanced Vite patterns and features. Learn performance optimization, custom integrations, and enterprise patterns. Advanced patterns are required for complex applications and senior-level positions.

|Topic|Focus & Purpose|
|---|---|
|**[[14.1 Custom Middleware]]**|Vite server middleware; custom routes; API mocking; development proxies. Dev server extension.|
|**[[14.2 Virtual Modules]]**|Virtual module concept; plugin virtual modules; dynamic content; configuration as modules. Advanced plugins.|
|**[[14.3 Multi-Page Apps]]**|MPA configuration; multiple entry points; shared assets; page-specific bundles. Multi-page setup.|
|**[[14.4 Micro-Frontends]]**|Module federation concept; vite-plugin-federation; independent deployments; shared dependencies. Micro-frontend architecture.|
|**[[14.5 Backend Integration]]**|Express integration; NestJS; Rails; Django; backend proxying; API development. Backend alignment.|
|**[[14.6 Performance Tuning]]**|Build performance; dev server performance; large project optimization; profiling. Performance optimization.|
|**[[14.7 Project: Enterprise Setup]]**|Enterprise-grade configuration; multi-app; shared components; optimized pipeline. Advanced project.|
