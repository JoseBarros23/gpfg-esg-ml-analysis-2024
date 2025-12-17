# Norwegian Pension Fund Global (GPFG) – ESG Equity Analysis & Governance Voting (2024-2025)

This repository provides a comprehensive analysis of the **Norwegian Pension Fund Global (GPFG)** with an **ESG and governance perspective**, combining equity holdings analysis (2024) with shareholder voting patterns (2020-2025). The analysis is divided into four main components:

---

## 1. Exploratory Data Analysis (EDA)
Examines sector and regional allocation, portfolio concentration, and ownership–voting discrepancies across historical holdings.

## 2. Data Preprocessing & Feature Engineering
Prepares a clean dataset for modeling, including variable standardization, outlier treatment, categorical encoding, and the construction of an ESG engagement indicator (`ESG_any`).

## 3. Machine Learning for ESG Engagement Prediction
Predicts which companies are likely to trigger ESG dialogues based on their characteristics. Multiple models (XGBoost, CatBoost, LightGBM) were trained, tuned, and interpreted using SHAP to understand feature importance.

## 4. Shareholder Voting & Governance Persistence Analysis
Analyzes 6,692 shareholder meeting disagreements across 1,134 companies (83% portfolio market value, 2020-2025) using NBIM's Voting Records API. 

## 🔍 Key Findings

**Governance Persistence:**
- 86.5% of governance issues recur year-over-year without resolution
- Only 13.5% cure rate within 2 years

**Regional Patterns:**
- North America: 5.3 avg disagreements/company (77.6% affected)
- Europe: 4.3 avg (59.7% affected)
- Asia: 2.2 avg (43.6% affected)
- Statistical validation: p<0.001 for regional differences

**Issue Drivers:**
- CEO/Chair separation: 34.2% (North America) vs 2.4% (Europe)
- CEO remuneration: 24.7% (Technology sector)
- Board independence: 22.8% (Asia)

**Technology Sector:**
- Heterogeneous governance (Alphabet: 39, Nvidia: 0)
- Not systematically worse, just higher variance

**Methodology:**
- Data extraction via NBIM Voting Records API with rate limit management
- Manual company name mapping for top 100 holdings by market value
- Temporal persistence tracking (2-year cure rate analysis)
- Statistical validation (chi-square, t-tests) of regional and sectoral patterns
- ESG category classification of disagreements (Environmental, Social, Governance)

---

## Data Sources

### Equity Holdings Analysis (Notebooks 1-3)
All datasets were obtained or constructed from publicly available GPFG information:
- Historical data (2018–2023) for context and portfolio concentration analysis
- 2024 holdings dataset (`clean_fund_2024.xlsx`) for current portfolio composition
- ESG engagement dataset (`esg_2024.xlsx`) for machine learning target variable

### Voting Records Analysis (Notebook 4)
- **NBIM Voting Records API**: official shareholder voting data
- Sample: 1,925 companies (P80 market value percentile + ESG_any=1 companies)
- Coverage: 1,134 companies successfully processed (59% company count, 83% sample market value)
- Period: 2020-2025 (5+ years of voting history)

---

## 🔧 Dependencies

This project uses two different environments, each with its own dependency file:

### 1. `requirements.txt`
Used for analysis, preprocessing, and **voting analysis notebooks** executed locally on **Python 3.12.4 (VSCode)**.  
Contains libraries required for exploratory analysis, ESG preprocessing, multi-year fund processing, and API-based voting data extraction.

**Key packages for voting analysis:**
- `requests` – API calls to NBIM Voting Records endpoint
- `python-dotenv` – secure API key management
- `matplotlib`, `seaborn` – visualizations (15+ professional charts)
- `scipy` – statistical hypothesis testing (chi-square, t-tests)

### 2. `requirements_ml.txt`
Used exclusively for the **machine learning notebook** (Notebook 3), executed on **Google Colab** for faster computation.  
Includes packages needed to reproduce ESG engagement classification models (XGBoost, CatBoost, LightGBM, SHAP).

### How to install
```bash
# For local analysis, preprocessing, and voting notebooks (1, 2, 4)
pip install -r requirements.txt

# For the ML notebook (3) - recommended in Google Colab or virtual environment
pip install -r requirements_ml.txt
```

---

## 📊 Project Structure
```
.
├── notebooks/
│   ├── 01_eda.ipynb                    # Exploratory data analysis
│   ├── 02_preprocessing.ipynb          # Feature engineering & ESG indicators
│   ├── 03_machine_learning.ipynb       # ML models (XGBoost, SHAP interpretation)
│   └── 04_voting_analysis.ipynb        # Shareholder voting patterns & persistence
├── datasets/
│   ├── clean_fund_2024.xlsx           # 2024 equity holdings
│   ├── esg_2024.xlsx                  # ESG engagement flags
│   ├── p80_companies.csv              # Analysis sample (P80 + ESG)
│   └── voting_data/                   # Voting records outputs
│       ├── disagreements_*.csv        # Individual disagreement records
│       ├── company_stats_*.csv        # Company-level aggregates
│       └── errors_*.csv               # API extraction errors
├── requirements/
│   ├── requirements.txt               # Local environment dependencies
│   └── requirements_ml.txt            # ML environment (Colab) dependencies
└── README.md
```

---

## 🔍 Key Insights

**From ESG Screening (Notebooks 1-3):**
- Machine learning models (XGBoost) predict ESG engagement likelihood with interpretable feature importance
- SHAP analysis reveals key drivers of ESG dialogue triggers

**From Voting Analysis (Notebook 4):**
- **Governance persistence**: 86.5% of issues recur year-over-year (only 13.5% cure rate)
- **Geographic patterns**: North America 5.3 avg disagreements/company vs Asia 2.2 (statistically significant)
- **Sector insights**: Technology sector heterogeneous (not uniformly problematic), CEO remuneration drives 24.7% of tech disputes
- **Temporal trends**: Sustainability reporting rising (+3.2pp from 2020-22 to 2023-25), dual-class shares declining (-2.3pp)
- **Escalation tracking**: 42.3% of companies show worsening governance trends vs 31.8% improving

---

## 🛠️ Methodology Highlights

**Voting Analysis Technical Approach:**
1. **API Integration**: NBIM Voting Records API with authentication and rate limit handling
2. **Name Matching**: Manual mapping of 96 top companies (exact NBIM naming conventions)
3. **Checkpoint System**: Progress saved every 100 companies to prevent data loss
4. **Error Handling**: Fallback hierarchy (ticker → name → cleaned name)
5. **Temporal Tracking**: Company-topic pairs analyzed across 2020-2025 for persistence patterns
6. **Statistical Validation**: Chi-square and t-tests to confirm regional/sectoral differences
7. **ESG Classification**: Position papers categorized into Environmental, Social, Governance dimensions

---

## 📝 Notes

- **API Key Required**: Voting analysis requires NBIM API key (stored in `.env`, not committed to repo)
- **Rate Limits**: NBIM API enforces rate limiting (~400-600 companies per day)
- **Statistical Rigor**: All major geographic/sectoral claims validated with hypothesis tests (α=0.05)

---

## 📄 License

Ssee LICENSE.txt for details.

---

## 👤 Author

Jose Fernando Barros Lozano  
Master's Candidate - Data Science and Business Analytics  
Università di Bologna - Business School

---

## 🙏 Acknowledgments

- **NBIM** for providing public access to Voting Records API
- **GPFG** for transparent equity holdings disclosure
- Anthropic's Claude for analytical assistance and code optimization
