# 🧠 Mental Health Chatbot

## 🗂️ Overview  
A **web-based AI assistant** that provides mental health resources by analyzing multiple knowledge sources (**JSON/PDF**) using **LangChain** and **ChromaDB** vector storage.

---

## 🌟 Core Features  
- ✅ **Multi-source knowledge integration**  
  • Supports **2 JSON formats + PDF**

- 💬 **Conversational web interface**  
  • Clean and formatted AI responses

- 📚 **Source attribution**  
  • Clearly shows the **origin** of each response

- 💾 **Persistent memory**  
  • Stores embeddings and chat history using **ChromaDB**


---

## ⚡ Quick Start

### 📦 Install dependencies  
```bash
pip install -r requirements.txt
```

## Launch server
```
python deployment.py
```
### ➡️ Access at: http://localhost:8000




## Project Guide Map

## 📌 Features

- ✅ JSON intent and PDF document ingestion
- ✅ Chunking and embedding with HuggingFace
- ✅ Context-aware Retrieval QA using LangChain
- ✅ FastAPI backend with HTML chat interface
- ✅ Persisted vector store using Chroma
- ✅ Pluggable LLM backend (uses `llama3-70b-8192` via Groq)
- ✅ Source document traceability

---
### 1. Project Definition & Goal
- Build an LLM-powered mental health chatbot.
- Use context from structured intents and PDFs.
- Serve a clear, empathetic answer through a web interface.

### 2. Data Acquisition & Exploration
- 📁 JSON files (`intents.json`) with Q&A patterns.
- 📄 PDF files (`sample_data/`) as extra knowledge.
- Documents split into chunks for vector storage.
- Exploratory: simple loading, type checks, error handling.

### 3. Data Preprocessing
- Missing/invalid formats handled in loading loop.
- Text split using `RecursiveCharacterTextSplitter`.
- Embedding generated using `HuggingFaceBgeEmbeddings`.
- Stored in a persistent `Chroma` vector database.

### 4. Model Selection & Training
- **LLM Used:** `llama3-70b-8192` via `ChatGroq`.
- Retrieval with `LangChain RetrievalQA`.
- No model training — context passed directly to model for zero-shot answers.


### 5. Interpretation & Communication
- Answers returned from `/chat` endpoint with source metadata.
- Web interface built using Jinja2 + HTML.
- Answers clearly tagged with source (PDF / JSON).

### 6. Deployment
- FastAPI + `uvicorn` server.
- Auto port discovery for local deployment.
- Frontend rendered at `/` using `chat.html`.

---

## 💻 Tech Stack

| Component         | Tool / Library                                |
|------------------|------------------------------------------------|
| Backend API       | FastAPI                                        |
| Vector DB         | Chroma                                         |
| Embeddings        | HuggingFace (`sentence-transformers`)         |
| LLM               | ChatGroq (`llama3-70b-8192`)                   |
| Text Splitting    | LangChain `RecursiveCharacterTextSplitter`    |
| PDF Loader        | `PyPDFLoader`                                  |
| Templating        | Jinja2                                         |
| Deployment        | `uvicorn` with dynamic port handling          |

---

## 🧠 Component Breakdown

| Component                              | Explanation                                                                                              |
|----------------------------------------|----------------------------------------------------------------------------------------------------------|
| **Backend API – FastAPI**              | A modern Python web framework used to build and serve your chatbot’s API. Fast and easy to use.         |
| **Vector DB – Chroma**                 | Stores text data for semantic search. Handles embeddings and fast document retrieval.                   |
| **Embeddings – HuggingFace**           | Uses `sentence-transformers` to convert text into vectors capturing semantic meaning.                   |
| **LLM – ChatGroq (llama3-70b-8192)**   | A large language model running on Groq hardware for fast and accurate response generation.              |
| **Text Splitting – LangChain**         | `RecursiveCharacterTextSplitter` splits long texts into chunks while preserving context.                |
| **PDF Loader – PyPDFLoader**           | Loads and parses content from PDF files to prepare for embedding and search.                            |
| **Templating – Jinja2**                | Python templating engine for rendering dynamic HTML or structured responses.                            |
| **Deployment – uvicorn**               | Runs the FastAPI app using an ASGI server with dynamic port support, ideal for scalable deployments.    |



# 🔍 What This Code Does (in Simple Terms)

✅ **Loads data** from JSON (intents) and PDF files.

✅ **Converts them into documents** with metadata.

✅ **Splits the documents** into smaller chunks.

✅ **Creates embeddings** using a pretrained model (`HuggingFaceBgeEmbeddings`).

✅ **Stores the vectors** in a **Chroma vector store** (a type of database for embeddings).

✅ **Uses a powerful pretrained LLM** (LLaMA 3 via **ChatGroq**) to generate answers.

✅ **Exposes the QA system** via a **FastAPI endpoint**.

---

## ❌ Does it *train* a model?

No. It does **NOT** train a new machine learning or deep learning model from scratch.

Instead, it does this:

---

## 🧠 Pretrained Models Used

- **Embedding model**: `sentence-transformers/all-MiniLM-L6-v2`
- **LLM**: `llama3-70b-8192` (served via **Groq**)

---

## 🧮 What It *Does* Do

- **Embeds texts** (vectorizes them) and stores them
- Uses **RetrievalQA**, which performs **retrieval-augmented generation (RAG)**

---

## 🔄 So How Does It *Behave Like Training*?

The only “learning-like” aspect is:

> Embedding the intents and PDFs into vector space to enable **semantic search**.

This is not full training, but rather a **data preparation + embedding step**.

Embedding the intents and PDFs into vector space to enable semantic search.

This is not full training, but rather a data preparation + embedding step.

