# PDF-Based Question Answering (Scientific & Biomedical Domains)

This project implements a Question Answering (QA) system for **scientific** and **biomedical** domain PDFs using transformer-based models like **SciBERT** and **Bio-ClinicalBERT**. It handles long documents, creates curated QA datasets, and extracts accurate answers from complex texts.

---

## 📌 Features

- Domain-specific QA on **scientific** and **biomedical** literature.
- Utilizes **SciBERT** and **Bio-ClinicalBERT** from Hugging Face.
- Supports long PDF inputs by chunking into model-compatible sizes.
- Curated QA dataset creation for reliable evaluation.
- Modular scripts for dataset creation and inference.

---

## 🚀 Approaches

### Scientific Domain
- Used [`allenai/scibert_scivocab_uncased`](https://huggingface.co/allenai/scibert_scivocab_uncased).
- Focused on scientific PDFs (research papers, articles).
- Extracted question-context-answer triplets from PDFs.

### Biomedical Domain
- Used [`emilyalsentzer/Bio_ClinicalBERT`](https://huggingface.co/emilyalsentzer/Bio_ClinicalBERT).
- Applied to biomedical PDFs (clinical notes, medical publications).
- Customized for handling domain-specific terminology and structure.

---

## ⚠️ Challenges & Solutions

### 1. **512 Token Limit**

- **Problem:** Transformer models like BERT can only process 512 tokens.
- **Solution:** 
  - Implemented `expand_split_sentences()` to split PDF text into overlapping chunks.
  - Performed QA on each chunk and selected the answer with the highest start score.

### 2. **Loss of Context in Long Documents**

- **Problem:** Chunking may break contextual continuity in complex documents.
- **Solution:** 
  - Created curated QA datasets with:
    - `question`
    - `context`
    - `ground truth`
  - This structure ensures meaningful evaluation of the QA pipeline.

---