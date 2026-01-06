# N4 Data Fetching & Caching

Master Next.js data fetching with the new fetch API, caching strategies, and revalidation. Learn incremental static regeneration (ISR), on-demand revalidation, and data mutation patterns. Proper data fetching is crucial for performance and user experience in production apps.

|Topic|Focus & Purpose|
|---|---|
|**[[N4.1 Fetch API & Caching]]**|Extended fetch API; cache options (force-cache, no-store); request deduplication; caching strategies. Data fetching.|
|**[[N4.2 Revalidation Strategies]]**|Time-based revalidation; on-demand revalidation; revalidatePath; revalidateTag; cache invalidation. Cache management.|
|**[[N4.3 Incremental Static Regeneration]]**|ISR fundamentals; revalidate option; stale-while-revalidate; background regeneration; use cases. Dynamic static content.|
|**[[N4.4 Server Actions]]**|Server Actions basics; 'use server' directive; form actions; data mutations; progressive enhancement. Modern forms.|
|**[[N4.5 Data Mutation Patterns]]**|POST requests; Server Actions; optimistic updates; error handling; form validation. Writing data.|
|**[[N4.6 Parallel Data Fetching]]**|Multiple fetch requests; Promise.all; parallel loading; waterfall prevention; performance optimization. Efficient loading.|
|**[[N4.7 Request Memoization]]**|React cache(); automatic deduplication; request memoization patterns; performance benefits. Request optimization.|
|**[[N4.8 Project: News Aggregator]]**|Building news site; ISR; multiple data sources; caching strategies; revalidation; real-time updates. Data-intensive app.|
