# 📅 AI Medical Assistant Chatbot — RAG-based Application
---

## 🧠 Project Overview

This application is a **Medical Domain Chatbot** built using **Retrieval-Augmented Generation (RAG)**. It allows users to upload their own medical documents (e.g., textbooks, reports), and the system intelligently answers queries by retrieving the most relevant content before generating a final response.

---

## 🎓 What is RAG?

**RAG (Retrieval-Augmented Generation)** enhances language models by supplying relevant external context from a knowledge base, preventing hallucinations and improving accuracy, especially for factual or specialized domains like **medicine**.

---

## 🔄 Architecture

```
User Input
   ↓
Query Embedding → Pinecone Vector DB ← Embedded Chunks ← Chunking ← PDF Loader
   ↓
Retrieved Docs
   ↓
     RAG Chain (Groq + LangChain)
   ↓
LLM-generated Answer
```

For a detailed view, refer to the **[MedicalAssistant.pdf](./assets/MedicalAssistant.pdf)**

---

## 📚 Features

- Upload medical PDFs (notes, books, etc.)
- Auto-extracts text and splits into semantic chunks
- Embeds using Google/BGE embeddings
- Stores vectors in **Pinecone DB**
- Uses **Groq's LLaMA3-70B** via LangChain
- FastAPI backend with endpoints for file upload and Q\&A

---

## 🌐 Tech Stack

| Component  | Tech Used                  |
| ---------- | -------------------------- |
| LLM        | Groq API (LLaMA3-70B)      |
| Embeddings | Google Generative AI / BGE |
| Vector DB  | Pinecone                   |
| Framework  | LangChain                  |
| Backend    | FastAPI                    |
| Deployment | Render                     |

---

## 📚 API Endpoints

```http
POST /upload_pdfs/ --- Upload one or more PDF files

POST /ask/ --- Ask a question --- Form field: `question`

```

---

## 📁 Folder Structure

```
└── 📁assets
    ├── DIABETES.pdf
    ├── MedicalAssistant.pdf
    └── medicalAssistant.png
```

```
└── 📁client
    └── 📁__pycache__
        ├── config.cpython-311.pyc
    └── 📁components
        └── 📁__pycache__
            ├── chatUI.cpython-311.pyc
            ├── history_download.cpython-311.pyc
            ├── upload.cpython-311.pyc
        ├── chatUI.py
        ├── history_download.py
        ├── upload.py
    └── 📁utils
        └── 📁__pycache__
            ├── api.cpython-311.pyc
        ├── api.py
    ├── app.py
    ├── config.py
    └── requirements.txt
```

```
└── 📁server
    └── 📁__pycache__
        ├── logger.cpython-311.pyc
        ├── main.cpython-311.pyc
        ├── test.cpython-311.pyc
    └── 📁middlewares
        └── 📁__pycache__
            ├── exception_handlers.cpython-311.pyc
        ├── exception_handlers.py
    └── 📁modules
        └── 📁__pycache__
            ├── llm.cpython-311.pyc
            ├── load_vectorstore.cpython-311.pyc
            ├── query_handlers.cpython-311.pyc
        ├── llm.py
        ├── load_vectorstore.py
        ├── pdf_handlers.py
        ├── query_handlers.py
    └── 📁routes
        └── 📁__pycache__
            ├── ask_question.cpython-311.pyc
            ├── upload_pdfs.cpython-311.pyc
        ├── ask_question.py
        ├── upload_pdfs.py
    └── 📁uploaded_docs
        ├── DIABETES.pdf
        ├── Supratim Nag - LOR.pdf
    ├── .env
    ├── logger.py
    ├── main.py
    ├── requirements.txt
    └── test.py
```
## Screenshots
<img width="1917" height="1025" alt="1" src="https://github.com/user-attachments/assets/2f4fe766-4855-436c-89fe-40fef47809aa" />
<img width="1917" height="1021" alt="2" src="https://github.com/user-attachments/assets/05d0aef8-ec36-47b6-882a-3b0a46444d57" />

<img width="1570" height="765" alt="3" src="https://github.com/user-attachments/assets/ca0ba5b8-e85f-407f-be5d-de479f996cab" />
<img width="1592" height="832" alt="2" src="https://github.com/user-attachments/assets/e218f295-c3d1-4e36-b171-26321b0227e7" />
<img width="1507" height="790" alt="1" src="https://github.com/user-attachments/assets/f644f10b-239b-43a8-b939-235fcd03f9a4" />


---

## ⚡ Quick Setup

```bash
# Clone the repo
$ git clone https://github.com/Bandish04/MedicalAssistant
$ cd medicalAssistant/server

# Create virtual env
$ uv venv
$ .venv/bin/activate  # Windows: venv\Scripts\activate

# Install dependencies
$ uv pip install -r requirements.txt

# Set environment variables (.env)
GOOGLE_API_KEY=...
GROQ_API_KEY=...
PINECONE_API_KEY=...

# Run the server
$ uvicorn main:app --reload --port 8000


$ cd medicalAssistant/client

# Create virtual env
$ uv venv
$ .venv/bin/activate  # Windows: venv\Scripts\activate

# Install dependencies
$ uv pip install -r requirements.txt

# Run the server
$ streamlit run app.py
```

---

## 🌐 Deployment

- Hosted on [Render](https://render.com)
- Configure `start command` as:

  ```bash
  uvicorn main:app --host 0.0.0.0 --port 10000
  ```

---

## 🌟 Credits

- Built by Supratim Nag
- Inspired by LangChain, Groq, Pinecone, and FastAPI ecosystems

---

## 🎉 License

This project is licensed under the MIT License.
