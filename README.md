# Cardiovascular Risk Prediction — A Logistic Regression Approach

A machine learning project that builds a binary classifier to predict 10-year cardiovascular risk using a synthetic UK primary care dataset. Developed as a practical demonstration of applied machine learning in a clinical context, with reference to how tools like QRISK3 are used in NHS general practice.

This was made with minimal coding knowledge and extensive AI assistance, highlighting the accessibility of practical applied ML from a non-coding background.  

---

## Background

Cardiovascular disease (CVD) is the leading cause of preventable mortality in England, accounting for around 160,000 deaths per year. The NHS currently uses QRISK3 — a logistic regression-based clinical risk tool — to estimate an individual's 10-year probability of experiencing a heart attack or stroke. QRISK3 is embedded in GP software across England and informs decisions about statin prescribing and lifestyle intervention.

This project builds a simplified, interpretable analogue to QRISK3 using logistic regression, trained on a publicly available synthetic primary care dataset. The aim is not to replicate or replace QRISK3, but to demonstrate how its underlying methodology can be applied, evaluated, and interpreted using standard machine learning tooling.

---

## Aims

**Primary aim**

To build a binary classification model that predicts whether an adult patient will experience a heart attack or stroke within a 10-year follow-up period, using demographic, lifestyle, and clinical variables drawn from a synthetic UK primary care dataset.

**Secondary aims**

1. To evaluate model performance using clinically appropriate metrics, with particular attention to the sensitivity–specificity tradeoff and its implications for NHS screening contexts.
2. To interpret the model's predictions using feature coefficients and SHAP values, and to contextualise these findings against known cardiovascular risk factors.
3. To critically appraise the model's limitations and its potential applicability — and barriers to deployment — within the NHS.

---

## Dataset

**Source:** [NIHR ARC Wessex Synthetic CVD Dataset (v0.2)](https://www.arc-wx.nihr.ac.uk/data-sets)

| Property | Detail |
|---|---|
| Rows | 100,000 simulated patients |
| Task | Binary classification (heart attack or stroke within 10 years: yes/no) |
| Variables | Demographics, lifestyle, comorbidities, blood pressure, family history, respiratory function |
| Licence | Creative Commons (open access) |
| Origin | Modelled on QRISK3 variable set; designed to reflect UK primary care data complexity |

The dataset was produced by the National Institute for Health and Care Research (NIHR) Applied Research Collaboration Wessex and is freely available with no registration required. It was specifically designed for machine learning training purposes and incorporates realistic data challenges including missing values, noise, variable irrelevance, and informative censoring.

> **Note:** This is a synthetic dataset, not derived from real patient records. It is not suitable for clinical use and results should not be interpreted as clinically validated.

---

## Methods

### 1. Exploratory Data Analysis
- Distribution of all variables examined
- Class balance assessed
- Missing data patterns characterised and visualised
- Clinically relevant correlations identified and annotated

### 2. Data Preprocessing
- Missing values handled via appropriate imputation strategies
- Categorical variables encoded
- Continuous variables scaled
- Stratified train/test split (80/20) applied to preserve class balance

### 3. Model Training
- **Primary model:** Logistic regression classifier
- **Comparator:** Random forest classifier
- Logistic regression coefficients examined for alignment with established cardiovascular risk factors

### 4. Evaluation
Models evaluated on the held-out test set using:
- AUC-ROC
- Sensitivity and specificity
- Precision-recall curve
- Confusion matrix

The clinical implications of false negatives and false positives are discussed explicitly in the context of NHS primary care decision-making.

### 5. Interpretability
- Feature importance examined via logistic regression coefficients
- SHAP values used to interpret individual predictions
- Results contextualised against QRISK3 variable weightings where possible

### 6. Critical Appraisal
The model is assessed against real-world deployment considerations including dataset limitations, generalisability to NHS populations, regulatory considerations under MHRA and NHS AI Lab guidance, and ethical implications of algorithmic risk scoring.

---

## Results

AUC-ROC: 0.83
Sensitivity: 0.80
Specificity: 0.73
False negatives: 267 out of 1,322 true events
Random forest AUC-ROC: 0.77 for comparison

---

## Limitations

**Synthetic data:** The dataset is simulated and may not capture the full heterogeneity of NHS primary care populations.

**Scope of variables:** The dataset does not include the full QRISK3 variable set, so direct performance comparison with QRISK3 is not possible.

**Proof of concept only:** This model is not intended for clinical use. Its purpose is to demonstrate applied machine learning methodology in a clinically grounded context.

---

## What I Would Do Next

- Validate the approach against a real-world dataset such as CPRD (with appropriate access)
- Explore gradient boosting models (XGBoost) as a higher-performing comparator
- Investigate fairness metrics across demographic subgroups
- Consider the regulatory pathway this type of tool would follow under MHRA's AI as a Medical Device framework

---

## Stack

- Python 3
- pandas, numpy
- scikit-learn
- matplotlib, seaborn
- SHAP
- Jupyter Notebook

---

## How to Run

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
cd YOUR_REPO_NAME
pip install -r requirements.txt
jupyter notebook
```

Then open `notebooks/01_eda.ipynb` to begin.

---

## References

- Burns D, Richardson K and Driessens C. *A synthetic dataset for the exploration of survival and classification models: prediction of heart attack or stroke within a 10-year follow-up period.* NIHR Open Research 2024. https://doi.org/10.3310/nihropenres.13651.1
- Hippisley-Cox J et al. *Predicting cardiovascular risk in England and Wales: prospective derivation and validation of QRISK2.* BMJ 2008.
- NHS AI Lab. *Guidance on AI and digital tools in health and social care.* NHS England, 2023.

---

*This project was developed as a portfolio demonstration at the intersection of clinical medicine and applied machine learning.*
