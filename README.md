# Article-Retrieval-System-RAG

### Overview

This project aims to develop an Article Retrieval System powered by advanced natural language processing (NLP) techniques. The system indexes articles from the "1300 Towards Data Science Medium Articles" dataset available on Kaggle and implements a Retrieval Augmented Generation (RAG) mechanism for effective retrieval of article fragments in response to user queries.

### Strategy

The strategy of the program is as follows:

1. **Data Preparation:** Load the dataset into a DataFrame and format it using DataFrameLoader.

2. **Indexing:** Divide articles into chunks using RecursiveCharacterTextSplitter for efficient indexing.

3. **Embeddings Extraction:** Extract embeddings from the articles using Cohere's embed-multilingual-light-v3.0 model for semantic similarity search.

4. **Vector Store Creation:** Create a vector store using Chroma to store the embeddings for fast retrieval.

5. **User Interaction:** Implement a function, ask_llm, to query the OpenAI chat completion service using the LLM model "llama2" for generating responses to user questions.

### Setup Guide

1.  Clone the repository to your local machine:

        git clone <repository-url>

2.  Navigate to the project directory.
3.  Install the required dependencies by running:

        pip install -r requirements.txt

4.  Obtain a Cohere API key from [Cohere](https://cohere.com/).
5.  Add your Cohere API key to the `config.env` file:

        COHERE_API_KEY=<your-cohere-api-key>

6.  Download and install Ollama from [Ollama website](https://ollama.com/download).

7.  Run all the cells.

8.  Interact with the system by asking questions and exploring retrieved article fragments.

### Examples of usage

```python
question = "What is Random Forest?"
docs = vectordb.similarity_search(question,k=3)
display_search_results(question, docs)
```

In this example, a query is sent to the Article Retrieval System asking "What is Random Forest?" using the `similarity_search` method. This method retrieves the top 3 most relevant article fragments from the dataset based on the similarity of their content to the given question. The retrieved fragments are then displayed using the `display_search_results` function.

```python
ask_llm("What is Random Forest?")
```

Here, the `ask_llm` function is used to generate responses to the question "What is Random Forest?" using the Large Language Model (LLM) model "llama2". The function first retrieves relevant document fragments using the Article Retrieval System's similarity search mechanism. It then merges these fragments into a single text and sends it as a message to the OpenAI chat completion service. Finally, the function iterates over the response chunks from the service and prints the generated content.

> **For more information please read `report.pdf` file.**
