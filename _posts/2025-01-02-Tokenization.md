---
layout: post
title: "Tokenization"
date: 2025-01-02 10:00:00 +0000
categories: [Concept]
tags: [Tokenization]
---

# A Comprehensive Guide to Tokenization
Tokenization is a foundational step in Natural Language Processing (NLP). Whether you’re building a sentiment analysis model, a text classifier, or a large language model (LLM) like GPT, understanding tokenization is essential. 

In this article, we’ll explore what tokenization is, why it matters, the different approaches, and best practices in modern NLP pipelines.


## Understanding the ML Workflow
![AI_Agents](/articles_img/Tokenization/ML_Flow.png){: style="width: 90%;" }

## What Is Tokenization?
Tokenization is the process of breaking a piece of text (e.g., a sentence or paragraph) into smaller units called “tokens.” Each token can be:

- A word (e.g., “cat”),
- A subword (e.g., “cat” split into “c” and “at”),
- A character (e.g., “c”, “a”, “t”), or
- Punctuation symbols (e.g., “,”, “.”, “!”).

The goal of tokenization is to transform raw text (which is inherently unstructured data) into a structured form that a machine learning model can interpret and process.

## Types of Tokenization
Tokenization approaches range from simple whitespace splitting to sophisticated subword tokenizers that reduce out-of-vocabulary (OOV) issues. Let’s look at some common methods:

### Word-level Tokenization
A word-level tokenizer splits text using spaces and punctuation marks. For instance, the sentence:

"I love NLP." becomes tokens like: ["I", "love", "NLP", "."]

- Pros: Simple to implement, intuitive.
- Cons: Large vocabularies, struggles with “unknown” words, morphological variations, and languages that don’t use spaces.

### Subword Tokenization (BPE / WordPiece / SentencePiece)

In modern NLP—especially for Transformers and LLMs—subword tokenization is dominant. It strikes a balance between word-level and character-level approaches by splitting rare words into more frequent “subwords”:

- Byte-Pair Encoding (BPE): Greedily merges character pairs to form subwords.
- WordPiece: Used by models like BERT; merges subwords based on maximum likelihood of subword sequences.
- SentencePiece: A newer approach that can handle whitespace uniformly, commonly used by T5 and XLNet.

For example, with subword tokenization (using WordPiece):

"unaffordable"  → ["un", "##aff", "##ord", "##able"]
(Note: "##" is sometimes used in WordPiece to indicate subword continuity.)

- Pros: Reduces the size of the vocabulary while also dealing gracefully with unknown or rare words (OOV words become a combination of subwords).
- Cons: Slightly more complex to implement, requires specific tokenization libraries.

### Character-level Tokenization
Here, the text is split into individual characters, including punctuation and special symbols. For example:

"Cat" → ["C", "a", "t"]

- Pros: Handles any language, no OOV issues at the character level.

- Cons: Longer sequence lengths, can be harder to learn meaningful semantic relationships solely from individual characters.

### Byte-level Tokenization
Popularized by GPT-2 and GPT-3, byte-level tokenization (e.g., Byte-Level BPE) treats text as a stream of raw bytes, effectively capturing every character. This approach can handle nearly all text variations, special Unicode characters, and emojis.

## Tools & Libraries
- Hugging Face Transformers: Provides state-of-the-art tokenizers (e.g., BERT, GPT, RoBERTa) and includes the tokenizers library for custom training.
- NLTK (Natural Language Toolkit): Offers basic word and sentence tokenizers.
- SpaCy: Efficient, production-ready tokenization for multiple languages.
- SentencePiece: Framework for language-independent subword tokenization.
- Byte-Pair Encoding (BPE): Often implemented in the above libraries or in standalone scripts.

## Why Do We Need Tokenization?

| Reason                             | Explanation                                                                                                                             |
|------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| **Model Input**                    | Machine learning and deep learning models operate on numerical data. Tokenization is the step that converts raw text into numerical IDs. |
| **Vocabulary Building**            | Tokenization determines which tokens appear in your vocabulary, influencing embedding sizes and handling of unseen words.               |
| **Handling Language Variations**   | Helps manage text in languages with no spaces (Chinese, Japanese) and accommodates morphological differences (e.g., plurals, tenses).   |
| **Reducing Out-of-Vocabulary**     | Subword tokenization in particular reduces the OOV problem by splitting rare or unknown words into smaller, more frequent units.         |
| **Preprocessing Efficiency**       | Ensures consistent tokens for the model, speeding up learning and improving performance.                                                |


