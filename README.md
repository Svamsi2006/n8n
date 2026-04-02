<img width="1709" height="765" alt="image" src="https://github.com/user-attachments/assets/08123026-be19-49f8-a0c9-073d5224a564" />
## 🚀 AI RAG Chat bot
<img width="1525" height="881" alt="image" src="https://github.com/user-attachments/assets/49c15cc6-78f1-4591-ba01-4f07cfb0040d" />
## LinkedIn job searcher
## 🧩 Overview

This project defines a modular AI-powered workflow that processes incoming requests via webhooks, chat, and document uploads. It performs research, document processing, and content generation, and stores embeddings in a vector database for retrieval.

---

## ⚙️ Architecture

### 🔹 Entry Points

- **Webhook Trigger**
  - Accepts external POST requests
  - Starts workflow execution

- **Chat Trigger**
  - Handles real-time user interaction

- **Document Upload Webhook**
  - Accepts files (e.g., PDFs)

---

### 🤖 Core AI Agent

The AI Agent acts as the central orchestrator:

- Chat model integration  
- Memory (Window Buffer)  
- Tool execution  
- Output parsing  

---

### 🧠 Memory

- **Window Buffer Memory**
  - Maintains conversation context
  - Supports multi-turn interactions

---

## 🛠️ Tools

### Utility Tools
- Weather API Tool
- Calculator
- Current DateTime Tool

### Web & Data Tools
- SerpAPI Web Search
- URL Content Fetcher

### GitHub Tools
- Create Issue
- Create File
- List Files
- Create Pull Request

### Google Sheets
- Read sheet data

---

## 📄 Document Processing Pipeline

1. Document Loader  
2. Text Splitter  
3. Extract Document Content  
4. Generate Embeddings  
5. Store in Vector Database  

---

## 🔍 Research Agent

- Uses Groq Chat Model  
- Performs web search via SerpAPI  
- Conducts deep analysis  

---

## ✍️ Content Creator

- Powered by Groq Chat Model  
- Generates:
  - Blogs  
  - Social media content  
  - Code  
  - Reports  

---

## 🧠 Vector Database

### Pinecone

- Stores embeddings for:
  - Documents  
  - Research  
  - Generated content  

- Enables:
  - Semantic search  
  - Retrieval-Augmented Generation (RAG)  

---

## 🔄 Workflow

```text
Input (Webhook / Chat / Upload)
        ↓
AI Agent (Orchestrator)
        ↓
Tool Usage
        ↓
Document Processing (if any)
        ↓
Research Agent (optional)
        ↓
Content Creator (optional)
        ↓
Embeddings Generation
        ↓
Pinecone Storage
        ↓
Response Output
```

---

## 📤 Outputs

- Webhook Response  
- Chat Response  
- Document Processing Result  

---

## 🔐 Features

- Modular architecture  
- Multi-input support  
- Tool-integrated AI  
- RAG system  
- Scalable vector storage  
- Extensible design  

---

## 🧪 Use Cases

- AI research assistant  
- Content automation  
- Document Q&A system  
- Knowledge base with semantic search  
- Developer automation (GitHub integration)  

---

## 🏁 Getting Started

1. Add API Keys:
   - Groq  
   - SerpAPI  
   - Pinecone  
   - Cohere (optional)

2. Configure environment variables  

3. Deploy workflow  

4. Trigger via:
   - Webhook  
   - Chat  
   - Document upload  

---

## 📌 Notes

- Embedding model: `nomic-embed-text`  
- Session memory enabled  
- Easily extendable with new tools  

---

## 📄 License

MIT License
