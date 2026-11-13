# Recession Identification Using Machine Learning and Economic Policy Uncertainty

An interdisciplinary research project investigating how machine learning can identify economic recessions across different countries and whether Economic Policy Uncertainty (EPU) provides additional predictive information beyond traditional macroeconomic indicators.

This research was conducted at **Lewis University** as part of the 2025 Summer Undergraduate Research Experience (SURE), in collaboration with Dr. Oguzhan Batmaz and Dr. Taeyong Kim.

**Manuscript:** *Recession Identification with Machine Learning across Four Advanced Economies: The Heterogeneous Role of Economic Policy Uncertainty* (under review).

## Research Overview

Economic recessions are difficult to identify due to changing economic conditions, structural differences between countries, and the limited number of historical recession episodes.

This study investigates recession identification across four advanced economies:

**United States · Canada · Japan · Germany**

Using monthly macroeconomic data from **1994 to 2024**, we evaluated whether machine learning models could identify recession periods and whether incorporating EPU improves model performance.

The research explored three main questions:

- How do different machine learning architectures perform across countries?
- Do country-specific models outperform models trained on pooled international data?
- Does Economic Policy Uncertainty improve recession identification beyond traditional macroeconomic indicators?

## Methodology

### Data & Feature Engineering

The study combined data from FRED, OECD, the World Bank, and the Economic Policy Uncertainty Project.

The analysis included macroeconomic indicators such as GDP, unemployment, inflation, industrial production, consumer confidence, yield spreads, and the OECD Composite Leading Indicator.

Additional features captured changes in EPU over time and interactions between economic uncertainty and macroeconomic conditions.

Official recession chronologies from each country's respective business-cycle dating institutions were used to establish the classification targets.

### Machine Learning Models

We compared several machine learning architectures:

- Logistic Regression
- Random Forest
- XGBoost
- LightGBM
- Multi-Layer Perceptron (MLP)
- Long Short-Term Memory (LSTM)

The primary evaluation used a **purged Leave-One-Recession-Out (LORO)** approach, testing model performance on held-out recession episodes while reducing temporal information leakage.

Country-specific and pooled models were compared under matched evaluation conditions.

### Model Interpretability

We used **SHapley Additive exPlanations (SHAP)** to investigate the contributions of macroeconomic indicators and EPU-related features.

Feature ablation experiments were also conducted to determine whether adding EPU improved predictive performance, rather than relying solely on feature importance.

## Research Results

### Model Performance

The best observed country-specific model varied across countries.

| Country | Best Model | ROC-AUC |
|---|---|---:|
| United States | MLP + SMOTE | 0.978 |
| Canada | Logistic Regression | 0.917 |
| Japan | Random Forest | 0.828 |
| Germany | XGBoost | 0.948 |

The average of these best observed scores was **0.918**. This is a descriptive comparison of the highest observed results, not a nested estimate of model-selection performance.

### Country-Specific vs. Pooled Models

Country-specific models achieved higher ROC-AUC in **9 out of 20 matched comparisons**, while pooled models performed better in the remaining 11.

These results suggest that training models on combined international data is not necessarily better or worse than using country-specific data. Performance depends on the country and model architecture.

### Economic Policy Uncertainty

SHAP analysis attributed approximately **12.5%–20.9%** of total mean absolute model attribution to EPU-related features across the four countries.

However, feature ablation experiments showed that including EPU did not consistently improve out-of-sample performance.

This highlighted an important distinction: **a feature can be influential within a model without necessarily improving its predictive performance.**

### Deep Learning

In a separate fixed-calendar holdout, the pooled LSTM achieved:

- ROC-AUC: 0.878
- PR-AUC: 0.635
- Brier Score: 0.198

Compared with pooled Logistic Regression, the LSTM demonstrated better precision-recall ranking and probability accuracy, despite having a lower ROC-AUC.

## Key Takeaways

The research demonstrated that no single machine learning architecture consistently performs best across all countries.

It also highlighted the importance of careful temporal evaluation, model interpretability, and distinguishing feature attribution from incremental predictive value.

While EPU-related variables contributed to model explanations, their additional predictive usefulness depended on the country, model, and evaluation metric.

Because some predictors use contemporaneous information and interpolated GDP data, the study focuses on **recession identification and monitoring**, rather than operational real-time forecasting.

## Research Presentations

- **Lewis University SURE Symposium (2025)**
- **95th Annual Meeting of the Southern Economic Association (2025)** — Tampa, Florida

## Research Team

**Authors:**
- Dr. Oguzhan Batmaz — Lewis University
- Dr. Taeyong Kim — Lewis University
- Gabriel Felipe dos Reis — Lewis University

---

*This repository contains research code and exploratory experiments associated with the project. The manuscript reports a subsequently expanded evaluation, and not all analyses described in the paper are represented in the current public notebooks.*
