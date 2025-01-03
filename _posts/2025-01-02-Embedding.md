---
layout: post
title: "From Tokenization to Embeddings: Building the Foundation of NLP"
date: 2025-01-02 10:00:00 +0000
categories: [Concept, NLP]
tags: [Embeddings]
---

> Read about [Tokenization](https://duckduckgo.com)

In modern Natural Language Processing (NLP), two core components often shape the performance of your models: Tokenization and Embeddings. In an earlier article, we explored how tokenization transforms raw text into discrete tokens. Here, we’ll build upon that foundation to see how embeddings map those tokens into meaningful numerical representations. 


## At which stage in the ML Workflow does Embeddings typically occur ? 
![AI_Agents](/articles_img/Tokenization/ML_Flow.png){: style="width: 90%;" }




Summary
Tokenization
Splits raw text into discrete tokens (e.g., words, subwords, characters).
This step typically happens outside or before the model architecture. You end up with a sequence of token IDs.

Embedding
Maps each token ID to a dense vector in a continuous space.
Often done inside the model’s “embedding layer” (especially in transformer-based LLMs) or via external libraries (e.g., pretrained word embeddings like GloVe, Word2Vec).

Converting tokens to IDs allows the model to look up an embedding vector for each token ID or use the IDs directly in classical ML workflows.