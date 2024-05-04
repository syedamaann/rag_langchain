# Langchain RAG application

## Overview

This Python-based Retrieval Augmented Generation (RAG) application enables users to interactively ask questions about a set of PDF documents using natural language queries. It is designed to work with a variety of source materials, with a current focus on three specific books: "Coming Wave," "Genius Makers," and "Clear Thinking." Users can input queries such as, "What are the main arguments in Genius Makers?" and the application will provide contextually relevant responses drawn directly from the PDFs.

## Key Features

- **Natural Language Queries:** Ask questions in plain English to retrieve information from your PDF documents.
- **Local and Cloud LLM Support:** Uses the Llama3 model by default but can be configured to use other models including those hosted on OpenAI's platform.
- **Dynamic Data Embedding:** Embeddings generated through Langchain, initially configured with OpenAI but adjustable to other services as per user requirements.
- **Vector Database Integration:** Utilizes ChromaDB for efficient data storage and retrieval, allowing for the addition of new data without full database rebuilds.
- **Real-Time Updates:** Supports real-time updating and adding of PDF documents into the system without downtime.
- **Extensible and Configurable:** Easily adaptable for different datasets, embedding functions, and LLM models.

## System Architecture

1. **Data Source Preparation:**
   - Load PDF documents ("Coming Wave," "Genius Makers," "Clear Thinking") into the system.
   - Use Langchain's document loaders to parse and prepare the data.

2. **Data Embedding:**
   - Convert text data into embeddings using OpenAI’s models via Langchain integration.
   - Store these embeddings in ChromaDB, tagged with unique identifiers for each text chunk (combining source path, page number, and chunk number).

3. **Query Processing:**
   - User inputs a natural language query.
   - The query is converted into an embedding and matched against the database to find the most relevant text chunks.
   - These chunks are compiled into a prompt for the LLM.

4. **Response Generation:**
   - The Llama3 model (or a model of your choice) processes the compiled prompt to generate a human-like response.
   - The application formats the response and cites the source material.

5. **Continuous Learning and Updating:**
   - New documents can be added to the system dynamically.
   - The database can be updated with new or changed content without requiring a full rebuild.

## Dependencies

- **Python:** Version 3.8 or higher.
- **Langchain:** For handling document loading and embedding integration.
- **ChromaDB:** Used for embedding-based database management.
- **Ollama (optional):** For managing local LLM deployments.

## Installation and Setup

1. **Install Required Libraries:**
   ```bash
   pip install langchain chromadb ollama
   ```

2. **Configuration:**
   - Set up your environment with appropriate API keys and endpoints for OpenAI and ChromaDB.
   - Configure the LLM settings in the application to point to either a local Ollama instance or an external LLM provider like OpenAI.

3. **Loading Data:**
   - Place the PDF files in the designated data folder.
   - Run the initial script to parse and embed the PDFs into ChromaDB.

4. **Running the Application:**
   - Start the application server.
   - Use the web interface or API endpoint to start querying your PDFs.

## Usage

Install dependencies.

```python
pip install -r requirements.txt
```

Create the Chroma DB.

```python
python populate_database.py
```

Query the Chroma DB.

```python
python query_data.py "What are the main arguments in Genius Makers?"
```

You'll also need to set up an OpenAI account (and set the OpenAI key in your environment variable) for this to work.

