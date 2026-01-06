### **[[E1 Fundamentals (11ty)]] **

Master Eleventy as the simple, powerful static site generator for building blazing-fast websites. Learn zero-config setup, template languages, and core concepts. Understand why 11ty is loved by developers—no JavaScript frameworks required, works with your existing directory structure, and builds incredibly fast sites. Downloaded 15+ million times and used on 82,000+ GitHub repositories, 11ty is the modern choice for static sites. Essential for JAMstack development and modern web projects.

| Topic                             | Focus & Purpose                                                                                                                                                             |
| --------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **[[E1.1 Installation & Setup]]** | Installing 11ty (npm install @11ty/eleventy); Node.js requirements; project initialization; directory structure; first site; zero-config start. Getting started.            |
| **[[E1.2 Template Languages]]**   | Supported languages (HTML, Markdown, Nunjucks, Liquid, Handlebars, JavaScript, Pug, EJS, Haml, Mustache, WebC); choosing templates; mixing languages. Language flexibility. |
| **[[E1.3 Project Structure]]**    | Input/output directories; folder organization; includes; layouts; data folders; static files; best practices. Organizing projects.                                          |
| **[[E1.4 Configuration File]]**   | eleventy.config.js; configuration options; zero-config vs custom; ESM vs CommonJS; async configuration; returns object. Project configuration.                              |
| **[[E1.5 Command Line Usage]]**   | Build command; serve command; watch mode; incremental builds; dry run; quiet mode; CLI options. Running 11ty.                                                               |
| **[[E1.6 Front Matter]]**         | YAML front matter; data in templates; custom data; computed data; front matter formats; data priority. Template metadata.                                                   |
| **[[E1.7 Permalinks]]**           | Permalink structure; custom URLs; permalink variables; date-based permalinks; pagination permalinks; dynamic permalinks. URL control.                                       |
| **[[E1.8 Why 11ty]]**             | Speed comparison; simplicity; flexibility; no client JS; incremental adoption; framework agnostic; long-term thinking. Value proposition.                                   |

### **[[E2 Layouts & Templates]]**

Master 11ty's powerful layout and templating system. Learn layout chaining, template inheritance, partials, and includes. Understand different template engines and when to use each. Build reusable, maintainable templates. Layouts provide the foundation for consistent, DRY (Don't Repeat Yourself) site architecture.

| Topic                             | Focus & Purpose                                                                                                                   |
| --------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| **[[E2.1 Layout Basics]]**        | Creating layouts; layout directory; assigning layouts; front matter layout; layout chaining; default layouts. Template structure. |
| **[[E2.2 Template Inheritance]]** | Extending layouts; nested layouts; layout chains; content blocks; overriding sections. Layout hierarchy.                          |
| **[[E2.3 Nunjucks Templates]]**   | Nunjucks syntax; variables; filters; macros; includes; conditionals; loops; Nunjucks advantages. Popular choice.                  |
| **[[E2.4 Liquid Templates]]**     | Liquid syntax; tags; filters; objects; Jekyll compatibility; when to use Liquid. Alternative engine.                              |
| **[[E2.5 Markdown Processing]]**  | Markdown basics; Markdown-it; plugins; syntax extensions; markdown-it-anchor; code highlighting. Content format.                  |
| **[[E2.6 Includes & Partials]]**  | Include files; reusable components; relative includes; include parameters; partial organization. Modular templates.               |
| **[[E2.7 WebC Components]]**      | WebC introduction; component syntax; web components; props; slots; WebC advantages. Modern components.                            |
| **[[E2.8 JavaScript Templates]]** | .11ty.js files; template literals; JSX-like syntax; dynamic generation; JS advantages. Programmatic templates.                    |

### **[[E3 Collections & Data]]**

Master 11ty's data cascade and collection system. Learn creating collections, filtering, sorting, and pagination. Understand global data, directory data, and template data. Build dynamic site structures from data. Collections and data management enable sophisticated content organization and generation.

| Topic                             | Focus & Purpose                                                                                                                   |
| --------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| **[[E3.1 Collections Basics]]**   | Creating collections; tags; collections.all; automatic collections; custom collections; collection items. Content grouping.       |
| **[[E3.2 Collection Filtering]]** | Filter functions; advanced filtering; filtering by date; filtering by custom fields; multiple filters. Selective content.         |
| **[[E3.3 Sorting Collections]]**  | Sort methods; custom sorting; reverse sort; sort by date; sort by custom fields. Ordering content.                                |
| **[[E3.4 Data Cascade]]**         | Data priority; template data; directory data; global data; front matter data; computed data. Data hierarchy.                      |
| **[[E3.5 Global Data Files]]**    | _data directory; JSON data; JavaScript data files; fetching external data; async data; data caching. Site-wide data.              |
| **[[E3.6 Directory Data]]**       | Directory-specific data; JSON files; JavaScript files; inheriting data; overriding data. Scoped data.                             |
| **[[E3.7 Computed Data]]**        | Computed properties; dynamic values; accessing other data; eleventyComputed; use cases. Derived data.                             |
| **[[E3.8 Pagination]]**           | Pagination basics; paginated collections; pagination size; pagination aliases; generating pages from data. Multi-page generation. |

