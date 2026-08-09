# Resume-Skill-Matcher
A Google Colab project that uses HuggingFace embeddings and ChromaDB to perform semantic similarity search on resumes stored in Google Drive.

The system processes PDF and TXT resumes, converts their contents into vector embeddings, and retrieves the most relevant resumes based on a user's job-skill query.

## Features

- Load PDF and TXT resumes from a Google Drive folder
- Split documents into smaller chunks
- Generate vector embeddings using HuggingFace
- Store embeddings in ChromaDB
- Perform semantic similarity search
- Upload new resumes and add them to the vector store
- Delete resumes and their corresponding vector embeddings
- Retrieve the top 5 matching resumes for a given query

## Technologies Used

- Python
- Google Colab
- LangChain
- HuggingFace Sentence Transformers
- ChromaDB
- PyPDF

## Embedding Model

This project uses:

`sentence-transformers/all-MiniLM-L6-v2`

The model converts document chunks and search queries into numerical vector representations for semantic similarity search.

## How It Works

### 1. Load Documents

PDF and TXT files are loaded from a Google Drive folder.

- PDF → `PyPDFLoader`
- TXT → `TextLoader`

The documents are then split into smaller chunks using `RecursiveCharacterTextSplitter`.

### 2. Create Vector Store

The document chunks are converted into embeddings and stored in ChromaDB.

```text
Document Chunks
      ↓
HuggingFace Embeddings
      ↓
ChromaDB
```
### 3. Upload a Resume

A new PDF or TXT resume can be uploaded through Google Colab.

The file is:

1. Saved to the selected folder
2. Loaded and split into chunks
3. Converted into embeddings
4. Added to the existing ChromaDB vector store

### 4. Delete a Resume

A resume can be deleted by providing its file path.

The corresponding embeddings are removed from ChromaDB and the original file is deleted.

### 5. Search

A job requirement query is compared against the stored document embeddings.

The system retrieves the top 5 most relevant resume chunks using ChromaDB similarity search.

Example Query
-------------

    Python developer with AWS and Docker skills

The system returns the most relevant resumes along with their similarity scores and file paths.

Requirements
------------

Install the required packages in Google Colab:

Bash

    pip install langchain-community pypdf
    pip install langchain-huggingface
    pip install langchain-chroma

Usage
-----

1. Open the notebook in Google Colab.
2. Mount your Google Drive.
3. Provide the path to the folder containing resumes.
4. Load and chunk the documents.
5. Create the ChromaDB vector store.
6. Upload or delete resumes as needed.
7. Enter a job-skill query.
8. View the top matching resumes.

Notes
-----

*   Designed to run in Google Colab.
*   Resumes are stored in Google Drive.
*   Supports PDF and TXT files.
*   HuggingFace is used for generating embeddings.
*   ChromaDB is used for vector similarity search.
*   The current implementation is notebook-based and does not include a web frontend.

Future Improvements
-------------------

*   Add a web-based frontend
*   Automatically rebuild/synchronize the vector store after document changes
*   Rank complete resumes instead of individual chunks
*   Add richer candidate matching and filtering
*   Add metadata-based filtering for skills, experience, location, etc.
