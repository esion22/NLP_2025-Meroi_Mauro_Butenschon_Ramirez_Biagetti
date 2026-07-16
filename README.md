# Multiple-Choice Question Answering on the RACE Dataset

This repository contains the project developed for the **Natural Language Processing** (NLP) course at **Politecnico di Milano** (Academic Year 2024-2025), taught by **Prof. Mark Carman**. 

The project focuses on building, evaluating, and fine-tuning various NLP models for multiple-choice reading comprehension using the **RACE** (Reading Comprehension Dataset from Examinations) dataset.

## Team Members
* Simone Mauro
* Lorenzo Meroi
* Theresa Butenschön
* Carlos Ramirez
* Alessandro Staffaroni Biagetti

---

## Project Overview
The project explores multiple NLP paradigms, from classical text classification and unsupervised topic modeling to transformer-based sentence search and fine-tuning large language models (LLMs) for multiple-choice Q&A. The dataset (RACE) comprises English reading comprehension passages and questions from Chinese middle and high school exams, presenting different difficulty levels.

The project implementation is divided into four main phases:

1. **Exploratory Data Analysis & Text Preprocessing**:
   * Analyzed vocabulary, sentence lengths, and POS distributions across exam levels.
   * Quantified passage complexity using the **Flesch Reading Ease Score**.
   * Addressed formatting anomalies (such as merged words without spaces) using the `WordNinja`/`SplitNinja` library.
   * Built a custom loose sentence splitter with regex and NLTK to handle missing spaces after punctuation.
2. **Classical Text Classifiers**:
   * Evaluated Bag-of-Words (BOW) representations to classify text difficulty (High School vs. Middle School).
   * Compared Naive Bayes (Multinomial & Complement), Support Vector Machines (SVM), Perceptron, and Logistic Regression with L1 regularization (which identified approximately 700 highly predictive words, such as *"opportunity"*).
3. **Embeddings, Semantic Search, and Topic Modeling**:
   * Trained custom Word2Vec (CBOW) embeddings and visualized word analogies.
   * Implemented keyword search (TF-IDF retrieval) and semantic search (Sentence Embeddings + **FAISS** indexing).
   * Uncovered underlying document topics using K-Means (TF-IDF vs. sentence embeddings) and contextual topic modeling using **BERTopic** (HDBSCAN clustering + KeyBERT representation tuning).
4. **Question Answering & Transformer Fine-Tuning**:
   * **Generative Prompting**: Evaluated **T5 FLAN** in zero-shot, one-shot, and few-shot scenarios. Zero-shot achieved the best results (69% accuracy), while few-shot suffered from prompt noise.
   * **Generative Fine-Tuning**: Fine-tuned **GPT-2** for Q&A, using **Cross-Encoder** semantic similarity to compress long contexts to only the sentences most relevant to the question.
   * **Discriminative Multiple Choice**: Fine-tuned **BERT-base-uncased** on all, middle-only, and high-only questions. Due to BERT's reasoning limitations on high-difficulty questions, the team trained the more advanced **DeBERTa-v3-base** model, achieving an accuracy of ~74%.

---

## Deliverables and Repository Structure
The deliverables are organized directly in the root directory:

* **[ExploringDataset.ipynb](./ExploringDataset.ipynb)**: Preprocessing, data cleaning, syllable and word counting, custom regex sentence splitting, POS tagging, and readability scoring.
* **[Classifying text.ipynb](./Classifying%20text.ipynb)**: Classical machine learning classifiers (Naive Bayes, SVM, Logistic Regression, Perceptron) for difficulty classification.
* **[Embeddings+Search+Clustering.ipynb](./Embeddings+Search+Clustering.ipynb)**: Semantic models, Word2Vec training, semantic search indexes (FAISS), K-Means topic clustering, and BERTopic modeling.
* **[FLAN&GPT-2_Q&A.ipynb](./FLAN&GPT-2_Q&A.ipynb)**: Generative Q&A experiments including T5 FLAN prompting, Cross-Encoder context extraction, and GPT-2 fine-tuning.
* **[Q&A_with_BERT_models.ipynb](./Q&A_with_BERT_models.ipynb)**: Fine-tuning BERT and DeBERTa-v3-base models for multiple-choice question answering, along with error analysis.
* **[CHAD_GPT_NLP_Project.html](./CHAD_GPT_NLP_Project.html)**: The compiled HTML document summarizing the code executions, visualizations, and results.
* **[NLP proj.mp4](./NLP%20proj.mp4)**: The video presentation demonstrating the project objectives, code walkthroughs, and key outcomes.
* **[LICENSE](./LICENSE)**: Project license file.

---

## License
This project is licensed under the terms of the license file in this repository.
