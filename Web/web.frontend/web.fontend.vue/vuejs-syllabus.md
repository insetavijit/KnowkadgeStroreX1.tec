### **[[V1 Vue.js Fundamentals & Setup]]**

Master Vue.js as the progressive JavaScript framework loved by developers worldwide. Learn why Vue powers applications at Alibaba, Xiaomi, GitLab, and BMW. Understand Vue's approachable syntax, reactivity system, and incremental adoption that makes it perfect for both beginners and large-scale applications. Vue.js developers earn $90k-$135k annually with growing demand. Essential for frontend development and a top choice for enterprise applications.

| Topic                              | Focus & Purpose                                                                                                                                 |
| ---------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| **[[V1.1 Vue.js Introduction]]**    | What is Vue; progressive framework philosophy; Vue 2 vs Vue 3; Options vs Composition API; ecosystem overview; market demand. Industry context. |
| **[[V1.2 react-Environment Setup]]**      | Node.js setup; create-vue; Vite; VS Code Volar extension; Vue DevTools; project templates. Professional setup.                                  |
| **[[V1.3 Project Structure]]**      | Vite Vue project; src directory; components folder; assets; main.js; App.vue. File organization.                                                |
| **[[V1.4 Vue Components]]**         | Single File Components (.vue); template; script; style; component basics. Building blocks.                                                      |
| **[[V1.5 Template Syntax]]**        | Interpolation; directives; v-bind; v-on; expressions; dynamic attributes. Template fundamentals.                                                |
| **[[V1.6 Development Tools]]**      | Vue DevTools; component inspection; state debugging; timeline; performance. Debugging tools.                                                    |
| **[[V1.7 Project: Hello Vue App]]** | Building first Vue app; components; styling; data binding; development workflow. First project.                                                 |

### **[[V2 Reactivity & Data Binding]]**

Master Vue's reactivity system for dynamic applications. Learn reactive data, computed properties, and watchers. Reactivity is the core concept that makes Vue powerful and is tested in every interview.

|Topic|Focus & Purpose|
|---|---|
|**[[V2.1 Reactive Data]]**|ref(); reactive(); data binding; reactivity basics; reactive primitives vs objects. Core reactivity.|
|**[[V2.2 Template Binding]]**|Text interpolation; v-bind; attribute binding; class binding; style binding. Data display.|
|**[[V2.3 Computed Properties]]**|computed(); derived state; caching; getters and setters; vs methods. Derived data.|
|**[[V2.4 Watchers]]**|watch(); watchEffect(); immediate; deep watching; cleanup; side effects. Reactive effects.|
|**[[V2.5 Event Handling]]**|v-on directive; @shorthand; event modifiers; inline handlers; method handlers. User interactions.|
|**[[V2.6 Two-Way Binding]]**|v-model; form inputs; modifiers (.lazy, .number, .trim); custom v-model. Input binding.|
|**[[V2.7 Reactivity in Depth]]**|Reactivity internals; Proxy; ref vs reactive; toRefs; unref; reactivity utils. Advanced reactivity.|
|**[[V2.8 Project: Interactive Form]]**|Building reactive form; validation; computed; watchers; v-model; submission. Reactivity project.|

### **[[V3 Components Deep Dive]]**

Master Vue component architecture for scalable applications. Learn props, events, slots, and component patterns. Component mastery is essential for all Vue development and code organization.

