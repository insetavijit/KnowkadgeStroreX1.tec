### **[[01 Vue.js Fundamentals & Setup]]**

Master Vue.js as the progressive JavaScript framework loved by developers worldwide. Learn why Vue powers applications at Alibaba, Xiaomi, GitLab, and BMW. Understand Vue's approachable syntax, reactivity system, and incremental adoption that makes it perfect for both beginners and large-scale applications. Vue.js developers earn $90k-$135k annually with growing demand. Essential for frontend development and a top choice for enterprise applications.

| Topic                              | Focus & Purpose                                                                                                                                 |
| ---------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| **[[1.1 Vue.js Introduction]]**    | What is Vue; progressive framework philosophy; Vue 2 vs Vue 3; Options vs Composition API; ecosystem overview; market demand. Industry context. |
| **[[1.2 Environment Setup]]**      | Node.js setup; create-vue; Vite; VS Code Volar extension; Vue DevTools; project templates. Professional setup.                                  |
| **[[1.3 Project Structure]]**      | Vite Vue project; src directory; components folder; assets; main.js; App.vue. File organization.                                                |
| **[[1.4 Vue Components]]**         | Single File Components (.vue); template; script; style; component basics. Building blocks.                                                      |
| **[[1.5 Template Syntax]]**        | Interpolation; directives; v-bind; v-on; expressions; dynamic attributes. Template fundamentals.                                                |
| **[[1.6 Development Tools]]**      | Vue DevTools; component inspection; state debugging; timeline; performance. Debugging tools.                                                    |
| **[[1.7 Project: Hello Vue App]]** | Building first Vue app; components; styling; data binding; development workflow. First project.                                                 |

### **[[02 Reactivity & Data Binding]]**

Master Vue's reactivity system for dynamic applications. Learn reactive data, computed properties, and watchers. Reactivity is the core concept that makes Vue powerful and is tested in every interview.

|Topic|Focus & Purpose|
|---|---|
|**[[2.1 Reactive Data]]**|ref(); reactive(); data binding; reactivity basics; reactive primitives vs objects. Core reactivity.|
|**[[2.2 Template Binding]]**|Text interpolation; v-bind; attribute binding; class binding; style binding. Data display.|
|**[[2.3 Computed Properties]]**|computed(); derived state; caching; getters and setters; vs methods. Derived data.|
|**[[2.4 Watchers]]**|watch(); watchEffect(); immediate; deep watching; cleanup; side effects. Reactive effects.|
|**[[2.5 Event Handling]]**|v-on directive; @shorthand; event modifiers; inline handlers; method handlers. User interactions.|
|**[[2.6 Two-Way Binding]]**|v-model; form inputs; modifiers (.lazy, .number, .trim); custom v-model. Input binding.|
|**[[2.7 Reactivity in Depth]]**|Reactivity internals; Proxy; ref vs reactive; toRefs; unref; reactivity utils. Advanced reactivity.|
|**[[2.8 Project: Interactive Form]]**|Building reactive form; validation; computed; watchers; v-model; submission. Reactivity project.|

### **[[03 Components Deep Dive]]**

Master Vue component architecture for scalable applications. Learn props, events, slots, and component patterns. Component mastery is essential for all Vue development and code organization.

|Topic|Focus & Purpose|
|---|---|
|**[[3.1 Component Registration]]**|Local vs global registration; component naming; PascalCase; async components. Component setup.|
|**[[3.2 Props]]**|Defining props; prop types; required; default values; prop validation; readonly. Component inputs.|
|**[[3.3 Events]]**|$emit; defineEmits; event arguments; event naming; v-model on components. Component outputs.|
|**[[3.4 Slots]]**|Default slots; named slots; scoped slots; slot props; dynamic slots. Content distribution.|
|**[[3.5 Provide/Inject]]**|provide(); inject(); dependency injection; reactive provide; symbol keys. Deep data passing.|
|**[[3.6 Component Lifecycle]]**|Lifecycle hooks; onMounted; onUnmounted; onUpdated; setup timing. Component lifecycle.|
|**[[3.7 Dynamic Components]]**|<component :is>; keep-alive; component caching; transition between components. Dynamic rendering.|
|**[[3.8 Project: Component Library]]**|Building reusable components; props; events; slots; documentation. Component project.|

### **[[04 Composition API]]**

Master Vue 3 Composition API for modern Vue development. Learn composables, script setup, and code organization. Composition API is the standard for new Vue 3 projects and required for professional Vue development.

