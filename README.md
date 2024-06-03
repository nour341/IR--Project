
---

# Information Retrieval (IR) Project

This project implements an Information Retrieval (IR) system with offline preprocessing, indexing, and clustering stages, and an online query processing stage. The system is designed to efficiently handle large datasets and provide relevant document retrieval based on user queries.

## Table of Contents
1. [Project Structure](#project-structure)
2. [Offline Stage](#offline-stage)
    - [Preprocessing](#preprocessing)
    - [TF-IDF Vectorization](#tf-idf-vectorization)
    - [Indexing](#indexing)
    - [Clustering](#clustering)
3. [Online Stage](#online-stage)
    - [Query Processing](#query-processing)
4. [Installation](#installation)
5. [Usage](#usage)
6. [Contributing](#contributing)
7. [License](#license)

## Project Structure

- `data/`: Directory containing the dataset.
- `offline/`: Directory containing scripts for the offline stage.
  - `preprocess.py`: Script for text preprocessing.
  - `vectorize.py`: Script for TF-IDF vectorization.
  - `index.py`: Script for FAISS indexing.
  - `cluster.py`: Script for clustering.
- `online/`: Directory containing scripts for the online stage.
  - `query.py`: Script for processing and retrieving queries.
- `utils/`: Utility scripts for common functions.
- `README.md`: Project documentation.

## Offline Stage

The offline stage includes preprocessing the dataset, vectorizing the documents using TF-IDF, creating an index using FAISS, and performing clustering for efficient retrieval.

### Preprocessing

1. **Text Normalization**: Convert text to lowercase, remove special characters and digits.
2. **Tokenization**: Split text into individual tokens (words).
3. **Stopword Removal**: Remove common stopwords to reduce noise.
4. **Lemmatization**: Convert words to their base form.

### TF-IDF Vectorization

1. **Fit TF-IDF Vectorizer**: Fit the vectorizer on the document corpus to learn the vocabulary and calculate term frequencies.
2. **Transform Documents**: Convert the processed documents into TF-IDF vectors.

### Indexing

1. **Create FAISS Index**: Initialize a FAISS index for efficient similarity search.
2. **Add Vectors to Index**: Add TF-IDF vectors to the FAISS index with document IDs for reference.

### Clustering

1. **Perform Clustering**: Use KMeans clustering to group similar documents together.
2. **Save Cluster Model**: Save the trained clustering model for use in the online stage.

## Online Stage

The online stage involves processing user queries, searching the FAISS index, and retrieving the most relevant documents.

### Query Processing

1. **Preprocess Query**: Apply the same preprocessing steps as for documents (normalization, tokenization, stopword removal, lemmatization).
2. **Vectorize Query**: Transform the preprocessed query into a TF-IDF vector using the fitted vectorizer.
3. **Search Index**: Use the FAISS index to find the top-k most similar documents to the query vector.
4. **Retrieve Documents**: Retrieve and rank the document IDs based on similarity scores.
5. **Calculate Metrics**: Evaluate the retrieval performance using metrics like MAP, MRR, Precision@10, and Recall.
