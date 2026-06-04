# Customer_Segmentation_Analysis
# 🎯 Lead Scoring Case Study — X Education
### Logistic Regression Model | MBA Business Analytics | Machine Learning Assignment

---

## 📌 Project Overview

X Education is an online education company that markets its courses to industry professionals. When visitors land on the website and fill out a form, they become **Leads** — but only around **38% of leads convert** into actual customers.

The goal of this project is to build a **Lead Scoring Model** using Logistic Regression that assigns a score between **0 and 100** to each lead, allowing the sales team to focus their efforts on leads most likely to convert — improving efficiency and revenue.

---

## 🎯 Business Problem

> *"Identify hot leads so the sales team stops wasting time on cold ones."*

The company wanted a data-driven way to prioritize which leads to call first. A score above **65** is recommended as the business threshold, which delivers an expected **~80% conversion rate** on contacted leads.

---

## 📂 Dataset

| Detail | Value |
|---|---|
| Source | [X Education Lead Scoring Dataset — Kaggle](https://www.kaggle.com/datasets/lakshmikalyan/lead-scoring-x-online-education) |
| Raw Shape | 9,240 rows × 37 columns |
| Target Variable | `Converted` (1 = converted, 0 = not converted) |
| Baseline Conversion Rate | ~38% |

---

## 🛠️ Tools & Libraries

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-ML-orange?logo=scikit-learn)
![Pandas](https://img.shields.io/badge/Pandas-Data-green?logo=pandas)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Viz-red)
![Google Colab](https://img.shields.io/badge/Google%20Colab-Notebook-yellow?logo=googlecolab)

- **Data Manipulation:** `Pandas`, `NumPy`
- **Machine Learning:** `Scikit-Learn` (LogisticRegression, StandardScaler, train_test_split)
- **Visualization:** `Matplotlib`, `Seaborn`
- **Environment:** Google Colab

---

## 🔄 Project Workflow

```
Raw Data (9240 rows)
    ↓
Task 1 — Import Libraries
    ↓
Task 2 — Load Data & Preliminary Observation
    ↓
Task 3 — Data Cleaning & Preprocessing
    ↓
Task 4 — Exploratory Data Analysis (13 Visualizations)
    ↓
Task 5 — Feature Engineering (Label Encoding + One-Hot Encoding)
    ↓
Task 6 — Train-Test Split (70/30) + Feature Scaling
    ↓
Task 7 — Model Training & Evaluation
    ↓
Task 8 — Lead Score Assignment (0–100) + Feature Importance
    ↓
Task 9 — Threshold Analysis & Final Visualizations
    ↓
Output: High Priority Leads CSV (Score ≥ 65)
```

---

## 🧹 Data Cleaning Highlights

- Dropped **21 columns** with >40% missing values (e.g., `Lead Quality`, `Asymmetrique` scores, `Tags`)
- Replaced `'Select'` entries (form non-responses) with `NaN` — treated as missing
- Removed binary columns with near-zero variance (e.g., `Magazine`, `Newspaper`) — no predictive value
- Final cleaned shape: significantly reduced from 37 columns, retaining only meaningful features

---

## 📊 Key EDA Findings

| # | Analysis | Finding |
|---|---|---|
| 1 | Target Distribution | 62% not converted, 38% converted — moderately imbalanced |
| 2 | Website Time | Converted leads spend significantly more time on the site |
| 3 | Correlation | `Total Time Spent on Website` has the strongest correlation (0.37) with conversion |
| 4 | Lead Source | Reference & Welingak leads have the highest conversion rates |
| 5 | Last Activity | Phone conversations → highest probability of conversion |
| 6 | Occupation | Working Professionals are the best-converting segment |
| 7 | Opt-Out Flags | `Do Not Email = Yes` leads convert at significantly lower rates |
| 8 | City Analysis | Mumbai dominates lead volume; some smaller cities outperform on conversion rate |

---

## ⚙️ Feature Engineering

- **Label Encoding** — Binary Yes/No columns mapped to 1/0 (`Do Not Email`, `Do Not Call`, `Search`)
- **One-Hot Encoding** — All remaining categorical columns encoded with `drop_first=True` to avoid multicollinearity (dummy variable trap)

---

## 🤖 Model: Logistic Regression

| Parameter | Value |
|---|---|
| Algorithm | Logistic Regression |
| Regularization (C) | 1.0 (default) |
| Max Iterations | 1000 |
| Train / Test Split | 70% / 30% |
| Random State | 42 (reproducible) |
| Feature Scaling | StandardScaler (fitted on train only — no data leakage) |

---

## 📈 Model Results

| Metric | Value |
|---|---|
| **Accuracy** | ~91% |
| **ROC-AUC Score** | ~0.97 |
| **Recommended Threshold** | 0.65 (Lead Score ≥ 65) |
| **Expected Conversion at Threshold** | ~80% |

### Threshold Analysis Summary

| Threshold | Precision | Recall | Sales Calls Made |
|---|---|---|---|
| 0.30 | Lower | Higher (more leads caught) | Maximum |
| 0.50 | Balanced | Balanced | Default |
| **0.65** | **Optimal** | **Optimal** | **Recommended** |
| 0.80 | Higher | Lower (misses some leads) | Minimum |

> **Business Recommendation:** Use threshold **0.65** — it balances Precision and Recall, ensuring the sales team contacts genuinely hot leads without missing real opportunities.

---

## 💡 Key Business Insights

1. **Time on Website is the #1 signal** — Leads who spend more time on the site and view more pages are dramatically more likely to convert. Improving website engagement could directly boost conversions.

2. **Lead Source matters** — Leads from Referrals and Welingak Leads convert best. Investing more in referral programs could be high ROI.

3. **Working Professionals are the sweet spot** — They are the most likely to convert, suggesting course messaging should emphasize career growth and professional development.

4. **Auto-deprioritize opt-outs** — Leads with `Do Not Email = Yes` show significantly lower conversion. Filtering these out saves the sales team's time automatically.

5. **Phone call = intent signal** — Leads whose last activity was a phone conversation have the highest conversion probability. Prioritizing callbacks is a quick win.

---

## 📁 Repository Structure

```
lead-scoring-x-education/
│
├── Assignment_ML_Shubham_1007_MBA_BA_3rd_final.ipynb   # Main notebook
├── README.md                                            # Project documentation
│
├── data/
│   ├── Leads.csv                                        # Raw dataset (from Kaggle)
│   └── Clean_Leads_df.csv                               # Cleaned dataset (output)
│
├── output/
│   ├── High_Priority_Leads.csv                          # Leads with Score ≥ 65
│   └── model_plots.png                                  # ROC curve, feature importance, score distribution
│
└── presentation/
    └── LeadScoring_Presentation.pdf                     # Project presentation
```

---

## 🚀 How to Run

1. Open the notebook in **Google Colab**: [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/)
2. Upload `Leads.csv` to your Google Drive under `MyDrive/ML Assignment/`
3. Run all cells in order (Runtime → Run All)
4. High-priority leads will be exported automatically to `High_Priority_Leads.csv`

---

## 👤 Author

**Shubham** |
MBA — Business Analytics |
Machine Learning Assignment

---

## 📜 References

- [X Education Lead Scoring Dataset — Kaggle](https://www.kaggle.com/datasets/lakshmikalyan/lead-scoring-x-online-education)
- [Machine Learning Lifecycle — GeeksforGeeks](https://www.geeksforgeeks.org/machine-learning/machine-learning-lifecycle/)
- Scikit-Learn Documentation — [scikit-learn.org](https://scikit-learn.org)