| Topic                                   | Focus & Purpose                                                                                   |
| --------------------------------------- | ------------------------------------------------------------------------------------------------- |
| **[[4.1 Composition API Basics]]**      | setup() function; reactive state; lifecycle in setup; returning values. API fundamentals.         |
| **[[4.2 Script Setup]]**                | script setup ; compiler macro; defineProps; defineEmits; defineExpose. Modern syntax.             |
| **[[4.3 Composables]]**                 | Creating composables; reusable logic; conventions; composition; sharing state. Code reuse.        |
| **[[4.4 Refs & Reactive]]**             | ref(); reactive(); toRef; toRefs; isRef; unref; shallowRef. Reactivity utilities.                 |
| **[[4.5 Computed & Watch]]**            | computed(); watch(); watchEffect(); watchPostEffect; cleanup. Derived state.                      |
| **[[4.6 Template Refs]]**               | Template refs; ref attribute; component refs; accessing DOM; focus management. DOM access.        |
| **[[4.7 Lifecycle Hooks]]**             | onMounted; onUnmounted; onBeforeMount; onUpdated; hook timing. Lifecycle in Composition.          |
| **[[4.8 Project: Composable Library]]** | Building composables; useFetch; useLocalStorage; useDebounce; documentation. Composables project. |

### **[[05 Routing with Vue Router]]**

Master Vue Router for single-page application navigation. Learn dynamic routes, navigation guards, and nested routes. Routing is essential for all multi-page Vue applications.

|Topic|Focus & Purpose|
|---|---|
|**[[5.1 Router Setup]]**|Vue Router installation; createRouter; history modes; router configuration. Router basics.|
|**[[5.2 Routes & Navigation]]**|Route definitions; RouterLink; RouterView; programmatic navigation; route naming. Basic routing.|
|**[[5.3 Dynamic Routes]]**|Route parameters; useRoute; params; props mode; optional parameters. Dynamic segments.|
|**[[5.4 Nested Routes]]**|Children routes; nested RouterView; layout routes; route nesting patterns. Nested navigation.|
|**[[5.5 Navigation Guards]]**|beforeEach; beforeEnter; beforeRouteEnter; async guards; navigation flow. Route protection.|
|**[[5.6 Route Meta]]**|Meta fields; authentication flags; breadcrumbs; SEO data; middleware patterns. Route metadata.|
|**[[5.7 Lazy Loading]]**|Dynamic imports; route-level code splitting; loading states; prefetching. Performance.|
|**[[5.8 Project: Multi-Page App]]**|Building SPA; routing; guards; nested routes; navigation; loading. Router project.|

### **[[06 State Management with Pinia]]**

Master Pinia as the official Vue state management library. Learn stores, actions, getters, and state patterns. State management is critical for complex Vue applications.

|Topic|Focus & Purpose|
|---|---|
|**[[6.1 Pinia Introduction]]**|What is Pinia; Pinia vs Vuex; store concept; installation; devtools. State management.|
|**[[6.2 Defining Stores]]**|defineStore; state; getters; actions; setup stores; options stores. Store creation.|
|**[[6.3 Using Stores]]**|Store instances; accessing state; calling actions; storeToRefs; reactivity. Store usage.|
|**[[6.4 Getters]]**|Computed state; getter arguments; using other getters; caching behavior. Derived state.|
|**[[6.5 Actions]]**|Async actions; error handling; calling other actions; action composition. State mutations.|
|**[[6.6 Store Composition]]**|Multiple stores; store dependencies; modular state; cross-store access. Store organization.|
|**[[6.7 Plugins & Persistence]]**|Pinia plugins; persisted state; hydration; storage integration. Extending Pinia.|
|**[[6.8 Project: E-Commerce Cart]]**|Building cart store; products; cart; checkout; persistence. State project.|

### **[[07 Forms & Validation]]**

Master form handling in Vue applications. Learn form binding, validation libraries, and complex form patterns. Form skills are essential for data-driven applications.

|Topic|Focus & Purpose|
|---|---|
|**[[7.1 Form Basics]]**|v-model; form elements; input types; textarea; select; form submission. Form fundamentals.|
|**[[7.2 Input Modifiers]]**|.lazy; .number; .trim; custom modifiers; modifier combinations. Input processing.|
|**[[7.3 Form Validation]]**|Manual validation; VeeValidate; Vuelidate; Zod; schema validation. Data validation.|
|**[[7.4 VeeValidate]]**|VeeValidate setup; Field; Form; validation rules; error messages; Yup integration. Validation library.|
|**[[7.5 Complex Forms]]**|Multi-step forms; dynamic fields; field arrays; conditional fields. Advanced forms.|
|**[[7.6 File Uploads]]**|File input; image preview; upload handling; progress; cloud upload. File handling.|
|**[[7.7 Form Accessibility]]**|Labels; ARIA; error announcements; keyboard navigation; accessible forms. A11y forms.|
|**[[7.8 Project: Registration Form]]**|Complete form; validation; multi-step; file upload; submission. Form project.|

