# Heart Failure Prediction Model

A machine learning system that predicts heart failure risk from routine clinical data, built as a final year BSc Information Technology project.

## Overview

Diagnosing heart failure in many hospitals still relies heavily on clinical expertise, lab tests, and imaging — a process that can be slow and resource-intensive, especially in low-resource settings. This project builds a machine learning-based decision-support tool that predicts a patient's heart failure risk from clinical data, and wraps the best model in a simple web application for clinicians.

## Features

- Trains and compares 5 machine learning algorithms for heart failure prediction
- Web interface for entering patient data and receiving instant risk predictions
- Displays risk category (Low Risk / High Risk) with probability score
- Keeps a history of previous predictions

## Dataset

- **Source:** Heart Failure Clinical Records dataset (public)
- **Size:** 299 patient records, 11 clinical features used for prediction (age, anaemia, creatinine phosphokinase, diabetes, ejection fraction, high blood pressure, platelets, serum creatinine, serum sodium, sex, smoking status)
- **Target:** Death event during follow-up (used as a proxy for heart failure risk)
- **Split:** 80% training (239 records) / 20% test (60 records)

## Models & Results

Five models were trained and evaluated on the same test set:

| Model | Accuracy | Precision | Recall | F1-score | ROC-AUC |
|---|---|---|---|---|---|
| Logistic Regression | 70.0% | 53.8% | 36.8% | 43.8% | 74.5% |
| Decision Tree | 71.7% | 57.1% | 42.1% | 48.5% | 63.7% |
| **Random Forest** | **75.0%** | **64.3%** | 47.4% | 54.5% | **79.5%** |
| Support Vector Machine | 75.0% | 64.3% | 47.4% | 54.5% | 74.3% |
| Artificial Neural Network | 73.3% | 57.9% | 57.9% | 57.9% | 71.5% |

**Random Forest** was selected as the best-performing model, with **serum creatinine** and **ejection fraction** identified as the strongest predictors of heart failure risk.

## Tech Stack

- **Language:** Python
- **ML:** scikit-learn, Pandas, NumPy
- **Visualization:** Matplotlib, Seaborn
- **Web framework:** Django

## Getting Started

### Prerequisites
- Python 3.x
- pip

### Installation

```bash
git clone https://github.com/your-username/heart-failure-prediction.git
cd heart-failure-prediction
pip install -r requirements.txt
```

### Running the app

```bash
python manage.py migrate
python manage.py runserver
```

Then open `http://127.0.0.1:8000` in your browser, log in, and submit patient data to get a prediction.

## Project Structure

```
heart-failure-prediction/
├── data/               # Dataset and preprocessing scripts
├── models/             # Trained ML models and training scripts
├── webapp/             # Django application (UI, views, templates)
├── notebooks/          # Model training & evaluation notebooks
├── requirements.txt
└── README.md
```

## Limitations

- Trained on a relatively small dataset (299 records) with class imbalance, which limits recall (the model misses some high-risk patients)
- Not yet validated on external patient populations
- Intended as a **decision-support** tool to assist clinicians, not to replace clinical judgement

## Future Work

- Train on larger, more diverse datasets
- Address class imbalance (oversampling / class weighting)
- Add model explainability (SHAP / LIME)
- Further clinical validation before real-world deployment

## Authors

- Serwaa Phillipa
- Ampofo George Adinkra
- Oppong Blessing
- Elizabeth Akodor

**Supervisor:** Dr. Michael Opoku
Department of Information Technology and Decision Sciences

## License

This project is for academic purposes.