|Topic|Focus & Purpose|
|---|---|
|**[[V3.1 Component Registration]]**|Local vs global registration; component naming; PascalCase; async components. Component setup.|
|**[[V3.2 Props]]**|Defining props; prop types; required; default values; prop validation; readonly. Component inputs.|
|**[[V3.3 Events]]**|$emit; defineEmits; event arguments; event naming; v-model on components. Component outputs.|
|**[[V3.4 Slots]]**|Default slots; named slots; scoped slots; slot props; dynamic slots. Content distribution.|
|**[[V3.5 Provide/Inject]]**|provide(); inject(); dependency injection; reactive provide; symbol keys. Deep data passing.|
|**[[V3.6 Component Lifecycle]]**|Lifecycle hooks; onMounted; onUnmounted; onUpdated; setup timing. Component lifecycle.|
|**[[V3.7 Dynamic Components]]**|<component :is>; keep-alive; component caching; transition between components. Dynamic rendering.|
|**[[V3.8 Project: Component Library]]**|Building reusable components; props; events; slots; documentation. Component project.|

### **[[V4 Composition API]]**

Master Vue 3 Composition API for modern Vue development. Learn composables, script setup, and code organization. Composition API is the standard for new Vue 3 projects and required for professional Vue development.

| Topic                                   | Focus & Purpose                                                                                   |
| --------------------------------------- | ------------------------------------------------------------------------------------------------- |
| **[[V4.1 Composition API Basics]]**      | setup() function; reactive state; lifecycle in setup; returning values. API fundamentals.         |
| **[[V4.2 Script Setup]]**                | script setup ; compiler macro; defineProps; defineEmits; defineExpose. Modern syntax.             |
| **[[V4.3 Composables]]**                 | Creating composables; reusable logic; conventions; composition; sharing state. Code reuse.        |
| **[[V4.4 Refs & Reactive]]**             | ref(); reactive(); toRef; toRefs; isRef; unref; shallowRef. Reactivity utilities.                 |
| **[[V4.5 Computed & Watch]]**            | computed(); watch(); watchEffect(); watchPostEffect; cleanup. Derived state.                      |
| **[[V4.6 Template Refs]]**               | Template refs; ref attribute; component refs; accessing DOM; focus management. DOM access.        |
| **[[V4.7 Lifecycle Hooks]]**             | onMounted; onUnmounted; onBeforeMount; onUpdated; hook timing. Lifecycle in Composition.          |
| **[[V4.8 Project: Composable Library]]** | Building composables; useFetch; useLocalStorage; useDebounce; documentation. Composables project. |

### **[[V5 Routing with Vue Router]]**

Master Vue Router for single-page application navigation. Learn dynamic routes, navigation guards, and nested routes. Routing is essential for all multi-page Vue applications.

|Topic|Focus & Purpose|
|---|---|
|**[[V5.1 Router Setup]]**|Vue Router installation; createRouter; history modes; router configuration. Router basics.|
|**[[V5.2 Routes & Navigation]]**|Route definitions; RouterLink; RouterView; programmatic navigation; route naming. Basic routing.|
|**[[V5.3 Dynamic Routes]]**|Route parameters; useRoute; params; props mode; optional parameters. Dynamic segments.|
|**[[V5.4 Nested Routes]]**|Children routes; nested RouterView; layout routes; route nesting patterns. Nested navigation.|
|**[[V5.5 Navigation Guards]]**|beforeEach; beforeEnter; beforeRouteEnter; async guards; navigation flow. Route protection.|
|**[[V5.6 Route Meta]]**|Meta fields; authentication flags; breadcrumbs; SEO data; middleware patterns. Route metadata.|
|**[[V5.7 Lazy Loading]]**|Dynamic imports; route-level code splitting; loading states; prefetching. Performance.|
|**[[V5.8 Project: Multi-Page App]]**|Building SPA; routing; guards; nested routes; navigation; loading. Router project.|

### **[[V6 State Management with Pinia]]**

Master Pinia as the official Vue state management library. Learn stores, actions, getters, and state patterns. State management is critical for complex Vue applications.