### **[[08 Styling & UI]]**

Master styling approaches for Vue applications. Learn scoped styles, CSS frameworks, and component libraries. Styling skills are essential for building polished user interfaces.

|Topic|Focus & Purpose|
|---|---|
|**[[8.1 Scoped Styles]]**|<style scoped>; style isolation; deep selectors; :deep(); :slotted(). Component styles.|
|**[[8.2 CSS Modules]]**|CSS Modules in Vue; :class binding; module naming; usage patterns. Module styling.|
|**[[8.3 Tailwind CSS]]**|Tailwind + Vue; configuration; utility classes; responsive design. Utility-first.|
|**[[8.4 Component Libraries]]**|Vuetify; Naive UI; PrimeVue; Element Plus; Quasar; library comparison. Pre-built UI.|
|**[[8.5 Transitions]]**|<Transition>; <TransitionGroup>; CSS transitions; JavaScript hooks; animation. Motion design.|
|**[[8.6 Dynamic Classes]]**|Class binding; object syntax; array syntax; computed classes; conditional. Class management.|
|**[[8.7 Theming]]**|CSS variables; dark mode; theme switching; user preferences. Theme system.|
|**[[8.8 Project: Styled Dashboard]]**|Building dashboard; component library; transitions; theming; responsive. Styling project.|

### **[[09 API Integration]]**

Master data fetching in Vue applications. Learn fetch, axios, and async patterns. API integration connects Vue frontends to backends.

|Topic|Focus & Purpose|
|---|---|
|**[[9.1 Fetch API]]**|Native fetch; async/await; error handling; request options. Built-in fetching.|
|**[[9.2 Axios Integration]]**|Axios setup; interceptors; instances; error handling; configuration. HTTP client.|
|**[[9.3 Data Fetching Patterns]]**|Fetching in onMounted; loading states; error states; refetching. Component fetching.|
|**[[9.4 Composable Data Fetching]]**|useFetch composable; reactive queries; caching; reusability. Composable pattern.|
|**[[9.5 TanStack Query]]**|Vue Query; useQuery; useMutation; caching; invalidation; optimistic updates. Data layer.|
|**[[9.6 Error Handling]]**|API errors; error boundaries; retry logic; user feedback; fallbacks. Robust handling.|
|**[[9.7 Project: Data Dashboard]]**|Building dashboard; API integration; real-time updates; error handling. API project.|

### **[[10 Testing Vue Applications]]**

Master testing strategies for Vue applications. Learn Vitest, Vue Testing Library, and component testing. Testing skills are essential for professional Vue development.

|Topic|Focus & Purpose|
|---|---|
|**[[10.1 Testing Setup]]**|Vitest; Vue Test Utils; testing environment; configuration; scripts. Test setup.|
|**[[10.2 Component Testing]]**|Mounting components; props; events; slots; shallow vs deep mounting. Component tests.|
|**[[10.3 Vue Testing Library]]**|User-centric testing; queries; user events; async utilities; debugging. Testing library.|
|**[[10.4 Testing Composables]]**|Testing custom composables; reactive testing; async composables. Composable tests.|
|**[[10.5 Testing Pinia Stores]]**|Store testing; mocking stores; state; actions; getters. Store tests.|
|**[[10.6 E2E Testing]]**|Cypress; Playwright; Vue-specific testing; component testing mode. End-to-end.|
|**[[10.7 Coverage & CI]]**|Code coverage; coverage reports; CI integration; test pipelines. Test automation.|
|**[[10.8 Project: Tested Application]]**|Complete test suite; component tests; store tests; E2E; coverage. Testing project.|

### **[[11 TypeScript with Vue]]**

Master TypeScript for type-safe Vue development. Learn component types, composable types, and patterns. TypeScript is increasingly required for professional Vue positions.

|Topic|Focus & Purpose|
|---|---|
|**[[11.1 TypeScript Setup]]**|Vue + TypeScript; tsconfig; Volar; type checking; configuration. TS setup.|
|**[[11.2 Component Types]]**|DefineComponent; props typing; emits typing; slots typing; generic components. Typed components.|
|**[[11.3 Composition API Types]]**|Ref types; computed types; reactive types; type inference. Typed Composition.|
|**[[11.4 Props & Emits Types]]**|PropType; runtime props; complex props; typed emits. I/O typing.|
|**[[11.5 Pinia TypeScript]]**|Typed stores; state types; getter types; action types. Typed state.|
|**[[11.6 Router TypeScript]]**|Typed routes; route params; meta types; navigation typing. Typed routing.|
|**[[11.7 Generics in Vue]]**|Generic components; generic composables; type parameters; reusability. Advanced types.|
|**[[11.8 Project: Typed Application]]**|Full TypeScript app; strict mode; type coverage; best practices. TypeScript project.|

