# PDF-Based Question Answering (Scientific Domain)

This project implements a Question Answering (QA) system for **scientific domain PDFs** using the `SciBERT` model. It allows users to extract answers from long and complex documents by splitting and processing the content intelligently.

---

## 📌 Features

- Domain-specific QA system for **scientific literature**.
- Utilizes the pre-trained **SciBERT** model.
- Handles long PDFs by chunking text into model-compatible sizes.
- Includes curated dataset creation for accurate evaluation.

---

## 🚀 Approach

- Used [`allenai/scibert_scivocab_uncased`](https://huggingface.co/allenai/scibert_scivocab_uncased) for fine-tuned question answering tasks.
- Processed raw PDF content by extracting text and breaking it into 512-token chunks.
- QA performed on each chunk, with final answer selected based on highest model confidence (start score).
- Constructed a structured dataset with the following fields:
  - `question`
  - `context`
  - `ground truth`

---

## ⚠️ Challenges & Solutions

### 1. **512 Token Limit**

- **Issue:** SciBERT (like BERT) can only process 512 tokens at once.
- **Solution:** Used a custom function `expand_split_sentences()` to split long texts into overlapping chunks of 512 tokens for inference.

### 2. **Loss of Context**

- **Issue:** Splitting text can reduce semantic coherence.
- **Solution:** Created a custom dataset to preserve meaningful context for QA:
  - Ensures evaluation aligns with intended answers even for complex scientific documents.

