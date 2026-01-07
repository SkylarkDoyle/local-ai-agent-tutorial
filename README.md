# 🍕 Pizza Restaurant Local AI Agent

A local **Retrieval-Augmented Generation (RAG)** system that allows users to ask questions about a pizza restaurant's performance, food quality, and customer service. The agent uses real customer reviews to provide factual, context-aware answers.

![Local AI Agent](https://img.shields.io/badge/AI-Local-orange?style=for-the-badge)
![Ollama](https://img.shields.io/badge/Ollama-llama3.2-blue?style=for-the-badge)
![LangChain](https://img.shields.io/badge/LangChain-Framework-white?style=for-the-badge)

---

## 🚀 Overview

This project demonstrates how to build a fully local AI agent using **Ollama**, **LangChain**, and **ChromaDB**.

The system reads 120+ realistic restaurant reviews from a CSV file, embeds them into a local vector database, and uses a Large Language Model (LLM) to retrieve relevant context when responding to user queries.

### Key Features

- **Privacy First**: Everything runs locally on your machine. No data leaves your network.
- **RAG Architecture**: Combines the reasoning capabilities of LLMs with specific, up-to-date data from customer reviews.
- **Persistent Storage**: Reviews are indexed once and stored in a local ChromaDB instance for fast subsequent lookups.
- **Interactive CLI**: Easy-to-use command-line interface for chatting with the agent.

---

## 🛠️ Technology Stack

- **LLM**: `llama3.2` (via Ollama)
- **Embeddings**: `mxbai-embed-large` (via Ollama)
- **Orchestration**: LangChain
- **Vector Database**: ChromaDB
- **Data Handling**: Pandas

---

## 📋 Prerequisites

1. **Ollama**: Download and install from [ollama.com](https://ollama.com/).
2. **Download Models**:
   ```bash
   ollama pull llama3.2
   ollama pull mxbai-embed-large
   ```
3. **Python 3.9+**: Ensure you have Python installed.

---

## 📥 Installation

1. **Clone the repository** (or navigate to the project directory).
2. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

---

## 🏃 Getting Started

To start the interactive agent, simply run:

```bash
python main.py
```

### Example Questions to Ask:

- "What do people think about the gluten-free options?"
- "Is the service generally fast or slow?"
- "Which pizza is recommended for someone who likes spicy food?"
- "Are there any complaints about cleanliness?"

---

## 📂 Project Structure

- `main.py`: The entry point for the application. Handles the user input loop and RAG chain orchestration.
- `vector.py`: Handles data loading from CSV, document chunking, embedding generation, and vector store management.
- `realistic_restaurant_reviews.csv`: The dataset containing ~124 customer reviews with ratings and dates.
- `chroma_langchain_db/`: Local directory where the embedded vector data is persisted.
- `requirements.txt`: Python package dependencies.

---

## 🧠 How it Works

1. **Data Loading**: `vector.py` reads the `realistic_restaurant_reviews.csv` file using Pandas.
2. **Indexing**: Documents are created from each review (Title + Body) and stored in ChromaDB using Ollama embeddings.
3. **Retrieval**: When you ask a question, the system searches the vector store for the top 5 most relevant reviews.
4. **Generation**: The retrieved reviews and your question are sent to the `llama3.2` model with a custom prompt, ensuring the answer is based _only_ on the provided reviews.

---

## 📄 License

MIT License - feel free to use this for your own local AI experiments!