### **[[12 Performance Optimization]]**

Master Vue performance optimization techniques. Learn rendering optimization, lazy loading, and profiling. Performance skills are critical for large-scale applications.

|Topic|Focus & Purpose|
|---|---|
|**[[12.1 Rendering Optimization]]**|Virtual DOM; key attribute; v-once; v-memo; avoiding re-renders. Render performance.|
|**[[12.2 Computed & Watchers]]**|Computed caching; efficient watchers; avoiding expensive operations. Reactive performance.|
|**[[12.3 Lazy Loading]]**|Async components; defineAsyncComponent; route splitting; lazy routes. Code splitting.|
|**[[12.4 List Rendering]]**|Large lists; virtual scrolling; vue-virtual-scroller; pagination. List performance.|
|**[[12.5 Devtools Profiler]]**|Performance tab; flame graphs; component timing; identifying bottlenecks. Profiling.|
|**[[12.6 Bundle Optimization]]**|Tree shaking; chunk splitting; bundle analysis; import optimization. Bundle size.|
|**[[12.7 Project: Optimized App]]**|Performance audit; implementing fixes; measuring improvements. Optimization project.|

### **[[13 SSR & Nuxt Introduction]]**

Master server-side rendering concepts and Nuxt introduction. Learn SSR benefits, hydration, and when to use Nuxt. SSR skills prepare for advanced Vue development.

|Topic|Focus & Purpose|
|---|---|
|**[[13.1 SSR Concepts]]**|Server-side rendering; hydration; SSR vs SPA; benefits; trade-offs. SSR basics.|
|**[[13.2 Nuxt Introduction]]**|What is Nuxt; Nuxt vs Vue; auto-imports; file-based routing; modules. Meta-framework.|
|**[[13.3 Nuxt Routing]]**|pages directory; dynamic routes; layouts; middleware; navigation. Nuxt routing.|
|**[[13.4 Data Fetching]]**|useFetch; useAsyncData; server routes; API routes; SSR data. Nuxt data.|
|**[[13.5 SEO & Head]]**|useHead; useSeoMeta; meta tags; Open Graph; structured data. SEO.|
|**[[13.6 Deployment]]**|Nuxt deployment; SSR hosting; static generation; edge rendering. Nuxt hosting.|
|**[[13.7 Project: Nuxt Application]]**|Building Nuxt app; routing; data fetching; SEO; deployment. Nuxt project.|

### **[[14 Deployment & Production]]**

Master deploying Vue applications to production. Learn build optimization, hosting, and production configuration. Deployment skills are essential for shipping applications.

|Topic|Focus & Purpose|
|---|---|
|**[[14.1 Production Builds]]**|npm run build; build optimization; environment variables; configuration. Build process.|
|**[[14.2 Static Hosting]]**|Netlify; Vercel; GitHub Pages; Cloudflare Pages; static deployment. Static hosting.|
|**[[14.3 Docker]]**|Dockerfile; nginx configuration; Docker deployment; container optimization. Containerization.|
|**[[14.4 CI/CD]]**|GitHub Actions; automated builds; testing in CI; preview deployments. Automation.|
|**[[14.5 Environment Config]]**|Environment variables; .env files; runtime config; secrets. Configuration.|
|**[[14.6 Monitoring]]**|Error tracking (Sentry); analytics; performance monitoring; logging. Production monitoring.|
|**[[14.7 Project: Production Deployment]]**|Complete deployment; CI/CD; monitoring; environment config. Deployment project.|

### **[[15 Real-World Projects]]**

Master building production-grade Vue applications. Build impressive portfolio pieces that demonstrate job-ready skills. Real projects are essential for landing Vue positions.

|Topic|Focus & Purpose|
|---|---|
|**[[15.1 Task Manager]]**|Full CRUD; drag-and-drop; filtering; persistence; responsive design. Productivity app.|
|**[[15.2 E-Commerce Store]]**|Product catalog; cart; checkout; filters; responsive; animations. E-commerce.|
|**[[15.3 Social Dashboard]]**|User profiles; posts; comments; likes; real-time updates. Social features.|
|**[[15.4 Admin Panel]]**|Data tables; forms; charts; authentication; role management. Admin interface.|
|**[[15.5 Chat Application]]**|Real-time messaging; Socket.io; rooms; presence; notifications. Real-time app.|
|**[[15.6 Blog Platform]]**|Markdown editor; categories; comments; SEO; responsive. Content platform.|
|**[[15.7 Portfolio Site]]**|Project showcase; animations; about; contact; responsive design. Personal branding.|
|**[[15.8 Production Application]]**|Complete production app; all features; testing; deployment. Portfolio centerpiece.|
