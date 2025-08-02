# PDF-Based Question Answering

This project implements a Question Answering (QA) system on domain-specific PDF documents using various transformer-based models.

## 📌 Features

- QA system for **financial**, **scientific**, and **biomedical** domains.
- Uses fine-tuned transformer models from Hugging Face.
- Chunk-based processing to handle long PDF inputs.
- Curated datasets for accurate evaluation.
- Cross-domain model evaluation.

---

## 🚀 Approaches

- **Financial Domain**
  - Fine-tuned `BERT-base`, `BERT-large`, and `DistilBERT` (on SQuAD) for PDF QA.

- **Scientific Domain**
  - Used `SciBERT` for scientific literature in PDF format.

- **Biomedical Domain**
  - Used `Bio-ClinicalBERT` for QA on biomedical PDFs.

- **Dataset Creation**
  - Custom datasets prepared from PDFs using the `Make_dataset_from_PDFs.ipynb` notebook.

- **Evaluation**
  - Cross-domain testing to assess model generalization.

---

## ⚠️ Challenges & Solutions

### 1. Token Limit (512 tokens)

- **Problem:** BERT-based models can only process up to 512 tokens.
- **Solution:** 
  - Split long PDF texts into 512-token chunks using the `expand_split_sentences` function.
  - Run the QA model on each chunk.
  - Select the final answer based on the maximum start score across chunks.

### 2. Context Loss

- **Problem:** Splitting can break context in complex documents.
- **Solution:**
  - Curated structured QA datasets with:
    - `question`
    - `context`
    - `ground truth`
  - Enables better and more reliable evaluation of the QA pipeline.

---


