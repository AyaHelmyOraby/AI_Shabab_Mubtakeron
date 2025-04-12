
# Mental Health Chatbot with Multi-Source Knowledge Base

## Overview
This project implements a mental health chatbot that combines information from multiple sources (JSON intents, PDF documents, and structured Q&A pairs) into a unified knowledge base using vector embeddings. The chatbot uses Groq's LLM (Llama 3 70B) for generating responses while being grounded in the provided knowledge sources.

## Features
- **Multi-format support**: Processes JSON files (both intent-based and context-response formats) and PDF documents.
- **Vector database**: Uses ChromaDB with sentence-transformers embeddings for efficient retrieval.
- **Context-aware responses**: Generates responses based on both retrieved knowledge and LLM capabilities.
- **Source attribution**: Shows which knowledge sources contributed to each response.
- **Error resilient**: Handles different file formats and metadata types gracefully.

## Code Structure
```
mental-health-chatbot/
│
├── main.py                 # Main application script
├── chroma_db/              # Directory for persistent vector storage
└── sample_data/            # Directory for input files
    ├── intents.json        # Example intent-based JSON file
    ├── qa_pairs.json       # Example context-response JSON file
    └── mental_health.pdf   # Example PDF document
```

## Key Components

### 1. Document Loaders
- **JSON Loaders**:
  - `load_chatbot_json()`: Handles intent-based JSON with patterns/responses.
  - `load_context_response_json()`: Handles simple context-response pairs.
- **PDF Loader**: `load_pdf()` processes PDF documents using PyPDFLoader.

### 2. Vector Database
- Creates unified vector store from all sources.
- Uses all-MiniLM-L6-v2 sentence transformer for embeddings.
- Implements metadata conversion for ChromaDB compatibility.

### 3. Chatbot Engine
- RetrievalQA chain with custom prompt template.
- Groq's Llama 3 70B model for response generation.
- Source attribution in responses.

## Setup Instructions

### 1. Install dependencies:
```bash
pip install langchain langchain-community langchain-groq chromadb pypdf sentence-transformers
```

### 2. Prepare your data:
- Place JSON files in `./sample_data/` (either intent-based or context-response format).
- Place PDF documents in the same directory.

### 3. Set up API key:
- Replace the placeholder Groq API key in `initialize_llm()` with your actual key.

### 4. Run the chatbot:
```bash
python main.py
```

## Usage
- Start a conversation by typing your message.
- The chatbot will respond using knowledge from all available sources.
- Type "exit" to end the session.
- Each response shows which sources contributed to the answer.

## Customization

### To add new knowledge sources:
- **JSON files**:
  - For intent-based format: Include `patterns` and `responses` arrays.
  - For Q&A format: Include `Context` and `Response` pairs.
- **PDF documents**:
  - Add any mental health-related PDFs to the `sample_data` directory.

### To modify the chatbot behavior:
- Edit the prompt template in `setup_qa_chain()`.
- Adjust temperature or model parameters in `initialize_llm()`.
- Change chunking parameters in `RecursiveCharacterTextSplitter`.

## Troubleshooting
- **Metadata errors**: Ensure all metadata values are simple types (str, int, float, bool).
- **File loading issues**: Check file formats match expected structures.
- **API errors**: Verify your Groq API key is valid and has sufficient quota.

## Future Enhancements
- Add support for more file formats (Word, HTML, etc.).
- Implement conversation history.
- Add evaluation metrics for response quality.
- Include user feedback mechanism.

## Dependencies
- Python 3.8+

See `requirements.txt` for full package requirements.
