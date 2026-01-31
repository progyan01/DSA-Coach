# DSA-Coach


**DSA-Coach**  is an **Agentic RAG System** designed to simulate a real DSA tutor. Instead of handing out code solutions, it acts as a mentor—deconstructing complex problems, identifying logic gaps, and guiding students toward the correct algorithm using pedagogical hints.

---

## Key Features

### 1.  Story Deconstruction
The system uses prompt engineering to translate vague, narrative-based problems (e.g., *"Alice needs to connect cities with minimum cable"*) into concrete Computer Science concepts (*"Minimum Spanning Tree / Kruskal's Algorithm"*) before searching its knowledge base.

### 2.  Pedagogical Guardrails
Unlike standard LLMs that spoil the answer, DSA-Coach follows a strict **"Hint-First" Protocol**:
* **Syntax Errors:** Pointed out immediately.
* **Logic Errors:** The agent compares the student's logic to the retrieved documentation and asks leading questions (e.g., *"Does a standard Queue guarantee order in a weighted graph?"*).

### 3.  Stateful Agentic Reasoning
Built on **LangGraph**, the system employs a **Cyclic ReAct Architecture**. If the agent retrieves irrelevant notes, it doesn't hallucinate; it "loops back," refines its search query, and tries again until it finds the correct algorithmic pattern.

### 4.  High-Precision Retrieval
* **Embeddings:** Uses **BAAI/bge-m3** (568M parameters) running on T4 GPU for semantic search.
* **Vector Store:** FAISS (Facebook AI Similarity Search) for millisecond-latency retrieval from the curated `DSA-Coach` knowledge base.

---

## Tech Stack

| Component | Technology | Role |
| :--- | :--- | :--- |
| **Orchestration** | **LangGraph** & **LangChain** | Manages the cyclic reasoning loop and state memory. |
| **LLM** | **Google Gemini 2.5 Flash** | The "Brain" that reasons, plans, and generates hints. |
| **Vector DB** | **FAISS** | Stores chunked DSA notes for fast retrieval. |
| **Embeddings** | **HuggingFace (BGE-M3)** | Converts text to vectors (Running on CUDA/GPU). |
| **Interface** | **Python CLI** | Interactive loop for Code/Question ingestion. |

---

## Installation & Setup

This project is optimized for **Google Colab** (T4 GPU Runtime).

### 1. Prerequisites
* Google Account (for Colab).
* Google AI Studio API Key.

### 2. Install Dependencies
Run the following command to install the modern LangChain/LangGraph stack:
```python
!pip install -q -U langchain-community langchain-core langchain-text-splitters \
                langchain-google-genai faiss-cpu langgraph langchain-huggingface
