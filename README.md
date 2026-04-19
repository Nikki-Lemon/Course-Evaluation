# Course Evaluation

This is an intelligent course recommendation and planning tool designed specifically for CMU students. By leveraging Large Language Models (LLMs) and Machine Learning, the system helps students align their academic choices with specific career goals through a Retrieval-Augmented Generation (RAG) chatbot and a specialized career-tagging classification model.

This project was developed as the final project for the **95-891 Introduction to Artificial Intelligence** course at Carnegie Mellon University.

## 🚀 Key Features

* **Career-Aware Course Tagging**: A multi-label classification model that automatically assigns industry and career tags (e.g., *Product Management*, *Software Engineering*, *Data Science*) to courses based on their descriptions.
* **Hybrid RAG Chatbot**: An interactive chatbot powered by **Groq (Llama 3.3)** and **ChromaDB**. It uses hybrid search (Vector + Keyword) and cross-encoder re-ranking to provide evidence-based answers.
* **Conflict-Aware Scheduling**: Backend logic that parses complex course schedules and filters recommendations based on the student's available time slots.
* **Chrome Extension UI**: A seamless side-panel interface that allows students to search for courses and get AI advice directly within their browser while navigating academic portals.

## 🏗️ System Architecture

The project consists of three integrated layers:
1.  **AI Engine (Jupyter Notebook)**: Handles data cleaning, embedding generation, and the training of the Multi-label Logistic Regression model for career tagging.
2.  **Backend API (Python/FastAPI)**: Orchestrates the RAG pipeline, including vector retrieval from ChromaDB and inference via Groq.
3.  **Frontend (Chrome Extension)**: Bridges the user experience by providing a side-panel interface that communicates with the local/cloud backend.

## 🛠️ Tech Stack

* **LLM**: Llama 3.3 70B (via Groq Cloud)
* **Vector DB**: ChromaDB
* **Embeddings**: `all-MiniLM-L6-v2` (Sentence-Transformers)
* **Re-ranking**: `cross-encoder/ms-marco-MiniLM-L-6-v2`
* **Backend**: Python (FastAPI / Flask)
* **ML Libraries**: Scikit-learn, Pandas, NumPy
* **Frontend**: JavaScript (Chrome Extension API)

## 📦 Installation & Setup

### Prerequisites
- Python 3.10+
- A [Groq API Key](https://console.groq.com/)

### 1. Backend Setup
```bash
# Clone the repository
git clone [https://github.com/your-username/course-pilot.git](https://github.com/your-username/course-pilot.git)
cd course-pilot

# Install dependencies
pip install -r requirements.txt

# Configure environment variables
echo "GROQ_API_KEY=your_actual_key_here" > .env

# Run the backend proxy
python llm-proxy.py
```

### 2. Extension Installation
1. Open Chrome and navigate to `chrome://extensions/`.
2. Enable **"Developer mode"** in the top right corner.
3. Click **"Load unpacked"** and select the extension folder from this repository.
4. Click the extension icon to open the Course Pilot side panel.

## 📊 Evaluation & Results
The system is evaluated across two dimensions:

* **Classification Performance**: The career-tagging model is assessed using F1-score and Precision-Recall metrics on labeled CMU course data.
* **RAG Fidelity**: We utilize grounded retrieval to ensure the chatbot provides specific course IDs and citations, minimizing hallucinations.

## 👥 Team Members (Group 24)
* **Shiyu Liu**
* **Kaitong Guan**
* **Nikki Chen**
