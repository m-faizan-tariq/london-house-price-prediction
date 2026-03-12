# 🏠 London House Price Prediction: Machine Learning vs. Deep Learning

[![Python](https://img.shields.io/badge/Python-3.9+-blue.svg?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-2.0-150458?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.2-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![XGBoost](https://img.shields.io/badge/XGBoost-1.7-blueviolet?style=for-the-badge&logo=xgboost&logoColor=white)](https://xgboost.ai/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.12-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white)](https://www.tensorflow.org/)
[![Gradio](https://img.shields.io/badge/Gradio-3.0-orange?style=for-the-badge&logo=gradio&logoColor=white)](https://gradio.app/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)](https://jupyter.org/)

---

## 📖 Overview

Predicting house prices accurately in dynamic markets like London poses significant challenges
for traditional modelling techniques due to the non-linearity of influencing factors. This
project investigates the extent to which machine learning (ML) and deep learning (DL) models
improve short-term prediction accuracy for freehold houses in London. By merging HM Land
Registry Price Paid Data (PPD) with Energy Performance Certificate (EPC) datasets, the study
overcomes the feature deficiency of transactional records alone. Five models — Linear
Regression, Random Forest, XGBoost, Multi-Layer Perceptron (MLP), and Long Short-Term Memory
(LSTM) — were evaluated on a 2024 hold-out set to test temporal generalisation and
real-world applicability.

---

## 📊 Model Performance Results

Models were trained on historical data (2015–2023) and validated against a final
**2024 Hold-Out Set** to test robustness against temporal drift.

| Model | Test R² | 2024 Hold-Out R² | Status |
|---|---|---|---|
| **XGBoost Regressor** | **0.82** | **0.83** | 🏆 Best Model |
| Random Forest | 0.78 | 0.77 | ✅ Strong |
| MLP (Neural Network) | 0.75 | 0.74 | ⚡ Moderate |
| LSTM (Deep Learning) | 0.63 | 0.64 | ⚠️ Weak |
| Linear Regression | 0.55 | 0.59 | 📏 Baseline |

---

## 🗄️ Dataset

The project uses an integrated dataset formed by merging two public sources under the
**Open Government Licence v3.0**:

- **HM Land Registry PPD** — Transactional data: sale price, date, property type, and address
- **EPC Data (MHCLG)** — Physical characteristics: floor area, habitable rooms, energy
  efficiency rating, and built form

> **Data Engineering Challenge:** High-cardinality features (postcodes, streets) and memory
> constraints (>32GB RAM) were resolved using Label Encoding and ZRAM compression, enabling
> training on over a decade of London freehold property records.

---

## 📂 Project Structure

```text
london-house-price-prediction/
├── README.md              # Project documentation
├── index.html             # GitHub Pages portfolio site
├── main.py                # Gradio visualization tool & model logic
├── FPR.pdf                # Final Project Report (Full Thesis)
├── assets/                # Screenshots and visualisation images
└── notebooks/             # Data cleaning & model training scripts


## 🛠️ Installation & Requirements

Requires **Python 3.9+**

**1. Clone the repository:**
```bash
git clone https://github.com/mt23acy/london-house-price-prediction.git
cd london-house-price-prediction
```

**2. Install dependencies:**
```bash
pip install numpy pandas scikit-learn xgboost tensorflow gradio matplotlib
```

***

## 🚀 How to Run the Gradio Visualization Tool

The interactive tool allows address lookups to view historical sales and predict property
valuations using the optimised XGBoost model.

**1. Prepare the data** — Ensure `london_merged_df_filtered.csv` is in the root directory.

**2. Run the script:**
```bash
python main.py
```

**3. Open the UI** — Gradio will provide a local URL (e.g., `http://127.0.0.1:7860`)

**4. Use the tool:**
- Type a **Street Name** to filter the database
- Select **House Number (PAON)** and **Postcode** from dynamic dropdowns
- Click **"Get Prices & Predict Current"** for the historical price trend and AI valuation

***

## 💡 Key Findings

- **XGBoost Superiority** — Achieved R² of 0.83, proving its effectiveness on complex
  structured tabular data
- **Feature Integration Value** — Merging EPC data (floor area, habitable rooms) significantly
  boosted predictive power over PPD alone
- **Deep Learning vs. Ensembles** — LSTM underperformed Gradient Boosting for this tabular
  task, showing sequence modelling is not a silver bullet for real estate without tuning
- **Encoding Strategy** — Label Encoding was the necessary compromise over One-Hot Encoding
  due to London's high-cardinality geographical data
- **Temporal Robustness** — Near-identical Test and 2024 Hold-Out R² scores confirm the
  XGBoost model generalises well to unseen future market data

***

## 🔮 Future Work

- **Macroeconomic Features** — Incorporate interest rates, inflation, and proximity to
  tube stations and local amenities
- **Advanced Encoding** — Target Encoding or CatBoost Encoding to capture geographical
  nuances without artificial ordering
- **Spatial Architectures** — Graph Neural Networks (GNNs) to model relationships between
  neighbouring properties and postcodes
- **Hyperparameter Optimisation** — Bayesian Optimisation for finer tuning of XGBoost
  and MLP architectures

***

## 👤 Author

**Muhammad Faizan Tariq**  
MSc Data Science and Analytics — University of Hertfordshire (2025)

[
[
[

***

## 📜 License

- **Data:** [Open Government Licence v3.0](https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/)
  — Contains HM Land Registry & EPC data
- **Code:** MIT License — See `LICENSE` for details

***

*Muhammad Faizan Tariq | MSc Data Science and Analytics — University of Hertfordshire, 2025*
