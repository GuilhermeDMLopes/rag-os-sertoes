# RAG with *Os Sertões*

This project compares three Retrieval-Augmented Generation (RAG) strategies using *Os Sertões*, by Euclides da Cunha.

## Goal

Build and evaluate three RAG approaches that answer questions about the book:

1. Naive RAG
2. Parent RAG
3. Rerank RAG

The source document is available at:  
https://fundar.org.br/wp-content/uploads/2021/06/os-sertoes.pdf

## Project structure

```text
notebooks/
├── 01_naive_rag.ipynb
├── 02_parent_rag.ipynb
└── 03_rerank_rag.ipynb

data/
└── os-sertoes.pdf
```

## Implemented approaches

### 1. Naive RAG

The PDF is split into small chunks, which are converted into embeddings and stored in a vector database. For each question, the system retrieves the most similar chunks and provides them to the language model to generate an answer.

### 2. Parent RAG

This approach uses two text levels: small chunks for retrieval and larger parent documents for the language model context. It helps avoid answers based only on isolated passages from the book.

### 3. Rerank RAG

After the initial retrieval step, a reranking model reorganizes the returned chunks. The most useful passages are prioritized before the final context is sent to the language model.

## Technologies

- Python
- Jupyter Notebook
- LangChain
- OpenAI API
- ChromaDB
- PyPDF
- Git and GitHub

## API credits and keys

Running the notebooks requires active API credits and valid keys.

| Approach | OpenAI API | Cohere API |
| --- | --- | --- |
| Naive RAG | Required for embeddings and answers | Not required |
| Parent RAG | Required for embeddings and answers | Not required |
| Rerank RAG | Required for embeddings and answers | Required for reranking |

Create a `.env` file in the project root with both keys:

```text
OPENAI_API_KEY=your_openai_api_key
COHERE_API_KEY=your_cohere_api_key
```

The `.env` file is ignored by Git and must never be committed. ChatGPT subscriptions do not include OpenAI API credits; OpenAI and Cohere billing are managed separately by each provider.

## Running the project

1. Install the dependencies listed in `requirements.txt`.
2. Create the `.env` file with `OPENAI_API_KEY` and `COHERE_API_KEY`.
3. Download the PDF into the `data/` directory.
4. Run the notebooks in the desired order.

> Never commit the OpenAI API and COHERE_API_KEY keys to the repository.
