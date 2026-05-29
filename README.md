# 🦙 RAG-LLaMA-LangChain-FAISS

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/LangChain-🦜-1C3C3C?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/FAISS-Vector_DB-blue?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Ollama-LLaMA_3.1-black?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge"/>
</p>

<p align="center">
  A fully local <strong>Retrieval-Augmented Generation (RAG)</strong> system built using <strong>LangChain</strong>, <strong>FAISS</strong>, and <strong>LLaMA 3.1</strong> via Ollama — capable of answering questions from real web content with context-aware, intelligent responses. No paid APIs required.
</p>

---

## 🚀 Project Overview

This project implements a **complete end-to-end RAG pipeline** that:

- 🌐 Extracts data from web sources (Wikipedia)
- ✂️ Splits text into meaningful chunks with overlap strategy
- 🧠 Converts text into embeddings using `nomic-embed-text` via Ollama
- ⚡ Stores and searches embeddings using FAISS vector database
- 🔍 Retrieves the most relevant context based on user query
- 🤖 Generates intelligent, grounded answers using LLaMA 3.1 (fully local)

---

## 🧠 Architecture

```
┌─────────────────────────────────────────────────────┐
│                    RAG PIPELINE                     │
│                                                     │
│   📥 Web Loader (Wikipedia / BeautifulSoup)         │
│              ↓                                      │
│   ✂️  Text Splitter (Chunk + Overlap)               │
│              ↓                                      │
│   🧠 Embeddings (nomic-embed-text via Ollama)       │
│              ↓                                      │
│   🗄️  FAISS Vector Store (Index & Store)            │
│                                                     │
│   ─────────── At Query Time ─────────────           │
│                                                     │
│   ❓ User Query                                     │
│              ↓                                      │
│   🧠 Query Embedding (Ollama)                       │
│              ↓                                      │
│   ⚡ FAISS Similarity Search                        │
│              ↓                                      │
│   📄 Relevant Context Retrieval                     │
│              ↓                                      │
│   🤖 LLaMA 3.1 (via Ollama) — Answer Generation    │
│              ↓                                      │
│   ✅ Final Context-Aware Answer                     │
└─────────────────────────────────────────────────────┘
```

---

## ✨ Features

| Feature | Description |
|---|---|
| 🔍 Web Ingestion | Fetches live data from Wikipedia using LangChain loaders |
| ✂️ Smart Chunking | Text split with configurable chunk size and overlap |
| 🧠 Local Embeddings | Uses `nomic-embed-text` model via Ollama |
| ⚡ FAISS Vector DB | Fast approximate nearest-neighbor search |
| 🤖 Local LLM | LLaMA 3.1 8B running entirely on your machine via Ollama |
| 📄 Context-Aware QA | Answers grounded in retrieved document context |
| 🔒 Fully Local | No OpenAI, no paid API — runs 100% on your hardware |

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Language | Python 3.10+ |
| Orchestration | LangChain |
| Vector Database | FAISS |
| LLM & Embeddings | Ollama (LLaMA 3.1, nomic-embed-text) |
| Web Scraping | BeautifulSoup4 |
| Config | python-dotenv |
| Notebook | Jupyter |

---

## 📦 Installation

### 1. Clone the repository

```bash
git clone https://github.com/your-username/rag-llama-langchain-faiss.git
cd rag-llama-langchain-faiss
```

### 2. Install Python dependencies

```bash
pip install -r requirements.txt
```

### 3. Setup Ollama & pull models

Make sure [Ollama](https://ollama.com) is installed and running, then pull the required models:

```bash
ollama pull llama3.1:8b
ollama pull nomic-embed-text
```

### 4. Configure environment variables

Create a `.env` file in the root directory:

```env
LANGCHAIN_API_KEY=your_key_here
LANGCHAIN_PROJECT=rag-project
LANGCHAIN_TRACING_V2=true
```

> 💡 LangChain tracing is optional. You can disable it by setting `LANGCHAIN_TRACING_V2=false`.

---

## ▶️ How to Run

**Option A — Jupyter Notebook:**

```bash
jupyter notebook
```

**Option B — Python Script:**

```bash
python app.py
```

---

## 💡 Example Queries

```python
"Why is Hanumanji so powerful?"
"What is the Ramayana?"
"What is the Mahabharata?"
"Why is the USA so powerful?"
```

The system retrieves relevant context from Wikipedia and generates accurate, grounded responses using LLaMA 3.1 — all running locally on your machine.

---

## 📊 Sample Output

```
Query: Why is Hanumanji so powerful?

🔍 Retrieving relevant context from FAISS...
📄 Top 3 chunks retrieved.

🤖 LLaMA 3.1 Response:
Hanumanji is considered one of the most powerful figures in Hindu mythology
due to his unwavering devotion to Lord Rama, immense physical strength,
and divine blessings from multiple gods. According to the Ramayana...
```

---

## 📁 Project Structure

```
rag-llama-langchain-faiss/
│
├── app.py                  # Main RAG pipeline script
├── notebook.ipynb          # Jupyter notebook version
├── requirements.txt        # Python dependencies
├── .env                    # Environment variables (not committed)
├── faiss_index/            # Saved FAISS vector store
└── README.md
```

---

## 📌 Key Learnings

- ✅ Designing and implementing a complete **RAG pipeline** from scratch
- ✅ Using **FAISS** for efficient vector storage and semantic search
- ✅ Local embedding generation with **nomic-embed-text**
- ✅ Local LLM inference using **Ollama** (zero API cost)
- ✅ **LangChain** orchestration for document loading, splitting, retrieval, and generation
- ✅ Prompt engineering for grounded, context-aware responses

---

## 🔮 Future Improvements

- [ ] 🌐 Add **Streamlit UI** for an interactive chat interface
- [ ] 📄 Support **PDF & multi-document ingestion**
- [ ] 🔍 Add **reranking** (e.g., cross-encoder) for better retrieval accuracy
- [ ] 🚀 Deploy as a **web app** (FastAPI / Render / HuggingFace Spaces)
- [ ] 💬 Add **conversational memory** for multi-turn Q&A
- [ ] 🗂️ Support multiple vector stores (Chroma, Pinecone)

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

1. Fork the project
2. Create your feature branch: `git checkout -b feature/amazing-feature`
3. Commit your changes: `git commit -m 'Add amazing feature'`
4. Push to the branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

---

## 📜 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 👨‍💻 Author

**Prabhat Maurya**
CSE Student | AI/ML Enthusiast

<p>
  <a href="https://github.com/your-username"><img src="https://img.shields.io/badge/GitHub-your--username-181717?style=flat&logo=github"/></a>
  <a href="https://linkedin.com/in/your-profile"><img src="https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat&logo=linkedin"/></a>
</p>

---

<p align="center">
  If you found this project helpful, please consider giving it a ⭐ — it means a lot!<br/>
  Feel free to <strong>fork</strong>, <strong>share</strong>, and <strong>build on top of it</strong>. 🚀
</p>
