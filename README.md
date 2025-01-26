# CORAL-X: Contextual Risk Assessment using LLMs for Explainable Loan Default Prediction

## Overview
CORAL-X is a hybrid system designed to improve loan default prediction and risk assessment by combining traditional machine learning (ML) models with large language models (LLMs) using Retrieval-Augmented Generation (RAG). The system incorporates contextual data, such as regional economic conditions, to provide explainable credit decisions that are fast, accurate, and transparent.

---

## Problem Statement
Loan default prediction systems often rely solely on individual borrower data, leading to suboptimal decisions, particularly for underserved populations. Current methods lack the ability to incorporate contextual factors like regional economic policies or income trends without significant human intervention. CORAL-X addresses this gap by leveraging LLMs and RAG to integrate contextual insights from publicly available data, automating the process while maintaining transparency.

---

## Objectives
- Develop a hybrid system combining ML models for structured data with LLMs for unstructured contextual insights.
- Integrate regional economic and policy data into the risk assessment pipeline.
- Ensure explainability by generating natural language explanations for risk score prediction.

---

## Methodology

### Data Collection and Preprocessing
1. Collect structured datasets from public sources like Kaggle.
2. Extract unstructured data from policy reports and economic summaries.
3. Clean and preprocess datasets:
   - Normalize structured data.
   - Generate embeddings for unstructured text.

### Exploratory Data Analysis (EDA)
- Visualize income distributions and default patterns across regions.
- Analyze correlations between poverty rates and loan default probabilities.

### Modeling
1. **Traditional ML Models**:
   - Train models like Gradient Boosting on structured features.
   - Evaluate using metrics such as accuracy, F1-score, and AUC-ROC.
2. **LLM + RAG Pipeline**:
   - Store text embeddings in a vector database (e.g., Pinecone).
   - Use RAG to retrieve relevant context during queries.

### Deployment
- Containerize the system using Docker.
- Deploy APIs for ML predictions and RAG workflows using Flask and AWS Lambda.
- Build an interactive interface with Streamlit for user inputs and outputs.

---