# 🏥 Medical RAG (Retrieval-Augmented Generation)

A robust Retrieval-Augmented Generation (RAG) system tailored for medical data. This project features a high-performance **FastAPI** backend for orchestration, a user-friendly **Streamlit** frontend for interactive chatting, and an automated **FAISS** vector indexing pipeline for fast similarity search across medical datasets.

---

## 📂 Project Structure

\`\`\`text
medical-rag/
│
├── app.py              # Streamlit frontend (User Interface)
├── ingest.py           # Data ingestion & FAISS index creation
├── rag_pipeline.py     # Core RAG logic (Embeddings, Retrieval, LLM Integration)
├── main.py             # FastAPI backend (API routing & endpoints)
├── requirements.txt    # Python dependencies
├── Dockerfile          # Containerization instructions
├── README.md           # Project documentation
├── .env                # Environment variables (API keys, config)
│
├── .github/
│   └── workflows/
│       └── ci-cd.yml   # GitHub Actions CI/CD pipeline
│
└── data/               # Raw and formatted dataset directory
    ├── chatdoctor5k.json
    └── format_dataset.csv
\`\`\`

---

## ✨ Features

* **Interactive UI:** Streamlit-based web interface for real-time medical Q&A.
* **FastAPI Backend:** High-speed asynchronous API serving the RAG pipeline.
* **Vector Search:** FAISS integration for lightning-fast document retrieval.
* **Data Ingestion:** Automated scripts to process, chunk, and index raw JSON and CSV medical datasets.
* **Dockerized:** Ready for deployment anywhere with an included Dockerfile.
* **CI/CD Pipeline:** Automated testing and deployment via GitHub Actions.

---

## 🚀 Getting Started

### 1. Prerequisites
Ensure you have the following installed on your machine:
* Python 3.9+
* Docker (optional, for containerized deployment)

### 2. Installation
Clone the repository and install the required dependencies:

\`\`\`bash
git clone https://github.com/Shreesanyog/Medical-bot-Rag-Pipeline.git
cd Medical-bot-Rag-Pipeline
python -m venv venv
source venv/bin/activate  # On Windows use: venv\Scripts\activate
pip install -r requirements.txt
\`\`\`

### 3. Environment Variables
Create a `.env` file in the root directory and add your API keys (e.g., OpenAI, HuggingFace) and configurations:

\`\`\`env
OPENAI_API_KEY=your_api_key_here

\`\`\`

---

## 🧠 Usage Instructions

### Step 1: Ingest Data & Build Vector Index
Before running the application, you must process the medical datasets in the `/data` folder and build the FAISS index:

\`\`\`bash
python ingest.py
\`\`\`
*Note: This will read `chatdoctor5k.json` and `format_dataset.csv`, create embeddings, and save the vector store locally.*

### Step 2: Start the FastAPI Backend
Launch the backend server to expose the RAG API endpoints:

\`\`\`bash
uvicorn main:app --reload --host 0.0.0.0 --port 8000
\`\`\`
*The API documentation will be available at `http://localhost:8000/docs`.*

### Step 3: Start the Streamlit Frontend
In a new terminal window, launch the user interface:

\`\`\`bash
streamlit run app.py
\`\`\`
*The app will automatically open in your browser at `http://localhost:8501`.*

---

## 🐳 Docker Deployment

1. Build the image

2. Run the container

---

## ⚙️ CI/CD (GitHub Actions)

This project uses GitHub Actions for Continuous Integration and Continuous Deployment. 
The pipeline is defined in `.github/workflows/ci-cd.yml` and is triggered on pushes to the `main` branch. It automatically:
* Sets up the Python environment.
* Installs dependencies.
* Runs automated tests (if configured).
* Builds the Docker image.

---
