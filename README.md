# Assignment02
Intelligent Multi-Source Research Assistant (Advanced RAG)

# 📄 Agentic RAG System with Confidence Scoring

An end-to-end Agentic Retrieval-Augmented Generation (RAG) system that intelligently processes documents, routes user queries to appropriate tools, and returns responses with citations and confidence scores.

Built using LangChain, FAISS, HuggingFace embeddings, Groq LLM, and Gradio UI.

## 🚀 Features
- **📂 Multi-format Document Support**
  - PDF
  - CSV
  - JSON
  - Markdown
- **🧠 Agent-Based Query Routing**
  - Automatically selects the right tool:
    - Summarization
    - Question Answering
    - Analytical Comparison
- **🔍 Vector Search with FAISS**
  - Semantic retrieval using embeddings
- **🧾 Citations**
  - Displays document sources used for answers
- **📊 Confidence Scoring**
  - Combines:
    - LLM self-evaluation
    - Retrieval similarity scores
- **🌐 Interactive UI**
  - Built with Gradio for easy usage

## 🏗️ System Architecture
```
User Query 
     ↓ 
Agent Router (LLM-based decision) 
     ↓ 
 ┌───────────────┬───────────────┬──────────────────┐
 │ Summarizer    │ Q&A Tool      │ Analytical Tool  │
 └───────────────┴───────────────┴──────────────────┘
     ↓ 
Retriever (FAISS + Embeddings)
     ↓ 
LLM (Groq - LLaMA 3.3)
     ↓ 
Response + Citations + Confidence
```

## ⚙️ Installation
Run the following in your environment (Colab/local):
```bash
pip uninstall -y langchain langchain-core langchain-community langchain-text-splitters langsmith langchain-groq langgraph langgraph-prebuilt
pip install langchain==0.2.16
pip install langchain-core==0.2.43
pip install langchain-community==0.2.16
pip install langchain-text-splitters==0.2.4
pip install langsmith==0.1.147
pip install langchain-groq==0.1.5
pip install sentence-transformers faiss-cpu pypdf gradio markdown unstructured
pip install numpy==1.26.4 --force-reinstall```

## 🔑 Setup
Set your Groq API key:
```python import os os.environ["GROQ_API_KEY"] = "your_api_key_here"```

## 📂 Supported File Types and Loaders:
| Format | Loader Used |
|---------|--------------|
| PDF | PyPDFLoader |
| CSV | CSVLoader |
| JSON | JSONLoader |
| Markdown | UnstructuredMarkdownLoader |

## 🔄 Workflow Steps:
e.g.,
defaults to a typical process flow.
a) Upload Documents: Files are loaded and converted into Document objects.
b) Chunking: Uses RecursiveCharacterTextSplitter with chunk size of 800 and overlap of 100.
c) Embeddings: Model used is `sentence-transformers/all-MiniLM-L6-v2`.
d) Vector Store: FAISS for similarity search.
e) Query Handling: Agent Router decides among tools.
f) Tools include Summarizer, Q&A, and Analytical tools.
g) Confidence Scoring System combines LLM self-evaluation and retrieval confidence to produce a final score.
h) Gradio Interface provides file upload, process button, query input, and output display including response, tool used, citations, and confidence.
i) Run the app with `demo.launch(debug=True)`.
j) Example Queries include summarizing documents or comparing methods.
k) Known issues involve scaling challenges and heuristic scoring; future improvements aim at persistent storage, better routing, streaming responses, UI enhancements, benchmarks, and handling large documents.
l) Tech Stack includes Groq LLaMA 3.3 B model, LangChain framework, Sentence Transformers embeddings, FAISS vector database, Gradio frontend.
m) License notes educational/research use.
