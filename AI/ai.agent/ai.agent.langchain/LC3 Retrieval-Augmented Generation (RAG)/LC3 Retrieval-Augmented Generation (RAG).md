# [[LC3 Retrieval-Augmented Generation (RAG)]]

Master RAG as the essential pattern for building knowledge-grounded LLM applications. Learn document loading, text splitting, embeddings, vector stores, and retrieval strategies. Understand semantic search, hybrid search, and re-ranking. RAG enables LLMs to access external knowledge—critical for accurate, up-to-date, and verifiable AI applications. This is the most important real-world pattern.

| Topic                            | Focus & Purpose                                                                                                                                               |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **[[LC3.1 Document Loaders]]**   | Loading PDFs, CSVs, HTML, APIs; TextLoader, PyPDFLoader, UnstructuredLoader; web scraping; data ingestion; source connectors. Data acquisition.               |
| **[[LC3.2 Text Splitting]]**     | RecursiveCharacterTextSplitter; chunk size/overlap; semantic splitting; context preservation; splitting strategies; optimal chunking. Document preprocessing. |
| **[[LC3.3 Embeddings]]**         | Embedding models; OpenAIEmbeddings, HuggingFaceEmbeddings; vector representations; embedding dimensions; cost-performance trade-offs. Vector encoding.        |
| **[[LC3.4 Vector Stores]]**      | Chroma, Pinecone, FAISS, Weaviate; similarity search; CRUD operations; metadata filtering; vector store selection; indexing. Knowledge storage.               |
| **[[LC3.5 Retrievers]]**         | VectorStoreRetriever; similarity search; MMR (Maximum Marginal Relevance); search kwargs; retrieval strategies; custom retrievers. Document retrieval.        |
| **[[LC3.6 RAG Chains]]**         | RetrievalQA; ConversationalRetrievalChain; RAG with LCEL; context injection; source citation; RAG patterns. Knowledge-grounded generation.                    |
| **[[LC3.7 Advanced Retrieval]]** | Hybrid search; re-ranking; parent document retrieval; self-query; compression; contextual compression. Enhanced retrieval.                                    |
| **[[LC3.8 RAG Evaluation]]**     | Retrieval metrics; faithfulness; answer relevance; context precision; RAGAs framework; evaluation datasets. Quality measurement.                              |