### **[[E4 Content Management]]**

Master content creation, organization, and management in 11ty. Learn blog setup, taxonomies, tags, dates, and content strategies. Build blogs, documentation sites, and content-rich applications. Proper content management enables scalable, maintainable sites with excellent content discovery.

| Topic                             | Focus & Purpose                                                                                                    |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| **[[E4.1 Blog Setup]]**           | Blog structure; post organization; post collections; post templates; blog index; archive pages. Building blogs.    |
| **[[E4.2 Tags & Taxonomies]]**    | Tag systems; multiple tags; tag pages; category systems; filtering by tags; tag clouds. Content classification.    |
| **[[E4.3 Content Dates]]**        | Date handling; content dates; created dates; published dates; date formatting; date sorting. Temporal content.     |
| **[[E4.4 Draft Posts]]**          | Draft system; conditional rendering; excluding drafts; preview drafts; draft workflow. Content staging.            |
| **[[E4.5 Featured Content]]**     | Featured flags; highlighting content; featured collections; homepage features; custom ordering. Content promotion. |
| **[[E4.6 Search Functionality]]** | Client-side search; Lunr.js; Pagefind; search indexes; search UI; search optimization. Site search.                |
| **[[E4.7 RSS Feeds]]**            | RSS plugin; feed generation; Atom feeds; JSON feeds; podcast feeds; feed templates. Content syndication.           |
| **[[E4.8 Sitemap Generation]]**   | Sitemap plugin; XML sitemap; sitemap configuration; dynamic sitemaps; robots.txt. SEO basics.                      |

### **[[E5 Plugins & Extensions]]**

Master 11ty's plugin ecosystem and create custom plugins. Learn official plugins, community plugins, and plugin development. Extend 11ty with images, syntax highlighting, navigation, and custom functionality. Plugins dramatically extend 11ty's capabilities without framework bloat.

| Topic                                | Focus & Purpose                                                                                                                      |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ |
| **[[E5.1 Plugin Basics]]**           | Installing plugins; plugin configuration; official plugins; community plugins; plugin patterns. Extending 11ty.                      |
| **[[E5.2 Image Plugin]]**            | @11ty/eleventy-plugin-image; image optimization; responsive images; image formats; lazy loading; image shortcodes. Optimized images. |
| **[[E5.3 Syntax Highlighting]]**     | Syntax highlighting plugin; PrismJS; code block styling; language support; line highlighting. Code display.                          |
| **[[E5.4 Navigation Plugin]]**       | Navigation plugin; hierarchical navigation; breadcrumbs; nav structure; active states. Site navigation.                              |
| **[[E5.5 Fetch Plugin]]**            | Fetching remote data; caching; API integration; async fetch; fetch at build time. External data.                                     |
| **[[E5.6 RSS Plugin]]**              | Generating RSS feeds; feed configuration; item templates; podcast RSS; multiple feeds. Syndication feeds.                            |
| **[[E5.7 i18n Plugin]]**             | Internationalization; multi-language sites; locale management; translated content; language switching. Multilingual sites.           |
| **[[E5.8 Creating Custom Plugins]]** | Plugin architecture; plugin functions; filters; shortcodes; transforms; collections; plugin distribution. Building plugins.          |

### **[[E6 Filters, Shortcodes & Transforms]]**

Master 11ty's data transformation and templating utilities. Learn creating filters, shortcodes, and transforms. Build reusable template logic and content processing. These tools enable powerful template functionality while keeping markup clean and maintainable.

| Topic                             | Focus & Purpose                                                                                                          |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| **[[E6.1 Filter Basics]]**        | Built-in filters; template filters; universal filters; async filters; filter patterns. Data transformation.              |
| **[[E6.2 Custom Filters]]**       | Creating filters; date filters; string filters; array filters; filter chaining; complex filters. Custom logic.           |
| **[[E6.3 Shortcode Basics]]**     | Universal shortcodes; paired shortcodes; async shortcodes; shortcode parameters; shortcode templates. Template macros.   |
| **[[E6.4 Custom Shortcodes]]**    | Building shortcodes; image shortcodes; embed shortcodes; component shortcodes; shortcode libraries. Reusable components. |
| **[[E6.5 Transforms]]**           | Output transforms; HTML transforms; minification; post-processing; transform timing. Build-time processing.              |
| **[[E6.6 Linters & Validators]]** | HTML validation; link checking; accessibility checking; custom validators. Quality assurance.                            |
| **[[E6.7 Data Filters]]**         | Filtering collections; date filters; sorting filters; grouping filters; custom logic. Data manipulation.                 |
| **[[E6.8 Template Helpers]]**     | Helper functions; utility functions; computed helpers; date helpers; string helpers. Template utilities.                 |

