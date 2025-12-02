# ESG Analysis of the Norwegian Pension Fund Global (GPFG) – 2024

This repository presents a project focused on **Environmental, Social, and Governance (ESG) analysis** of the Norwegian Pension Fund Global (GPFG), one of the largest sovereign wealth funds in the world, managed by Norges Bank. The GPFG invests across multiple industries and countries, balancing long-term returns with sustainability considerations.

The project is organized into **three main notebooks**, covering data exploration, preprocessing, and machine learning for ESG insights.

## Notebooks

1. **Exploratory Data Analysis (EDA)**  
   - Analyzes the GPFG’s equity holdings in 2024, including sector, industry, and regional allocations.  
   - Examines portfolio concentration metrics over historical years (2018–2024) using Gini, Lorenz curves, and HHI.  
   - Provides insights into ownership–voting discrepancies and governance implications.

2. **Data Preprocessing & Feature Engineering**  
   - Prepares the 2024 equity holdings dataset for machine learning.  
   - Standardizes numeric and categorical variables, handles skewed distributions, and calculates portfolio weights.  
   - Constructs ESG features from company dialogues to indicate engagement on Environmental, Social, Governance, and Climate topics.

3. **Machine Learning for ESG Engagement Prediction**  
   - Builds predictive models to identify companies likely to engage in ESG dialogues with the GPFG.  
   - Uses manual hyperparameter tuning with GridSearchCV for transparency and domain-specific customization.  
   - Includes feature importance analysis using SHAP values to interpret model predictions.

## Datasets

- The 2024 equity holdings dataset was obtained from **public GPFG reports**.  
- The ESG engagement dataset was constructed from **publicly available GPFG company dialogues**. s
---

This project aims to combine **financial analysis, ESG insights, and machine learning** to explore how large sovereign funds can monitor and influence corporate sustainability practices.
