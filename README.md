# RAG com Os Sertões

Projeto desenvolvido para comparar três estratégias de *Retrieval-Augmented Generation* (RAG) usando o livro **Os Sertões**, de Euclides da Cunha.

## Objetivo

Construir e avaliar três abordagens de RAG para responder perguntas sobre a obra:

1. Naive RAG
2. Parent RAG
3. Rerank RAG

O documento-base é o livro *Os Sertões*, disponível em:  
https://fundar.org.br/wp-content/uploads/2021/06/os-sertoes.pdf

## Estrutura do projeto

```text
notebooks/
├── 01_naive_rag.ipynb
├── 02_parent_rag.ipynb
└── 03_rerank_rag.ipynb

data/
└── os-sertoes.pdf
```

## Abordagens implementadas

### 1. Naive RAG

É a abordagem mais simples. O PDF é dividido em pequenos trechos (*chunks*), transformado em embeddings e armazenado em um banco vetorial. Quando uma pergunta é feita, o sistema busca os trechos mais parecidos e os envia para o modelo gerar a resposta.

### 2. Parent RAG

Mantém dois níveis de texto: trechos pequenos para realizar a busca e trechos maiores, chamados de documentos-pai, para fornecer mais contexto ao modelo. Isso tende a evitar respostas baseadas em partes isoladas do livro.

### 3. Rerank RAG

Após recuperar os trechos inicialmente mais relevantes, um modelo de reranking reorganiza esses resultados. Assim, os trechos mais úteis para responder à pergunta têm prioridade no contexto enviado à LLM.

## Tecnologias

- Python
- Jupyter Notebook
- LangChain
- OpenAI API
- ChromaDB
- PyPDF
- Git e GitHub

## Execução

1. Instale as dependências descritas em `requirements.txt`.
2. Configure a variável de ambiente `OPENAI_API_KEY`.
3. Baixe o PDF para a pasta `data/`.
4. Execute os notebooks na ordem desejada.

> A chave da OpenAI não deve ser enviada ao GitHub.