### **[[E7 Performance Optimization]]**

Master optimizing 11ty sites for maximum performance. Learn build optimization, asset optimization, caching strategies, and performance monitoring. Build sites that score perfect Lighthouse scores. Performance is 11ty's superpower—learn to leverage it fully.

| Topic                                | Focus & Purpose                                                                                                    |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------------ |
| **[[E7.1 Build Performance]]**       | Fast builds; incremental builds; watch mode optimization; build profiling; bottleneck identification. Build speed. |
| **[[E7.2 Asset Optimization]]**      | Image optimization; CSS minification; JS minification; font optimization; asset pipeline. Asset performance.       |
| **[[E7.3 Caching Strategies]]**      | Data caching; fetch caching; incremental builds; cache invalidation; build caching. Smart caching.                 |
| **[[E7.4 Critical CSS]]**            | Inline critical CSS; above-the-fold CSS; CSS splitting; critical extraction. First paint optimization.             |
| **[[E7.5 Lazy Loading]]**            | Image lazy loading; iframe lazy loading; loading attribute; intersection observer. Deferred loading.               |
| **[[E7.6 Output Optimization]]**     | HTML minification; removing whitespace; optimizing output; compression. Clean output.                              |
| **[[E7.7 Performance Monitoring]]**  | Lighthouse scores; SpeedCurve; WebPageTest; performance budgets; monitoring. Tracking performance.                 |
| **[[E7.8 Progressive Enhancement]]** | No-JS baseline; JavaScript enhancement; graceful degradation; accessibility-first. Resilient sites.                |

### **[[E8 Headless CMS Integration]]**

Master integrating headless CMS platforms with 11ty. Learn API-driven content, GraphQL, REST APIs, and webhook deployments. Build sites that combine 11ty's speed with powerful content management. Headless CMS integration enables non-technical content editors while maintaining static site benefits.

| Topic                            | Focus & Purpose                                                                                             |
| -------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| **[[E8.1 Headless CMS Basics]]** | Git-based vs API-driven; CMS options; choosing a CMS; CMS comparison. Content management.                   |
| **[[E8.2 Git-Based CMSes]]**     | Netlify CMS; Forestry; Decap CMS; TinaCMS; git workflow; markdown editing. File-based CMS.                  |
| **[[E8.3 API-Driven CMSes]]**    | Contentful; Sanity; DatoCMS; Strapi; Prismic; API integration. Cloud CMS.                                   |
| **[[E8.4 Fetching CMS Data]]**   | Data files; async fetch; GraphQL queries; REST requests; authentication. Getting content.                   |
| **[[E8.5 GraphQL Integration]]** | GraphQL basics; queries; fragments; pagination; GraphQL clients. Querying APIs.                             |
| **[[E8.6 Content Modeling]]**    | Content types; field types; relationships; references; structured content. Data modeling.                   |
| **[[E8.7 Webhook Deployments]]** | Deploy hooks; automatic builds; webhook setup; build triggers; CI/CD. Automated publishing.                 |
| **[[E8.8 Live Preview]]**        | Preview environments; draft content; preview modes; serverless preview. Content preview.                    |

### **[[E9 Styling & Frontend Integration]]**

Master integrating CSS frameworks, build tools, and frontend technologies with 11ty. Learn Sass, PostCSS, Tailwind, Alpine.js, and modern frontend workflows. Build complete frontend applications. 11ty works seamlessly with modern frontend tooling.

| Topic                              | Focus & Purpose                                                                                              |
| ---------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| **[[E9.1 CSS Integration]]**       | CSS processing; CSS imports; postcss; autoprefixer; CSS organization. Styling setup.                         |
| **[[E9.2 Sass-SCSS]]**             | Sass integration; Sass plugins; Sass compilation; Sass organization; Sass best practices. CSS preprocessing. |
| **[[E9.3 PostCSS]]**               | PostCSS plugins; cssnano; autoprefixer; PostCSS config; modern CSS. CSS transformation.                      |
| **[[E9.4 Tailwind CSS]]**          | Tailwind integration; JIT mode; PurgeCSS; Tailwind config; utility classes. Utility-first CSS.               |
| **[[E9.5 JavaScript Bundling]]**   | Webpack; Rollup; esbuild; JS bundling; module bundling; code splitting. JS processing.                       |
| **[[E9.6 Alpine.js Integration]]** | Alpine basics; reactive components; interactive elements; progressive enhancement. Lightweight JS.           |
| **[[E9.7 Vite Plugin]]**           | 11ty + Vite; HMR; fast dev server; Vite config; modern tooling. Development experience.                      |
| **[[E9.8 Design Systems]]**        | Component libraries; pattern libraries; style guides; design tokens. Systematic design.                      |

