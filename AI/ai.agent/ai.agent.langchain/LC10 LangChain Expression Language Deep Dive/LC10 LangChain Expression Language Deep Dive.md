# [[LC10 LangChain Expression Language Deep Dive]]

Master LCEL as the modern standard for building LangChain applications. Learn advanced composition, custom components, type safety, and performance optimization. Understand the Runnable protocol, streaming architecture, and async patterns. Build production-grade LCEL chains with proper error handling and observability. LCEL replaces legacy chains—mastery is essential for modern LangChain development.

| Topic                                       | Focus & Purpose                                                                                                             |
| ------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| **[[LC10.1 Runnable Protocol]]**            | Runnable interface; invoke/batch/stream; InputType/OutputType; Runnable contract; protocol design. Core abstraction.        |
| **[[LC10.2 Advanced Composition]]**         | Complex pipelines; nested composition; RunnableSequence; RunnableParallel; composition patterns. Building complex chains.   |
| **[[LC10.3 Type Safety]]**                  | TypedDict; Pydantic models; input/output types; type checking; runtime validation; type inference. Type-safe chains.        |
| **[[LC10.4 RunnablePassthrough Patterns]]** | Pass-through data; data injection; side effects; data transformation; assign; context preservation. Data flow control.      |
| **[[LC10.5 RunnableLambda Advanced]]**      | Custom functions; async lambdas; error handling; logging; side effects; lambda patterns. Custom logic.                      |
| **[[LC10.6 Streaming Architecture]]**       | Event streaming; chunk streaming; streaming callbacks; astream_events; streaming patterns. Stream processing.               |
| **[[LC10.7 Configuration & Context]]**      | RunnableConfig; configurable chains; runtime context; environment; tags; metadata. Chain configuration.                     |
| **[[LC10.8 Performance Optimization]]**     | Batch optimization; parallel execution; caching; lazy evaluation; profiling; bottleneck identification. Speed improvements. |
