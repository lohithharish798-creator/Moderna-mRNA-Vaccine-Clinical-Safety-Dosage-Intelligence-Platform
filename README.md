# Moderna-mRNA-Vaccine-Clinical-Safety-Dosage-Intelligence-PlatformModerna — mRNA Vaccine Clinical Safety & Dosage Intelligence Platform
Disclaimer: This is an individually completed applied AI engineering case study and is not a production clinical system. The clinical guidance produced by this pipeline is for engineering-skill demonstration only and must never be used for real medical decision-making.
Overview
An end-to-end Applied AI pipeline combining classical machine learning, deep learning mathematics, and generative AI to support mRNA vaccine clinical safety evaluation and dosage recommendations.
The system flows sequentially across five modules:
1. Data Pipeline & Risk Classifier (ML): Cleans tabular clinical/biomarker patient records and trains a supervised classifier (Random Forest vs. Logistic Regression) to predict adverse-reaction risk.
2. mRNA Sequence Self-Attention Engine (DL Math): Implements the scaled dot-product Transformer self-attention mechanism from scratch in NumPy/PyTorch to model nucleotide relationships (A, C, G, U).
3. Regulatory RAG Index (Vector Search): Chunks and embeds mRNA regulatory storage/dosing guidelines into a persistent local ChromaDB vector store for semantic retrieval.
4. Structured Clinical Safety Report Generator (GenAI): Combines ML risk scores and retrieved regulatory facts into a strictly schema-validated (Pydantic) JSON and Markdown report with anti-hallucination guardrails.
5. Multi-Panel Evaluation Dashboard: Aggregates the ML ROC curve, self-attention heatmap, and pipeline stage latencies into a single publication-grade figure.
Repository Structure
Prerequisites & Environment Setup
​Python: 3.10 or higher
​API Key: An active OpenAI (or compatible LLM provider) API key for Module 4.
​1. Clone & Create Virtual Environment
Ensure .env is listed in your .gitignore so secrets are never committed.)
​4. Verify Input Data
​Ensure the two provided source files are placed inside the data/ directory before running the pipeline:
​data/patient_records.csv
​data/mrna_safety_guidelines.txt
​How to Reproduce Results
​Run each module sequentially from the root directory (mrna-vip/):
​Week 1: Data Cleaning & ML Risk Classification
​Cleans missing biomarker/reaction history values, standardizes numeric features, compares Logistic Regression and Random Forest models, and saves the winning model.
.Week 3: Regulatory RAG Pipeline
​Splits mrna_safety_guidelines.txt into overlapping chunks, generates all-MiniLM-L6-v2 embeddings, persists them to ChromaDB, and benchmarks semantic search latency.
Week 4: Structured Safety Report & Final Dashboard
Generates a schema-validated ClinicalSafetyReport grounded strictly in Module 1 predictions and Module 3 guidelines, then compiles the final 3-panel summary dashboard.
