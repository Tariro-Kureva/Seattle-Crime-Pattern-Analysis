# Seattle-Crime-Pattern-Analysis
Predicting violent crime in Seattle using XGBoost &amp; Logistic Regression — 97% accuracy, 99.7% precision
# 🚨 Predicting Crime Before It Happens
### A Comprehensive Analysis of Crime Patterns & Severity in Seattle

> *90.83% of Seattle crimes are Non-Violent. This project builds a system that identifies the other 9.17% — before dispatch.*

**Author:** Tariro Kureva | Final Report

---

## 💡 The Problem
Seattle's emergency dispatch system treats every crime report the same way. But a stolen bicycle and a homicide are not the same emergency. This project builds a predictive framework that classifies incoming crime reports as **Violent** or **Non-Violent** in real time — enabling smarter resource allocation and faster response to the incidents that matter most.

---

## 💥 The Numbers That Define This Dataset

| Stat | Value |
|------|-------|
| 🗂️ Dataset | Seattle Police Department Crime Data |
| 👮 Crime records analyzed | Full SPD dataset (cleaned) |
| ⚖️ Class split | ~90.83% Non-Violent · ~9.17% Violent |
| 🏆 Best model accuracy | 97.0% (Logistic Regression) |
| 🎯 Best model precision | 99.7% (Logistic Regression) |
| 🌲 Ensemble model | Random Forest + XGBoost (hyperparameter tuned) |
| 🔢 Severity scale | 1 (Other) → 10 (Homicide) |

---

## 🔢 Custom Severity Scoring System

One of the most impactful innovations in this project — a custom severity scale built from scratch:

| Crime Category | Severity Score | Classification |
|----------------|---------------|----------------|
| Homicide | 10 | 🔴 Violent |
| Sex Offenses | 9 | 🔴 Violent |
| Assault Offenses | 8 | 🔴 Violent |
| Robbery | 7 | 🔴 Violent |
| Burglary | 6 | 🟡 Non-Violent |
| Motor Vehicle Theft | 5 | 🟡 Non-Violent |
| Larceny-Theft | 4 | 🟡 Non-Violent |
| Other | 1 | 🟢 Non-Violent |

> Crimes with Severity Score ≥ 7 = **Violent**. Below 7 = **Non-Violent**.

---

## 🤖 Models Tested & Results

| Model | Accuracy | Precision | Recall | F1 |
|-------|----------|-----------|--------|----|
| Logistic Regression | **97.0%** | **99.7%** | — | — |
| Decision Tree | — | — | — | — |
| K-Nearest Neighbors | — | — | — | — |
| Random Forest | — | — | — | — |
| Random Forest (Tuned) | — | — | — | — |
| XGBoost | — | — | — | — |
| XGBoost (Tuned) | — | — | — | — |

> Logistic Regression selected as primary dispatch model for its unmatched precision and explainability.

---

## 🛠️ Full Pipeline

```
Seattle Crime Dataset (SPD)
        ↓
Data Cleaning
(drop duplicates, handle nulls, fix datatypes)
        ↓
Feature Engineering
├── Extract Year, Month, Hour from timestamps
├── Calculate Crime Duration (mins)
├── Apply Custom Severity Score (1–10)
└── Classify as Violent / Non-Violent
        ↓
Outlier Handling
(IQR method + Z-Score for numerical columns)
        ↓
Preprocessing
(One-hot encoding + StandardScaler)
        ↓
Train/Test Split (80/20 stratified)
        ↓
Model Training
├── Logistic Regression
├── Decision Tree
├── K-Nearest Neighbors
├── Random Forest
└── XGBoost
        ↓
Hyperparameter Tuning
(RandomizedSearchCV + StratifiedKFold)
        ↓
Model Evaluation
(Accuracy, Precision, Recall, F1, Confusion Matrix)
        ↓
Feature Importance Analysis
        ↓
Deployment Strategy
```

---

## 🔑 Key Findings

### 1. Property crimes dominate — violent crimes are rare but critical
~62% of incidents are property crimes. Violent crimes make up only ~9.17% — but represent the highest urgency calls requiring fastest dispatch.

### 2. East and West precincts show highest crime severity
Spatial analysis revealed the East and West sectors as high-priority zones for nocturnal surveillance and targeted patrols.

### 3. Logistic Regression outperforms ensemble models for this use case
With 99.7% precision, Logistic Regression virtually eliminates false positives — critical in a dispatch context where wrongly flagging a non-violent crime as violent wastes emergency resources.

### 4. XGBoost excels at catching violent crimes (recall)
While Logistic Regression leads on precision, the tuned XGBoost model captures more true violent crime cases — making it ideal as a secondary screening layer.

### 5. Crime duration and hour of day are key predictors
Temporal features extracted from timestamps (hour, month, crime duration) are among the top feature importances — crime patterns are strongly time-dependent.

---

## 🏛️ Proposed Deployment Strategy

**Tier 1 — Real-Time Dispatch (Logistic Regression)**
99.7% precision. Near-zero false positives. Explainable to dispatchers. Fast inference.

**Tier 2 — Secondary Screening (XGBoost Tuned)**
Higher recall catches violent crimes the primary model may miss. Acts as a safety net.

**Tier 3 — Strategic Planning (Feature Importance + Clustering)**
Long-term pattern analysis for resource allocation, patrol scheduling and policy decisions.

---

## 💡 Policy Recommendations

1. **Targeted Patrols** — increase nocturnal surveillance in East and West precincts as identified by the model
2. **Precision Prevention** — launch focused property crime prevention in high-frequency zones before crimes escalate
3. **Early Intervention** — use temporal patterns (peak hours, seasonal trends) to pre-position resources
4. **Embed Model in Dispatch System** — auto-flag incoming reports using the Logistic Regression classifier for real-time triage

---

## ⚠️ Limitations
- Geospatial gaps — some records lack latitude/longitude, introducing potential bias in spatial analysis
- Highly imbalanced dataset (~90/10 split) — evaluation focused on Precision, Recall and F1 over raw accuracy
- Static dataset — model requires retraining as crime patterns evolve
- Severity scoring is rule-based — a data-driven severity model could improve nuance

---

## 🔧 Tools & Libraries
- Python
- Pandas / NumPy
- Scikit-learn (Logistic Regression, Decision Tree, KNN, Random Forest, StandardScaler)
- XGBoost
- Matplotlib / Seaborn
- RandomizedSearchCV + StratifiedKFold (hyperparameter tuning)

---

## 📁 Files
| File | Description |
|------|-------------|
| `Tariro_Kureva_Final_Report_Seattle_Crime.ipynb` | Full Jupyter notebook — EDA, modeling, evaluation |

---

## 🔗 Related Projects
👉 [IBM HR Analytics — K-Means Clustering & Attrition](https://github.com/Tariro-Kureva/IBM-HR-Analytics-Clustering)
👉 [IMDB Sentiment Analysis — NLP & Machine Learning](https://github.com/Tariro-Kureva/IMDB-Sentiment-Analysis-NLP)
👉 [MovieLens Rating Analysis — Collaborative Filtering](https://github.com/Tariro-Kureva/MovieLens-Rating-Analysis)
👉 [Movie Plot Narrative Similarity — SentenceTransformers](https://github.com/Tariro-Kureva/Movie-Plot-Narrative-Similarity)
👉 [Extreme Disaster Events in Southern Africa — Power BI](https://github.com/Tariro-Kureva/Extreme-disaster-events-Southern-Africa)

---

*Last updated: April 2026*