|Topic|Focus & Purpose|
|---|---|
|**[[V6.1 Pinia Introduction]]**|What is Pinia; Pinia vs Vuex; store concept; installation; devtools. State management.|
|**[[V6.2 Defining Stores]]**|defineStore; state; getters; actions; setup stores; options stores. Store creation.|
|**[[V6.3 Using Stores]]**|Store instances; accessing state; calling actions; storeToRefs; reactivity. Store usage.|
|**[[V6.4 Getters]]**|Computed state; getter arguments; using other getters; caching behavior. Derived state.|
|**[[V6.5 Actions]]**|Async actions; error handling; calling other actions; action composition. State mutations.|
|**[[V6.6 Store Composition]]**|Multiple stores; store dependencies; modular state; cross-store access. Store organization.|
|**[[V6.7 Plugins & Persistence]]**|Pinia plugins; persisted state; hydration; storage integration. Extending Pinia.|
|**[[V6.8 Project: E-Commerce Cart]]**|Building cart store; products; cart; checkout; persistence. State project.|

### **[[V7 Forms & Validation]]**

Master form handling in Vue applications. Learn form binding, validation libraries, and complex form patterns. Form skills are essential for data-driven applications.

|Topic|Focus & Purpose|
|---|---|
|**[[V7.1 Form Basics]]**|v-model; form elements; input types; textarea; select; form submission. Form fundamentals.|
|**[[V7.2 Input Modifiers]]**|.lazy; .number; .trim; custom modifiers; modifier combinations. Input processing.|
|**[[V7.3 Form Validation]]**|Manual validation; VeeValidate; Vuelidate; Zod; schema validation. Data validation.|
|**[[V7.4 VeeValidate]]**|VeeValidate setup; Field; Form; validation rules; error messages; Yup integration. Validation library.|
|**[[V7.5 Complex Forms]]**|Multi-step forms; dynamic fields; field arrays; conditional fields. Advanced forms.|
|**[[V7.6 File Uploads]]**|File input; image preview; upload handling; progress; cloud upload. File handling.|
|**[[V7.7 Form Accessibility]]**|Labels; ARIA; error announcements; keyboard navigation; accessible forms. A11y forms.|
|**[[V7.8 Project: Registration Form]]**|Complete form; validation; multi-step; file upload; submission. Form project.|

### **[[V8 Styling & UI]]**

Master styling approaches for Vue applications. Learn scoped styles, CSS frameworks, and component libraries. Styling skills are essential for building polished user interfaces.

|Topic|Focus & Purpose|
|---|---|
|**[[V8.1 Scoped Styles]]**|<style scoped>; style isolation; deep selectors; :deep(); :slotted(). Component styles.|
|**[[V8.2 CSS Modules]]**|CSS Modules in Vue; :class binding; module naming; usage patterns. Module styling.|
|**[[V8.3 Tailwind CSS]]**|Tailwind + Vue; configuration; utility classes; responsive design. Utility-first.|
|**[[V8.4 Component Libraries]]**|Vuetify; Naive UI; PrimeVue; Element Plus; Quasar; library comparison. Pre-built UI.|
|**[[V8.5 Transitions]]**|<Transition>; <TransitionGroup>; CSS transitions; JavaScript hooks; animation. Motion design.|
|**[[V8.6 Dynamic Classes]]**|Class binding; object syntax; array syntax; computed classes; conditional. Class management.|
|**[[V8.7 Theming]]**|CSS variables; dark mode; theme switching; user preferences. Theme system.|
|**[[V8.8 Project: Styled Dashboard]]**|Building dashboard; component library; transitions; theming; responsive. Styling project.|

### **[[V9 API Integration]]**

Master data fetching in Vue applications. Learn fetch, axios, and async patterns. API integration connects Vue frontends to backends.

