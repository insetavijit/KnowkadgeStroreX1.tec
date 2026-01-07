# [[LC2 Advanced Chains & LCEL]]

Master sophisticated chain patterns using LCEL for complex workflows. Learn parallel chains, routing, fallbacks, and retry logic. Understand RunnablePassthrough, RunnableLambda, and custom runnables. Build production-grade chains with proper error handling and composition. LCEL is the modern standard—legacy chain syntax is deprecated. This section enables building maintainable, scalable applications.

| Topic                                    | Focus & Purpose                                                                                                                                  |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| **[[LC2.1 Parallel Chains]]**            | RunnableParallel; parallel execution; result merging; fan-out patterns; concurrent processing; performance optimization. Concurrent workflows.   |
| **[[LC2.2 Routing & Branching]]**        | RunnableBranch; conditional routing; dynamic chain selection; route conditions; multi-path workflows; decision logic. Conditional execution.     |
| **[[LC2.3 Fallbacks & Retries]]**        | RunnableWithFallbacks; retry logic; error recovery; fallback chains; timeout handling; graceful degradation. Robust chains.                      |
| **[[LC2.4 Custom Runnables]]**           | Creating custom Runnables; Runnable interface; invoke/batch/stream methods; type annotations; composition; reusable components. Building blocks. |
| **[[LC2.5 Chain Composition Patterns]]** | Nested chains; modular design; chain reuse; interface design; input/output mapping; composition strategies. Maintainable chains.                 |
| **[[LC2.6 Streaming & Async]]**          | Stream method; async chains; astream; token streaming; event streaming; async generators; real-time output. Async operations.                    |
| **[[LC2.7 Batch Processing]]**           | Batch method; concurrent batching; batch optimization; throughput; parallel requests; batch error handling. Efficient processing.                |
| **[[LC2.8 Configuration & Runtime]]**    | Configurable chains; runtime configuration; RunnableConfig; environment variables; dynamic configuration; chain customization. Flexible chains.  |
