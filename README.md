# Self-Correcting RAG Framework for Industrial Intelligence
### Modular NLP Pipeline with LangGraph, Qdrant, & Multi-LLM Orchestration

[![Python](https://img.shields.io/badge/Python-3.12-blue.svg)](https://www.python.org/)
[![Gradio](https://img.shields.io/badge/UI-Gradio-orange.svg)](https://gradio.app/)
[![NLP](https://img.shields.io/badge/Specialization-NLP-blueviolet.svg)](#)
[![License](https://img.shields.io/badge/License-Apache_2.0-red.svg)](https://opensource.org/licenses/Apache-2.0)

A high-performance **Self-Correcting Retrieval-Augmented Generation (RAG)** framework engineered for high-stakes industrial environments. This system is designed to eliminate AI hallucinations by implementing a multi-stage verification loop, ensuring responses are strictly grounded in technical documentation, safety protocols, and domain-specific data.

## 🧠 Practitioner's Note: NLP & Deep Learning Integration
As an **NLP-specialized Data Science practitioner**, I developed this system to address the "trust gap" in Large Language Models. While this implementation uses hosted LLMs via OpenRouter for reasoning, the architecture is designed to be **Deep Learning Agnostic**. 

Researchers and developers can extend this framework using:
* **PyTorch / Hugging Face Transformers:** Deploy and fine-tune local models like **Llama-3** or **Mistral** for offline industrial environments.
* **TensorFlow / Keras:** Integrate custom deep learning heads for query intent classification or sentiment-based routing.
* **Domain-Specific Embeddings:** Swap the embedding layer for **SciBERT** or custom-trained variants to handle hyper-specialized technical nomenclature.

---

## 🚀 Key Features

* **Self-Correction Logic (LangGraph):** Unlike linear RAG pipelines, this system utilizes graph-based orchestration to "grade" retrieved context. If information is deemed irrelevant, the system triggers a re-write or re-search loop rather than generating a hallucinated response.
* **Industrial Safety Guardrails:** Hardcoded logic layers prevent the disclosure of sensitive proprietary data (such as internal recipes) while maintaining high utility for end-user technical support.
* **High-Fidelity Parsing (IBM Docling):** Specialized extraction that preserves the integrity of complex data tables and safety values from PDFs—critical for industrial compliance.
* **Interactive Gradio UI:** A production-ready web interface designed for rapid testing, session management, and live performance monitoring.

## 🛠️ Technical Stack

| Component | Technology |
| :--- | :--- |
| **Framework** | LangChain & LangGraph (State Machine Logic) |
| **User Interface** | Gradio (Interactive Web UI) |
| **Vector DB** | Qdrant Cloud (Vector Similarity Search) |
| **Embeddings** | Nomic-Embed-Text-v1.5 (High-Dimensional Semantic Mapping) |
| **LLM Reasoning** | Elephant-Alpha (100B) / Llama-3 (Switchable via OpenRouter) |
| **Data Extraction** | IBM Docling (Markdown-based PDF Analysis) |

---

## 🏗️ System Architecture

1.  **Ingestion Pipeline:** Raw technical PDFs/Docs → IBM Docling (Markdown Conversion) → Semantic Recursive Chunking.
2.  **Vector Space:** Text Chunks → Nomic Embedder → Indexed in Qdrant Cloud.
3.  **The Self-Correction Loop (The "Brain"):**
    * **Step A:** User Query → Semantic Search.
    * **Step B (The Grader):** Evaluates if the Top-K results actually answer the query.
    * **Step C (The Logic):** If "No," it re-frames the question or signals a search failure. If "Yes," it proceeds to generation.
4.  **Interactive Layer:** The finalized, verified response is streamed to the Gradio UI.

---

## 💻 Personal Project Deployment (Gradio)

This repository is optimized for personal project use cases. You can launch the interactive UI locally to test with your own datasets:

```python
# Launch the Gradio UI after configuring your .env
python app.py