|Topic|Focus & Purpose|
|---|---|
|**[[V9.1 Fetch API]]**|Native fetch; async/await; error handling; request options. Built-in fetching.|
|**[[V9.2 Axios Integration]]**|Axios setup; interceptors; instances; error handling; configuration. HTTP client.|
|**[[V9.3 Data Fetching Patterns]]**|Fetching in onMounted; loading states; error states; refetching. Component fetching.|
|**[[V9.4 Composable Data Fetching]]**|useFetch composable; reactive queries; caching; reusability. Composable pattern.|
|**[[V9.5 TanStack Query]]**|Vue Query; useQuery; useMutation; caching; invalidation; optimistic updates. Data layer.|
|**[[V9.6 Error Handling]]**|API errors; error boundaries; retry logic; user feedback; fallbacks. Robust handling.|
|**[[V9.7 Project: Data Dashboard]]**|Building dashboard; API integration; real-time updates; error handling. API project.|

### **[[V10 Testing Vue Applications]]**

Master testing strategies for Vue applications. Learn Vitest, Vue Testing Library, and component testing. Testing skills are essential for professional Vue development.

|Topic|Focus & Purpose|
|---|---|
|**[[V10.1 Testing Setup]]**|Vitest; Vue Test Utils; testing environment; configuration; scripts. Test setup.|
|**[[V10.2 Component Testing]]**|Mounting components; props; events; slots; shallow vs deep mounting. Component tests.|
|**[[V10.3 Vue Testing Library]]**|User-centric testing; queries; user events; async utilities; debugging. Testing library.|
|**[[V10.4 Testing Composables]]**|Testing custom composables; reactive testing; async composables. Composable tests.|
|**[[V10.5 Testing Pinia Stores]]**|Store testing; mocking stores; state; actions; getters. Store tests.|
|**[[V10.6 E2E Testing]]**|Cypress; Playwright; Vue-specific testing; component testing mode. End-to-end.|
|**[[V10.7 Coverage & CI]]**|Code coverage; coverage reports; CI integration; test pipelines. Test automation.|
|**[[V10.8 Project: Tested Application]]**|Complete test suite; component tests; store tests; E2E; coverage. Testing project.|

### **[[V11 TypeScript with Vue]]**

Master TypeScript for type-safe Vue development. Learn component types, composable types, and patterns. TypeScript is increasingly required for professional Vue positions.

|Topic|Focus & Purpose|
|---|---|
|**[[V11.1 TypeScript Setup]]**|Vue + TypeScript; tsconfig; Volar; type checking; configuration. TS setup.|
|**[[V11.2 Component Types]]**|DefineComponent; props typing; emits typing; slots typing; generic components. Typed components.|
|**[[V11.3 Composition API Types]]**|Ref types; computed types; reactive types; type inference. Typed Composition.|
|**[[V11.4 Props & Emits Types]]**|PropType; runtime props; complex props; typed emits. I/O typing.|
|**[[V11.5 Pinia TypeScript]]**|Typed stores; state types; getter types; action types. Typed state.|
|**[[V11.6 Router TypeScript]]**|Typed routes; route params; meta types; navigation typing. Typed routing.|
|**[[V11.7 Generics in Vue]]**|Generic components; generic composables; type parameters; reusability. Advanced types.|
|**[[V11.8 Project: Typed Application]]**|Full TypeScript app; strict mode; type coverage; best practices. TypeScript project.|

### **[[V12 Performance Optimization]]**

Master Vue performance optimization techniques. Learn rendering optimization, lazy loading, and profiling. Performance skills are critical for large-scale applications.

|Topic|Focus & Purpose|
|---|---|
|**[[V12.1 Rendering Optimization]]**|Virtual DOM; key attribute; v-once; v-memo; avoiding re-renders. Render performance.|
|**[[V12.2 Computed & Watchers]]**|Computed caching; efficient watchers; avoiding expensive operations. Reactive performance.|
|**[[V12.3 Lazy Loading]]**|Async components; defineAsyncComponent; route splitting; lazy routes. Code splitting.|
|**[[V12.4 List Rendering]]**|Large lists; virtual scrolling; vue-virtual-scroller; pagination. List performance.|
|**[[V12.5 Devtools Profiler]]**|Performance tab; flame graphs; component timing; identifying bottlenecks. Profiling.|
|**[[V12.6 Bundle Optimization]]**|Tree shaking; chunk splitting; bundle analysis; import optimization. Bundle size.|
|**[[V12.7 Project: Optimized App]]**|Performance audit; implementing fixes; measuring improvements. Optimization project.|

