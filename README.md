# 🧠 Term Deposit Prediction – ML App (FastAPI + Scikit-learn)

A Machine Learning–powered web application built using **FastAPI** that predicts whether a bank client will subscribe to a **term deposit**.  
The prediction is based on demographic, financial, and marketing campaign features.

---

## 📊 Dataset

This project uses the **Bank Marketing Dataset**, containing attributes such as:

- Age, Job, Marital Status, Education  
- Default, Housing Loan, Personal Loan  
- Contact Communication Type  
- Campaign Duration & Outcome  
- Previous Campaign Interactions  

📄 For complete **EDA, preprocessing, model comparison, and training**, see:![Alt text](Notebook_v1.ipynb)

---

## ✅ Features

### 🔍 EDA + Preprocessing Pipeline
- One-Hot Encoding (categorical features)  
- Missing value imputation  
- Standard scaling for numerical fields  
- Train–test split + model evaluation  

### 🤖 ML Models Used
- Random Forest  
- XGBoost  
- Gradient Boosting  

### 🌐 FastAPI Web Interface
- Clean **Jinja2 HTML form** for user inputs  
- Automatic preprocessing + prediction  
- User-friendly result display  

### 🚫 No Docker Required
- Fully runnable locally with **Uvicorn**  
- Docker support is optional

---

## 🛠 Tech Stack

| Layer        | Tools & Libraries                         |
|--------------|--------------------------------------------|
| Backend API  | FastAPI, Pydantic, Uvicorn                |
| ML / EDA     | Scikit-learn, XGBoost, Pandas, NumPy      |
| Frontend     | HTML (Jinja2 templates)                   |
| Visualization| Matplotlib, Seaborn                       |
| Environment  | Python 3.8+                                |

---

