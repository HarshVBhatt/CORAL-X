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

## Setup
- Currently the most updated branch is "ml_models". This deals with processing structured data and creating ML models for the same. Make sure to switch to that before cloning
- Create a dedicated folder where you would like to have all the notebooks and data. Clone the repo into the folder
- Create a new environment
- Use the requirements.txt with the following command to install all dependencies: pip install -r /path/to/requirements.txt
- Download the data from: https://www.kaggle.com/code/pavlofesenko/minimizing-risks-for-loan-investments?select=accepted_2007_to_2018Q4.csv.gz
- Move the data file to the dedicated folder. You can choose to move it inside the cloned repo, or keep it outside. Copy the path to the data file as /path/to/accepted_2007_to_2018Q4.csv
- Create a separate folder inside the repo /path/to/repo/data/procesed. This is where the processed data will be saved

- NOTE: pinecone_embedding_and_indexing.ipynb is used to generate embeddings for the unstructured data. The current file is a sample of how the process would work but is not reflective of the final state. This will be worked on in the next phase i.e. after the completion of structed data and it's respecive modelling.
---

## How to run
- First run the preprocessing_eda.ipynb. In cell 4 change the data_path variable to /path/to/accepted_2007_to_2018Q4.csv. Run the entire notebook.
- You should see the following files - all_data_cleaned_grouped.csv, train_data.csv, test_data.csv - saved to "data/processed/". We will primarily use "all_data_cleaned_grouped.csv" to run the other notebooks and the ML model. The other files are used for ablation studies and experimentation
- Run the notebook rand_OS_models_shap.ipynb. The notebook simulates random oversampling, experiments with LGBM and XGBoost classifiers using sklearn pipeline, and SHAP values for each sample in the test data which will be created in the notebook.
- Note that the outputs in rand_OS_models_shap.ipynb are currently not saved. This is a work in progress. To reproduce the outputs, the entire notebook must be run again.

--

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
