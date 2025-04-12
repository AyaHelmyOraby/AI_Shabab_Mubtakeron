
# 🧠 AI Chatbot Project

## 📁 Project Structure

```
ML/
├── chroma_db/               # Local database folder for Chroma
│   └── chroma.sqlite3       # ChromaDB SQLite file
│
├── myenv/                   # Python virtual environment
│
├── sample_data/             # Folder for test or sample data
│
├── static/                  # Static files (CSS, JS, etc.)
│   └── style.css
│
├── templates/               # HTML templates
│   └── chat.html
│
├── .env                     # Environment variables
├── deployment.py            # Main FastAPI app
├── requirements.txt         # Python dependencies
└── README.md                # Project overview (this file)
```

## 🚀 Project Description

This is a **web-based chatbot application** built using:
- **FastAPI** for the backend
- **Jinja2** for server-side rendering
- **HTML/CSS** for the frontend
- **ChromaDB** for vector-based semantic search
- **LangChain** for LLM interaction

## 🛠 How to Run the Project

1. **Create virtual environment**
   ```bash
   python -m venv myenv
   ```

2. **Activate virtual environment**
   - On Windows:
     ```bash
     myenv\Scripts\activate
     ```
   - On macOS/Linux:
     ```bash
     source myenv/bin/activate
     ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Run the app**
   ```bash
   uvicorn deployment:app --reload --port 8001
   or
   py deployment.py
   ```

5. **Visit in browser**
   ```
   http://127.0.0.1:8001
   ```

## ✏️ Key Files

- `deployment.py` – Main FastAPI application
- `chat.html` – Frontend template for chatbot
- `style.css` – Styling for chatbot interface
- `chroma.sqlite3` – Local database used for semantic search

## 📌 Features

- Chat interface
- LLM interaction with LangChain
- ChromaDB for semantic memory
- Clean UI with CSS styling
