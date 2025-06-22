README: LlamaIndex Legal Document Q&A System
Overview
This script (llamaindex_legal_qa.py) implements a Legal Document Q&A System using LlamaIndex with the Grok API (Llama-3.3-70B-Versatile model). It enables a legal firm to query documents (e.g., "What are key points of 2023 tax law case?") with context-aware responses, leveraging memory management and Retrieval-Augmented Generation (RAG).
Features

Scenario: Querying legal documents for key insights.
Memory Management:
Short-Term Memory (STM): ChatMemoryBuffer (512-token limit) for recent chat history.
Long-Term Memory (LTM): Pinecone vector store for document embeddings.
RAG: Semantic search retrieves top-3 relevant document chunks.


Tools: Grok API, HuggingFaceEmbedding (sentence-transformers/all-MiniLM-L6-v2), Pinecone, LlamaIndex components (VectorStoreIndex, ReActAgent).

Setup
Prerequisites

Python 3.8+ (recommended).
Grok API key (Grok console).
Pinecone API key (Pinecone).
Google Colab or local Python environment.

Installation

Install dependencies:pip install pinecone==7.0.2 llama-index llama-index-llms-groq llama-index-embeddings-huggingface sentence-transformers


Set environment variables:
Replace your_grok_api_key_here with your Grok API key.
Replace your_pinecone_api_key_here with your Pinecone API key.



Data Preparation

Create a tax_law_2023.txt file with sample legal content (e.g., "2023 Tax Law Case: Key points include updated deductions...") or use your own documents.
Place the file in the same directory as the script.

Usage

Save the script as llamaindex_legal_qa.py.
Run the script in Colab or a local environment:python llamaindex_legal_qa.py


Observe the console output for the response to the query: "What are key points of 2023 tax law case?"
Test with custom queries by modifying the agent.chat() input.
Visualize the workflow using the Mermaid diagram (below) in Mermaid Live Editor.

Mermaid Workflow Diagram
graph TD
    A[User Query] --> B[ChatMemoryBuffer: STM]
    B --> C[RAG: Semantic Search]
    C --> D[Pinecone: LTM]
    D --> E[Query Engine]
    E --> F[Response]

Memory Management

STM: ChatMemoryBuffer stores recent interactions (512 tokens) for context continuity.
LTM: Pinecone stores document embeddings, enabling semantic search for RAG.
RAG: Retrieves relevant document chunks based on query similarity, enhancing response accuracy.

Pros and Cons

Pros:
Scalable for large document sets.
Robust RAG for precise retrieval.
Supports local processing.


Cons:
Complex setup with multiple components.
Resource-intensive.

