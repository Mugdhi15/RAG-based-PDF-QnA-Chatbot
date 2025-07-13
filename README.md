# RAG-based-PDF-QnA-Chatbot
This project is a Retrieval-Augmented Generation (RAG) based chatbot that answers user queries by reading and understanding PDF documents. It uses LangChain, FAISS, and a local LLM via Ollama (gemma2:2b)

Tested on the iPhone User Manual, the system can be easily extended to any domain-specific documents like legal contracts, product guides, or research papers.

# Core Components
# 1. Document Ingestion & Chunking
- Loader: The PyPDFLoader from LangChain reads the PDF file.
- Text Splitter: RecursiveCharacterTextSplitter splits the extracted text into overlapping chunks for better context handling by the model.

# 2. Embedding & Vector Store
- Embedding Model: OllamaEmbeddings uses the locally served LLM (gemma2:2b) to embed text chunks.
- Vector Store: FAISS stores these embeddings and supports fast similarity-based retrieval during querying.

# 3. Language Model
The system uses Ollama’s local gemma2:2b model as the primary LLM for answer generation and embeddings. This allows privacy-preserving, offline-friendly inference without relying on cloud APIs.

# 4. RetrievalQA Chain
Combines the retriever with the LLM in a RetrievalQA chain to generate answers using relevant document chunks as context.

# 5. Tool Integration and Agent
Tools are created using LangChain's Tool abstraction for:
- PDF Q&A
- Direct document lookup
A ZERO_SHOT_REACT_DESCRIPTION AgentType is used to select appropriate tools and answer queries based on user input.

# 6. Validation Checks
The pipeline includes unit tests for LLM availability, embedding model setup, retrieval performance, and QA chain consistency to ensure modular robustness.
