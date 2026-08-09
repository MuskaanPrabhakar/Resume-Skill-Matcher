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

## Workflow

```text
Google Drive Folder
        ↓
   PDF / TXT Files
        ↓
   Document Loading
        ↓
   Text Chunking
        ↓
HuggingFace Embeddings
        ↓
    ChromaDB
        ↓
   Similarity Search
        ↓
   Matching Resumes
