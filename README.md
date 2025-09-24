# RAG Pipeline Chatbot

This project implements a **Retrieval-Augmented Generation (RAG)** pipeline to create a chatbot that can answer questions based on a company's policy documents. The system is designed for **easy updates**—new information can be added simply by uploading documents to a specified Google Drive folder.

---

## 📜 Overview
The system has two main components:

1. **RAG Pipeline** – Automatically ingests and processes new policy documents.  
2. **Chatbot** – Uses the processed information to answer user queries in real time.

---

## ⚙️ RAG Pipeline Setup
The RAG pipeline is triggered whenever a new file is uploaded to the designated Google Drive folder. The steps include:

### 1. **Google Drive Trigger**
A new file uploaded to the target Google Drive folder initiates the pipeline.

### 2. **Download File**
The pipeline downloads the newly uploaded document.

### 3. **Embeddings Generation**
The document text is converted into **vector representations (embeddings)** using the **OpenAI Embeddings API**.  
These embeddings capture the semantic meaning of the text for efficient search and retrieval.

### 4. **Text Splitting**
The document is split into smaller, manageable chunks using a **Recursive Character Text Splitter**.  
This improves retrieval accuracy by allowing chunk-level semantic search.

### 5. **Pinecone Vector Store**
The generated embeddings and their corresponding text chunks are stored in a **Pinecone Vector Database**, which serves as the knowledge base for the chatbot.

---

## 💬 Chatbot with Knowledge Base
The chatbot uses the RAG pipeline’s knowledge base to deliver precise answers to user queries.

### Workflow:
1. **User Message Received**  
   The chatbot is activated when a user sends a message.

2. **AI Agent**  
   A **Language Model (e.g., OpenRouter Chat Model)** processes the query.

3. **Knowledge Retrieval**  
   - The query is converted into an embedding using **OpenAI Embeddings**.
   - Relevant document chunks are retrieved from the **Pinecone Vector Store**.

4. **Response Generation**  
   The language model combines the retrieved information with its own reasoning to generate a **context-aware response**.

---

## 🚀 How to Use

### 1. **Ingesting Policy Documents**
- Upload new policy documents (**PDF**, **DOCX**, **TXT**, etc.) to the designated Google Drive folder.
- The RAG pipeline will:
  - Automatically detect the new file,
  - Process it,
  - Update the Pinecone Vector Store.

### 2. **Interacting with the Chatbot**
- Use the provided chat interface to ask questions.  
- Example queries:
  - “What is the company’s policy on remote work?”
  - “How many sick days are employees entitled to?”
  - “Can you explain the expense reimbursement process?”
  - “What are the rules for using company-provided vehicles?”

---

## 🛠️ Requirements and Dependencies
- **Google Drive API** – Detects new file uploads to trigger the pipeline.
- **OpenAI API Key** – Generates embeddings for document text and user queries.
- **Pinecone API Key** – Stores and retrieves vector embeddings.
- **OpenRouter API Key** – Powers the language model for response generation.

---

## 🤝 Contribution
This project is an excellent foundation for building custom, document-aware chatbots.  
Possible extensions:
- Support additional document types (e.g., HTML, CSV).
- Integrate with other data sources (databases, APIs).
- Fine-tune the AI agent for domain-specific use cases.

---
