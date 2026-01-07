# [[LC5 Memory Systems]]

Build stateful applications with sophisticated memory management. Learn conversation memory, entity memory, knowledge graphs, and long-term storage. Understand memory types, retrieval strategies, and context window management. Memory enables personalization, context awareness, and multi-turn interactions—essential for production chatbots and assistants. Proper memory design prevents context loss and improves user experience.

| Topic                                   | Focus & Purpose                                                                                                                                                 |
| --------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **[[LC5.1 Conversation Memory Types]]** | ConversationBufferMemory; ConversationBufferWindowMemory; ConversationSummaryMemory; ConversationSummaryBufferMemory; selecting memory type. Memory strategies. |
| **[[LC5.2 Entity Memory]]**             | ConversationEntityMemory; entity extraction; entity tracking; relationship memory; knowledge accumulation. Tracking entities.                                   |
| **[[LC5.3 Vector Store Memory]]**       | VectorStoreRetrieverMemory; semantic memory; embedding-based retrieval; long-term memory; memory search. Searchable memory.                                     |
| **[[LC5.4 Knowledge Graphs]]**          | ConversationKGMemory; knowledge graph construction; entity-relationship extraction; graph-based memory; knowledge representation. Structured knowledge.         |
| **[[LC5.5 Chat Message History]]**      | Chat message stores; persistent storage; database backends; Redis, PostgreSQL; message retrieval; history management. Durable conversations.                    |
| **[[LC5.6 Memory in Chains & Agents]]** | Adding memory to chains; memory in agents; memory keys; context injection; memory persistence; conversation continuity. Stateful applications.                  |
| **[[LC5.7 Custom Memory]]**             | Custom memory classes; memory interface; save_context; load_memory_variables; memory backends; specialized memory. Advanced memory.                             |
| **[[LC5.8 Context Window Management]]** | Token counting; message trimming; summarization; context compression; cost optimization; preventing context overflow. Managing context limits.                  |
