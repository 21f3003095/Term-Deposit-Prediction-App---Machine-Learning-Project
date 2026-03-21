# 🏦 Term Deposit Prediction — ML Web App

A production-ready **Machine Learning web application** built with **FastAPI** and **Scikit-learn** that predicts whether a bank client will subscribe to a **term deposit**, based on the classic UCI Bank Marketing Dataset.

---

## 📌 Overview

Banks run marketing campaigns to promote term deposit subscriptions, but not every client converts. This project builds an end-to-end ML pipeline — from **exploratory data analysis** in a Jupyter notebook to a **live FastAPI web app** — that predicts subscription likelihood using client demographic and campaign data.

The trained **Random Forest** model is serialized with `joblib` and served through a clean Jinja2 HTML interface, with full **Docker support** for containerized deployment.

---

## ✨ Features

### 📊 Data & EDA (`Notebook_v1.ipynb`)
- Exploratory Data Analysis on the **Bank Marketing Dataset**
- Feature analysis: age, job, marital status, education, account balance, loan status, campaign interaction history
- Model comparison: **Random Forest**, **XGBoost**, **Gradient Boosting**
- Preprocessing pipeline design and evaluation metrics

### ⚙️ ML Pipeline (`train_rf.py`)
- Separate **numerical** and **categorical** preprocessing pipelines via `ColumnTransformer`
- Numerical features: mean imputation + standard scaling
- Categorical features: most-frequent imputation + one-hot encoding
- `LabelEncoder` for target variable (`yes` / `no`)
- Full `sklearn.Pipeline` chaining — preprocessing + classifier in one object
- Model and encoder serialized to `app/model.joblib` and `app/label_encoder.joblib`

### 🌐 FastAPI Web App (`app/`)
- Clean HTML form (Jinja2 templates) for entering client details
- Automatic preprocessing of user input through the saved pipeline
- Instant prediction with result display
- REST API endpoint for programmatic access
- Served via **Uvicorn** ASGI server

### 🐳 Docker Support *(Optional)*
- A `Dockerfile` is included for containerized deployment
- Runs on port `8000` inside the container
- Docker is **not required** — the app runs fully with just Uvicorn locally

---

## 🗂️ Project Structure

```
Term-Deposit-Prediction-App---Machine-Learning-Project/
│
├── app/
│   ├── main.py             # FastAPI app entry point
│   ├── model.joblib        # Trained Random Forest pipeline
│   └── label_encoder.joblib
│
├── data/
│   └── train.csv           # Bank Marketing Dataset
│
├── Notebook_v1.ipynb       # EDA, model comparison, training analysis
├── train_rf.py             # Model training + pipeline serialization script
├── Dockerfile              # Container definition
├── requirements.txt        # Python dependencies
└── .gitignore
```

---

## 🔢 Input Features

| Feature | Type | Description |
|---|---|---|
| `age` | Numerical | Client's age |
| `balance` | Numerical | Average yearly account balance (EUR) |
| `duration` | Numerical | Last contact duration (seconds) |
| `campaign` | Numerical | Number of contacts in current campaign |
| `pdays` | Numerical | Days since last contact from previous campaign |
| `previous` | Numerical | Number of contacts before this campaign |
| `job` | Categorical | Type of job |
| `marital` | Categorical | Marital status |
| `education` | Categorical | Education level |
| `default` | Categorical | Has credit in default? |
| `housing` | Categorical | Has housing loan? |
| `loan` | Categorical | Has personal loan? |
| `contact` | Categorical | Contact communication type |
| `poutcome` | Categorical | Outcome of previous campaign |

**Target:** Will the client subscribe to a term deposit? → `yes` / `no`

---

## ⚙️ Tech Stack

| Layer | Technology |
|---|---|
| ML Framework | Scikit-learn 1.2.2, XGBoost, Gradient Boosting |
| Model Serving | FastAPI, Uvicorn |
| Preprocessing | Pandas, NumPy 1.24.4 |
| Serialization | Joblib |
| Frontend | Jinja2 HTML Templates |
| Containerization | Docker |
| Notebook | Jupyter Notebook |
| Visualization | Matplotlib, Seaborn |

---

## 🚀 Getting Started

### Option 1 — Run Locally *(Recommended)*

```bash
# 1. Clone the repository
git clone https://github.com/21f3003095/Term-Deposit-Prediction-App---Machine-Learning-Project.git
cd Term-Deposit-Prediction-App---Machine-Learning-Project

# 2. Create and activate a virtual environment
python -m venv venv
source venv/bin/activate        # On Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Train the model (generates model.joblib and label_encoder.joblib)
python train_rf.py

# 5. Start the FastAPI app
uvicorn app.main:app --reload
```

Open your browser at: **`http://127.0.0.1:8000`**

---

### Option 2 — Run with Docker *(Optional)*

```bash
# Build the Docker image
docker build -t term-deposit-predictor .

# Run the container
docker run -p 8000:8000 term-deposit-predictor
```

Open your browser at: **`http://localhost:8000`**

---

## 🔄 ML Pipeline Flow

```
Raw CSV Data (train.csv)
        ↓
  Drop unused columns
        ↓
  Train / Test Split (80/20)
        ↓
  ColumnTransformer
  ├── Numerical  → Impute (mean) → StandardScaler
  └── Categorical → Impute (most_frequent) → OneHotEncoder
        ↓
  RandomForestClassifier
        ↓
  Evaluate on Test Set
        ↓
  Serialize → model.joblib + label_encoder.joblib
        ↓
  FastAPI loads model → Serves predictions via web form
```

---

## 📓 Notebook

The [`Notebook_v1.ipynb`](./Notebook_v1.ipynb) contains the full analytical workflow:
- Dataset overview and class distribution
- Feature correlation analysis
- EDA visualizations (Matplotlib, Seaborn)
- Comparison of Random Forest, XGBoost, and Gradient Boosting
- Final model selection rationale