### **[[E10 Deployment & Hosting]]**

Master deploying 11ty sites to production. Learn Netlify, Vercel, Cloudflare Pages, GitHub Pages, and other hosting platforms. Understand CI/CD, custom domains, and production configurations. Deployment is where your site goes live—master modern deployment workflows.

| Topic                            | Focus & Purpose                                                                                    |
| -------------------------------- | -------------------------------------------------------------------------------------------------- |
| **[[E10.1 Deployment Basics]]**  | Build output; static hosting; deployment workflow; environment variables. Going live.              |
| **[[E10.2 Netlify Deployment]]** | Netlify setup; netlify.toml; build settings; deploy contexts; branch deploys. Netlify platform.    |
| **[[E10.3 Vercel Deployment]]**  | Vercel setup; vercel.json; build configuration; preview deployments. Vercel platform.              |
| **[[E10.4 Cloudflare Pages]]**   | Cloudflare setup; pages configuration; edge functions; CF analytics. Cloudflare platform.          |
| **[[E10.5 GitHub Pages]]**       | GitHub Actions; gh-pages deployment; custom domain; deployment workflow. GitHub hosting.           |
| **[[E10.6 Custom Domains]]**     | DNS configuration; SSL certificates; domain verification; domain routing. Domain setup.            |
| **[[E10.7 CI-CD Pipelines]]**    | Automated deployment; GitHub Actions; GitLab CI; testing in CI; deployment automation. Automation. |
| **[[E10.8 Edge Functions]]**     | Serverless functions; dynamic routes; API routes; edge computing. Dynamic capabilities.            |

### **[[E11 Advanced Patterns]]**

Master advanced 11ty techniques and patterns. Learn edge cases, complex configurations, and sophisticated architectures. Build large-scale sites, multi-language sites, and complex applications. Advanced patterns enable building anything with 11ty.

| Topic                              | Focus & Purpose                                                                                         |
| ---------------------------------- | ------------------------------------------------------------------------------------------------------- |
| **[[E11.1 Multi-Language Sites]]** | i18n strategies; locale routing; translated content; language switching; hreflang. International sites. |
| **[[E11.2 Large-Scale Sites]]**    | Scaling strategies; build optimization; content organization; architectural patterns. Enterprise sites. |
| **[[E11.3 Incremental Adoption]]** | Migrating to 11ty; partial conversion; hybrid approaches; gradual migration. Transitioning.             |
| **[[E11.4 Custom Engines]]**       | Template engine plugins; custom parsing; extending engines; engine configuration. Engine customization. |
| **[[E11.5 Serverless 11ty]]**      | On-demand builders; serverless rendering; preview modes; dynamic content. Hybrid static/dynamic.        |
| **[[E11.6 Build Events]]**         | Before/after events; event listeners; build hooks; custom processing. Build lifecycle.                  |
| **[[E11.7 Testing]]**              | Testing static output; accessibility testing; link checking; visual regression. Quality assurance.      |
| **[[E11.8 Documentation Sites]]**  | Docs structure; search; versioning; navigation; best practices. Technical documentation.                |

### **[[E12 Real-World Projects]]**

Master building production 11ty sites across use cases. Learn portfolio sites, blogs, documentation, e-commerce, and complex applications. Build complete, deployed projects. Real projects solidify understanding and provide portfolio pieces.

| Topic                                | Focus & Purpose                                                                                   |
| ------------------------------------ | ------------------------------------------------------------------------------------------------- |
| **[[E12.1 Portfolio Website]]**      | Portfolio structure; project pages; about page; contact form; resume page. Personal branding.     |
| **[[E12.2 Blog Platform]]**          | Blog architecture; post system; categories; tags; RSS; comments integration. Content publishing.  |
| **[[E12.3 Documentation Site]]**     | Docs organization; search; versions; sidebar navigation; code examples. Technical docs.           |
| **[[E12.4 Marketing Site]]**         | Landing pages; lead capture; analytics; forms; CTA optimization. Business site.                   |
| **[[E12.5 E-commerce Integration]]** | Product catalog; Shopify integration; Snipcart; payment integration; shopping cart. Online store. |
| **[[E12.6 Podcast Site]]**           | Episode pages; audio players; RSS podcast feed; iTunes integration; show notes. Podcast platform. |
| **[[E12.7 Community Site]]**         | Event pages; member directory; resources; forum integration. Community platform.                  |
| **[[E12.8 JAMstack Application]]**   | API integration; authentication; dynamic features; serverless functions. Full applications.       |

---
