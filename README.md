# contract qa assistant

## summary

This repository implements a **retrieval‑augmented question answering assistant** for federal contracting guidance.  It uses natural‑language understanding and document retrieval to provide context‑aware answers to questions about the Federal Acquisition Regulation (FAR), the Defense FAR Supplement (DFARS) and related agency directives.

### data science

- **Text preprocessing and chunking** – cleaned and segmented FAR/DFARS provisions into semantically meaningful passages for retrieval and ranking.
- **Embedding selection** – evaluated embedding models (sentence‑transformers, OpenAI embeddings) on legal text, measuring semantic coverage and retrieval precision.
- **Retrieval experiments** – tuned vector search algorithms and distance metrics to identify the best ranking configuration for legal queries.
- **Evaluation** – designed experiments to measure retrieval accuracy, answer relevance and latency.

### ml engineering

- **Modular API service** – implemented a FastAPI service with endpoints for embedding queries, retrieving relevant passages and synthesizing answers.
- **Vector store integration** – integrated a FAISS/Chroma vector database for efficient similarity search.
- **Deployment** – containerized the service with a multi‑stage `Dockerfile`; configured GitHub Actions for linting, tests and automated container builds.
- **UI layer** – provided a Streamlit front‑end that calls the API and displays retrieval results and citations.

### repository structure

| path                 | purpose                                                                           |
|---------------------|------------------------------------------------------------------------------------|
| `data/`             | Sample documents and embeddings for testing.                                       |
| `src/`              | Python modules for preprocessing, embedding, retrieval and API code.               |
| `requirements.txt`  | Python dependencies.                                                               |
| `Dockerfile`        | Multi‑stage build for deployment.                                                |
| `.github/workflows/`| CI scripts for linting and container builds.                                       |
| `README.md`         | Project overview and instructions.                                                 |

### running locally

Clone the repository and install dependencies:

```bash
git clone https://github.com/Fam12345/contract-qa-assistant.git
cd contract-qa-assistant
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

Start the API using Uvicorn, specifying the module path as appropriate:

```bash
uvicorn src.api:app --reload
```

Optionally launch the Streamlit app in another terminal:

```bash
streamlit run src/app.py
```

The assistant will accept a question about contracting regulations, retrieve relevant paragraphs and generate an answer with citations.
