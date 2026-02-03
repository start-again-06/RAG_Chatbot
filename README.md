# Chat with PDF using Gemini (RAG Application)

This project is a Streamlit-based Retrieval-Augmented Generation (RAG) application that enables users to upload PDF documents and ask natural language questions about their content. The system retrieves relevant information from the uploaded documents and generates accurate, context-grounded answers using Google Gemini Pro.

---

## Overview

The application combines document retrieval and large language model reasoning to ensure responses are strictly based on the provided PDFs. It is designed for document analysis, research assistance, and knowledge extraction use cases.

---

## Features

- Upload and process one or multiple PDF files
- Automatic text extraction and chunking
- Semantic search using vector embeddings
- Context-aware question answering
- Interactive Streamlit interface

---

## Tech Stack

- Frontend: Streamlit  
- LLM: Google Gemini Pro  
- Embeddings: Google Generative AI (`embedding-001`)  
- Vector Store: FAISS  
- Framework: LangChain  
- PDF Processing: PyPDF2  

---

## High-Level Architecture

The application follows a Retrieval-Augmented Generation (RAG) architecture that integrates document ingestion, vector-based retrieval, and large language model inference.

### Architecture Flow

1. Users upload PDF files and submit questions via the Streamlit UI.
2. PDF content is extracted and split into overlapping text chunks.
3. Text chunks are converted into vector embeddings.
4. Embeddings are stored in a FAISS vector index.
5. User queries are embedded and matched against stored vectors.
6. Relevant document chunks are retrieved.
7. Gemini Pro generates an answer using the retrieved context.
8. The response is displayed to the user.


---

## System Design

The system is designed as a modular, scalable pipeline that separates document ingestion, retrieval, and generation responsibilities.

### Core Components

#### Client Layer
- Streamlit-based web interface
- Handles PDF uploads, user queries, and result display
- Stateless and lightweight

#### Application Layer
- Orchestrates the end-to-end workflow
- Manages ingestion, retrieval, and inference pipelines

#### Document Processing Layer
- Extracts text from PDFs
- Splits text into overlapping chunks to preserve context

#### Embedding Layer
- Converts document chunks and user queries into dense vector embeddings
- Ensures embedding consistency across ingestion and retrieval

#### Vector Database
- FAISS stores document embeddings locally
- Enables fast similarity search

#### Retrieval Layer
- Retrieves the most relevant document chunks for a given query
- Controls context size sent to the LLM

#### LLM Inference Layer
- Gemini Pro generates answers using retrieved document context
- Prevents hallucinations by restricting responses to known content

#### Response Layer
- Formats and displays the final answer
- Handles fallback responses when context is insufficient

---

### End-to-End Request Flow

1. User uploads PDFs and initiates processing.
2. Text is extracted, chunked, embedded, and indexed.
3. User submits a question.
4. The query is embedded and searched against FAISS.
5. Relevant chunks are retrieved.
6. Retrieved context is passed to Gemini Pro.
7. The generated answer is returned to the user.

---

## Design Considerations

- Context-grounded generation to reduce hallucinations  
- Modular design for easy extension  
- Efficient retrieval using vector similarity search  
- Model-agnostic architecture  

---

## Scalability and Extensions

- Replace FAISS with managed vector databases for large-scale use  
- Add OCR support for scanned PDFs  
- Introduce user authentication and document namespaces  
- Enable chat history and conversational memory  
- Deploy on Streamlit Cloud or containerized platforms  

---

## License

This project is open-source and available under the MIT License.




