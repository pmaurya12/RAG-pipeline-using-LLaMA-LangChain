# 🦙 RAG-LLaMA-LangChain-FAISS

<p>
  <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=flat&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/LangChain-🦜-1C3C3C?style=flat"/>
  <img src="https://img.shields.io/badge/FAISS-Vector_DB-blue?style=flat"/>
  <img src="https://img.shields.io/badge/Ollama-LLaMA_3.1-black?style=flat"/>
</p>

A fully local **Retrieval-Augmented Generation (RAG)** system built with **LangChain**, **FAISS**, and **LLaMA 3.1** via Ollama. Answers questions from real web content — no paid APIs required.

---

## 🧠 Pipeline

```
Web Loader (Wikipedia)
        ↓
Text Splitter (Chunk + Overlap)
        ↓
Embeddings (nomic-embed-text · Ollama)
        ↓
FAISS Vector Store
        ↓
User Query → Query Embedding → Similarity Search
        ↓
Relevant Context + LLaMA 3.1
        ↓
Final Answer
```

---

## 🛠️ Tech Stack

| | |
|---|---|
| Orchestration | LangChain |
| Vector DB | FAISS |
| LLM | LLaMA 3.1 8B (Ollama) |
| Embeddings | nomic-embed-text (Ollama) |
| Web Scraping | BeautifulSoup4 |

---

## 📦 Setup

```bash
git clone https://github.com/your-username/rag-llama-langchain-faiss.git
cd rag-llama-langchain-faiss
pip install -r requirements.txt
```

```bash
ollama pull llama3.1:8b
ollama pull nomic-embed-text
```

Create a `.env` file:
```env
LANGCHAIN_API_KEY=your_key_here
LANGCHAIN_TRACING_V2=true
LANGCHAIN_PROJECT=rag-project
```

## ▶️ Run

```bash
python app.py
# or
jupyter notebook
```

---

## 🔮 Upcoming

- [ ] Streamlit chat UI
- [ ] PDF ingestion support
- [ ] Conversational memory
- [ ] Web app deployment

---

👨‍💻 **Prabhat Maurya** · CSE Student | AI/ML Enthusiast

⭐ Star the repo if you found it useful!
