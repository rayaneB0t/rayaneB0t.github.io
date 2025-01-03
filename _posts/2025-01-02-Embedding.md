---
layout: post
title: "From Tokenization to Embeddings"
date: 2025-01-02 10:00:00 +0000
categories: [Concept, NLP]
tags: [Embeddings]
---
>**Reminder**: Proper tokenization is crucial before assigning embeddings. If you haven’t yet explored the basics of tokenization, be sure to review our [Tokenization Guide](https://rayaneb0t.github.io/posts/Tokenization/) to see how raw text becomes structured tokens.


## At which stage in the ML Workflow does Embeddings typically occur ? 
![Embeddings_Flow](/articles_img/NLP/Embeddings_Flow.png){: style="width: 90%;" }


## What is Embeddings ? 
Embeddings are at the heart of modern Natural Language Processing (NLP), bridging the gap between human language and machine-friendly data. In essence, embeddings transform words (or other text units) into numerical vectors. These vectors capture semantic and syntactic relationships, enabling machine learning models to interpret and generate language effectively.

## Embeddings and Tokenization
Before embeddings can be assigned, tokenization must split text into meaningful units (tokens). For example, the sentence:

> "I love cats!"

might become:

> Word-level tokens: ["I", "love", "cats", "!"]
> Subword tokens (WordPiece/BPE): ["I", "lo", "##ve", "cat", "##s", "!"]

Once tokenization is done, each token is converted into an ID (e.g., “love” → 101, “lo” → 102, etc.). 

Then these IDs are passed into an embedding layer which maps them to vectors. For example:

> ["I", "love", "cats", "!"] → [10, 11, 12, 13] (IDs)
- 10 → [0.12, -0.07, 0.44, ...] (embedding vector)
- 11 → [0.50, 0.99, 0.13, ...]
and so on...

*Key Point: Tokenization and embeddings work hand-in-hand to convert raw text into a numeric format suitable for neural networks.*

## Why Do We Need Embeddings?
- From Human-Readable: Text to Machine-Readable Data: Computers (specifically, neural networks) can’t process raw text in its natural, unstructured form. They need **numbers—vectors—on** which to perform mathematical operations. Embeddings offer a clever way to represent words or tokens as **real-valued vectors** so that similar words (e.g., cat and feline) end up closer in that **vector space**.

- Capturing Meaning & Context: A well-trained embedding might capture relationships and can encode conceptual meanings:
> king – man + woman ≈ queen


- Handling Large Vocabularies Efficiently: 
Traditionally, we could represent each unique word using a **“one-hot vector”**(a vector of length equal to the vocabulary size, with a 1 for the word index and 0 everywhere else). But if your vocabulary is in the tens or hundreds of thousands, that becomes huge and sparse.

Embeddings compress words into denser, lower-dimensional vectors (e.g., 300 or 768 dimensions), making them far more efficient in terms of both computation and memory.


## Types of Embeddings
- **Word2Vec** architecture learn embeddings where words that appear in similar contexts end up with similar vector representations.
    - **CBOW (Continuous Bag of Words)** predicts a target word given surrounding context.
    > CBOW: Context → Target word

    - **Skip-Gram** predicts surrounding context given the target word.
    > Skip-Gram: Target word → Context

- **GloVe (Global Vectors)** trains embeddings by factorizing a global word co-occurrence matrix (from large corpora).

- **FastText** built on Word2Vec but uses subword information (character n-grams).

- **Contextual Embeddings (ELMo, BERT, GPT)** : Embeddings that change depending on context.
    - **ELMo**: Uses bidirectional LSTMs to generate context-sensitive word embeddings.
    - **BERT / GPT**: Transformer-based models that produce embeddings which vary based on sentence context.

- **Sentence/Document Embeddings**: methods like **Sentence-BERT** or **Doc2Vec** produce a single embedding for an entire sentence or document.


<!-- ## Summary -->