### **[[V13 SSR & Nuxt Introduction]]**

Master server-side rendering concepts and Nuxt introduction. Learn SSR benefits, hydration, and when to use Nuxt. SSR skills prepare for advanced Vue development.

|Topic|Focus & Purpose|
|---|---|
|**[[V13.1 SSR Concepts]]**|Server-side rendering; hydration; SSR vs SPA; benefits; trade-offs. SSR basics.|
|**[[V13.2 Nuxt Introduction]]**|What is Nuxt; Nuxt vs Vue; auto-imports; file-based routing; modules. Meta-framework.|
|**[[V13.3 Nuxt Routing]]**|pages directory; dynamic routes; layouts; middleware; navigation. Nuxt routing.|
|**[[V13.4 Data Fetching]]**|useFetch; useAsyncData; server routes; API routes; SSR data. Nuxt data.|
|**[[V13.5 SEO & Head]]**|useHead; useSeoMeta; meta tags; Open Graph; structured data. SEO.|
|**[[V13.6 Deployment]]**|Nuxt deployment; SSR hosting; static generation; edge rendering. Nuxt hosting.|
|**[[V13.7 Project: Nuxt Application]]**|Building Nuxt app; routing; data fetching; SEO; deployment. Nuxt project.|

### **[[V14 Deployment & Production]]**

Master deploying Vue applications to production. Learn build optimization, hosting, and production configuration. Deployment skills are essential for shipping applications.

|Topic|Focus & Purpose|
|---|---|
|**[[V14.1 Production Builds]]**|npm run build; build optimization; environment variables; configuration. Build process.|
|**[[V14.2 Static Hosting]]**|Netlify; Vercel; GitHub Pages; Cloudflare Pages; static deployment. Static hosting.|
|**[[V14.3 Docker]]**|Dockerfile; nginx configuration; Docker deployment; container optimization. Containerization.|
|**[[V14.4 CI/CD]]**|GitHub Actions; automated builds; testing in CI; preview deployments. Automation.|
|**[[V14.5 Environment Config]]**|Environment variables; .env files; runtime config; secrets. Configuration.|
|**[[V14.6 Monitoring]]**|Error tracking (Sentry); analytics; performance monitoring; logging. Production monitoring.|
|**[[V14.7 Project: Production Deployment]]**|Complete deployment; CI/CD; monitoring; environment config. Deployment project.|

### **[[V15 Real-World Projects]]**

Master building production-grade Vue applications. Build impressive portfolio pieces that demonstrate job-ready skills. Real projects are essential for landing Vue positions.

|Topic|Focus & Purpose|
|---|---|
|**[[V15.1 Task Manager]]**|Full CRUD; drag-and-drop; filtering; persistence; responsive design. Productivity app.|
|**[[V15.2 E-Commerce Store]]**|Product catalog; cart; checkout; filters; responsive; animations. E-commerce.|
|**[[V15.3 Social Dashboard]]**|User profiles; posts; comments; likes; real-time updates. Social features.|
|**[[V15.4 Admin Panel]]**|Data tables; forms; charts; authentication; role management. Admin interface.|
|**[[V15.5 Chat Application]]**|Real-time messaging; Socket.io; rooms; presence; notifications. Real-time app.|
|**[[V15.6 Blog Platform]]**|Markdown editor; categories; comments; SEO; responsive. Content platform.|
|**[[V15.7 Portfolio Site]]**|Project showcase; animations; about; contact; responsive design. Personal branding.|
|**[[V15.8 Production Application]]**|Complete production app; all features; testing; deployment. Portfolio centerpiece.|
