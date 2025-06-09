# 🧠 Corrective RAG with LangGraph, Ollama, and Chroma

This project implements a fully local **Corrective Retrieval-Augmented Generation (RAG)** pipeline using [LangGraph](https://docs.langchain.com/langgraph), [Ollama](https://ollama.com), and [LangChain](https://www.langchain.com). The system can intelligently decide if retrieved documents are relevant, rewrite unclear questions, supplement with web search if needed, and only then generate a final response — all running locally using LLaMA 3.

---

## 🚀 Key Features

- 🔄 **Corrective RAG Workflow**  
  Retrieve, filter, rewrite, search, and only then generate — based on document quality.

- 🧠 **LLaMA 3 via Ollama**  
  Local inference using open-source models — no OpenAI key or internet required.

- 🔍 **Document Relevance Grading**  
  A local LLM grades each document's relevance using binary "yes/no" responses.

- ✏️ **Question Rewriting**  
  Automatically improves vague or poorly-formed queries using LLaMA 3.

- 🌐 **Optional Web Search (Tavily)**  
  Adds web results only when local context is insufficient.

- 📄 **Chroma Vectorstore + HF Embeddings**  
  Fast local retrieval using `sentence-transformers/all-MiniLM-L6-v2`.

---

## 🧠 What Is “Corrective RAG”?

Unlike basic RAG (retrieve → generate), **corrective RAG introduces decision-making**:

1. **Retrieve** documents from a vectorstore  
2. **Grade** relevance using an LLM  
3. If relevant → **Generate answer**  
4. If not → **Rewrite question** and **fallback to web search**  
5. Generate a better answer using improved context

This pipeline gives your LLM **awareness of context quality** — and the ability to fix bad inputs or retrieval failures automatically.

---

## 🛠️ Setup

> Requires Python 3.10+ and macOS/Linux with [Ollama installed](https://ollama.com/download)

### 1. Clone the repo

```bash
git clone https://github.com/yourusername/corrective-rag-langgraph.git
cd corrective-rag-langgraph

```

### 2. Create a virtual environment and install dependencies

```bash
python3 -m venv env
source env/bin/activate
pip install -r requirements.txt

```


### 3. Start Ollama and load the LLaMA 3 model
```bash
ollama run llama3
```

### 4. (Optional) Add Tavily API key for web search

```bash
export TAVILY_API_KEY=your-key

```


