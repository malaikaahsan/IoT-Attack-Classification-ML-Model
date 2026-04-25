# IoT Attack Classification ML Model

[![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)](https://www.python.org/)
[![Jupyter Notebook](https://img.shields.io/badge/jupyter-%23FA0F00.svg?style=for-the-badge&logo=jupyter&logoColor=white)](https://jupyter.org/)
[![Scikit-Learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![LightGBM](https://img.shields.io/badge/LightGBM-%2300BFFF.svg?style=for-the-badge&logo=microsoft&logoColor=white)](https://lightgbm.readthedocs.io/)
[![XGBoost](https://img.shields.io/badge/XGBoost-%23FF6600.svg?style=for-the-badge&logo=xgboost&logoColor=white)](https://xgboost.readthedocs.io/)

A machine learning project for classifying IoT network cyberattacks into 10 categories using a structured, multi-phase methodology. Built on a dataset of 211,000+ network traffic records with 44 features, this project covers the full ML pipeline — from data exploration to feature engineering, model training, and performance optimization.

---

## 📌 Problem Statement

IoT devices are increasingly targeted by cyberattacks such as DDoS, ransomware, MITM, and more. Detecting and classifying these attacks from raw network traffic is a critical challenge in cybersecurity. This project builds a multi-class classifier that can identify the type of attack from network behavior features.

---

## 📂 Project Structure

The project is organized across 4 progressive phases:

| Notebook | Phase | Description |
|---|---|---|
| `iot-ml-model.ipynb` | Phase 1 & 2 | Data loading, EDA, and preprocessing |
| `feature-engineering-phase3.ipynb` | Phase 3 | Feature importance analysis and feature engineering |
| `phase4-methodology.ipynb` | Phase 4 | Model training and evaluation |
| `phase5-improved-methodology.ipynb` | Phase 5 | Improvements: class imbalance handling and feature selection |

---

## 📊 Dataset

- **Source:** IoT Network Traffic Dataset (via Kaggle)
- **Size:** 211,000+ records, 44 features
- **Target:** `type` — 10 attack/traffic classes

| Class | Description |
|---|---|
| Normal | Legitimate network traffic (~23.7%) |
| DDoS | Distributed Denial of Service |
| DoS | Denial of Service |
| Backdoor | Unauthorized remote access |
| Injection | Code/SQL injection attacks |
| Password | Password brute-force attacks |
| Scanning | Network scanning/reconnaissance |
| Ransomware | Ransomware activity |
| XSS | Cross-site scripting attacks |
| MITM | Man-in-the-middle attacks (~0.49%) |

> ⚠️ **Class Imbalance:** MITM attack is significantly underrepresented (~0.49%), which was addressed in Phase 5.

---

## 🔧 Methodology

### Phase 1 & 2 — EDA & Preprocessing
- Loaded and explored the dataset (shape, dtypes, null checks, statistics)
- Visualized class distributions, feature histograms, boxplots, and correlation heatmap
- Dropped irrelevant high-cardinality text columns: IP addresses, HTTP user agents, DNS queries, SSL fields

### Phase 3 — Feature Engineering
- Used 5 algorithms (Random Forest, Extra Trees, Logistic Regression, LightGBM, XGBoost) for feature importance analysis
- Engineered 9 new meaningful features:
  - **Traffic Ratios:** `bytes_ratio`, `ip_bytes_ratio`
  - **Packet Behavior:** `pkts_ratio`
  - **Total Traffic:** `total_bytes`, `total_ip_bytes`
  - **Traffic Efficiency:** `bytes_per_pkt`, `bytes_per_second`
  - **Port Interaction:** `port_sum`, `port_diff`
  - **Suspicious Behavior Indicator:** `high_traffic_flag`

### Phase 4 — Model Training & Evaluation
- Split data: 80% training / 20% testing
- Trained 3 models:
  - **LightGBM** (primary model)
  - **Random Forest** (comparison)
  - **Logistic Regression** (baseline)
- Evaluated using accuracy, precision, recall, F1-score, and confusion matrix

### Phase 5 — Improvements
- **Class Imbalance Handling:** Applied `compute_class_weight('balanced')` to give more importance to minority classes like MITM
- **Feature Selection:** Selected top 15 most important features to reduce dimensionality and noise
- **IoT Attack Risk Indicator:** Added a `attack_risk` prediction column to the dataset for real-world interpretability

---

## 🤖 Models Used

| Model | Type | Purpose |
|---|---|---|
| LightGBM | Gradient Boosting | Primary classifier |
| Random Forest | Ensemble (Bagging) | Performance comparison |
| Extra Trees | Ensemble | Feature importance |
| XGBoost | Gradient Boosting | Feature importance |
| Logistic Regression | Linear | Baseline model |

---

## 📈 Results

| Model | Notes |
|---|---|
| LightGBM (baseline) | High accuracy, struggled with MITM minority class |
| LightGBM (improved) | Better recall on minority classes with class weights |
| LightGBM (top 15 features) | Improved generalization and reduced noise |

> The final improved model addresses class imbalance and feature redundancy, making it more suitable for real-world IoT security applications.

---

## 🛠️ Tech Stack

- **Language:** Python 3
- **Environment:** Jupyter Notebook / Kaggle Notebooks
- **Libraries:**
  - `pandas`, `numpy` — Data manipulation
  - `matplotlib`, `seaborn` — Visualization
  - `scikit-learn` — Preprocessing, model evaluation, class weights
  - `lightgbm` — Primary ML model
  - `xgboost` — Feature importance analysis

---

## 🚀 How to Run

1. Clone the repository:
```bash
git clone https://github.com/malaikaahsan/IoT-Attack-Classification-ML-Model.git
cd IoT-Attack-Classification-ML-Model
```

2. Install dependencies:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn lightgbm xgboost
```

3. Run the notebooks in order:
```
1. iot-ml-model.ipynb
2. feature-engineering-phase3.ipynb
3. phase4-methodology.ipynb
4. phase5-improved-methodology.ipynb
```

> **Note:** This project was originally developed on Kaggle. Dataset paths may need to be updated if running locally.

---

## 💡 Key Learnings

- How to handle **class imbalance** in multi-class classification using class weights
- How to perform **feature importance analysis** using multiple ML algorithms
- How to engineer **domain-specific features** from raw network traffic data
- Comparison of **tree-based ensemble models** for cybersecurity classification tasks

---

## 👩‍💻 Author

**Malaika Ahsan**  
BS Computer Science — PUCIT, Lahore  
[GitHub](https://github.com/malaikaahsan)
