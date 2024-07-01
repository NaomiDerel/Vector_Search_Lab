# Vector_Search_Lab

Vector Search assignment, as part of the "Data Analysis and Visualization" Lab course.

## Part 1 - Faiss Index Analysis

In this part, we focused on analyzing the performance of the Faiss library, compared to the brute-force search method. We explored the effects on dimensionality, number of vectors and other hyper-parameters on the search time.

## Part 2 - Implementing an Index

In this part, we implemented our own index, based on the idea behind the IVF algorithm. We based our implementation on dimension reduction (with PCA) and clustering (with KMeans) to create a division of the vectors space into clusters, and then search only in the relevant clusters exhaustively. 

By exploiting the unique properties of our data, we managed to recieve a significantly higher $recall@10$ score over the LSH implementation, while maintaining a fast search time.

## Part 3 - Implementing RAG

In this part, we implemented the RAG pipeline for a QA model, aiming to improve the performance of a given LLM model.

Necessary components for this implementation are:

- The Pinecone VectorDB API, a powerful and easy-to-use vector database to store and search the database for the QA model.
- The Cohere API, a free access LLM model to generate the answers. We chose to use the $\texttt{'all-MiniLM-L6-v2'}$ model.
- The SQuAD dataset from huggingface, which we used to evaluate the improvement with the RAG pipeline.

The RAG pipeline consists of the following steps:
1. Document reading and preprocessing.
2. Embedding generation and insertion into Pinecone VectorDB.
3. Retrieval of relevant documents for query.
4. Generating answers to given questions using an augmented prompt with the retrieved documents.

Anecdotal measurements on 50 examples show that the RAG pipeline improves the performance of the LLM model, both in run-time and in estimated correctness.