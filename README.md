# Norwegian Pension Fund Global (GPFG) – ESG Equity Analysis & Machine Learning (2024)

This repository provides a structured analysis of the **Norwegian Pension Fund Global (GPFG)** with an **ESG perspective**, using its equity holdings data for 2024. The analysis is divided into three main steps:

## 1. Exploratory Data Analysis (EDA)
Examines sector and regional allocation, portfolio concentration, and ownership–voting discrepancies.

## 2. Data Preprocessing & Feature Engineering
Prepares a clean dataset for modeling, including variable standardization, outlier treatment, categorical encoding, and the construction of an ESG indicator (`ESG_any`).

## 3. Machine Learning
Predicts which companies are likely to engage in ESG dialogues based on their characteristics. Multiple models were trained, tuned, and interpreted using SHAP to understand feature importance.

## Data Sources
All datasets were obtained or constructed from publicly available GPFG information.  
- Historical data (2018–2023) is used for context and portfolio concentration analysis.  
- The 2024 holdings dataset (`clean_fund_2024.xlsx`) and the ESG engagement dataset (`esg_2024.xlsx`) were prepared for machine learning and modeling.  

---

# 🔧 Dependencies

This project uses two different environments, each with its own dependency file:

### 1. `requirements.txt`
Used for the analysis and preprocessing notebooks executed locally on **Python 3.12.4 (VSCode)**.  
It contains only the libraries required for the exploratory analysis, ESG preprocessing, and multi-year fund processing.

### 2. `requirements_ml.txt`
Used exclusively for the **machine learning notebook**, which was executed on **Google Colab** to take advantage of faster computation and higher resources than a local PC.  
This file includes only the packages needed to reproduce the ESG-aligned company classification models.

### How to install
```bash
# For local analysis notebooks
pip install -r requirements.txt

# For the ML notebook (recommended in Google Colab or a virtual environment)
pip install -r requirements_ml.txt
