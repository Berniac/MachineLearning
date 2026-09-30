# 🤖 Machine Learning

**Author:** Bernard Mwamburi  
**Repository:** [Berniac/MachineLearning](https://github.com/Berniac/MachineLearing)  
**Language:** Python (Jupyter Notebooks)

---

## 📖 Overview

This repository contains all coursework for a Machine Learning course, including four progressive homework assignments and a comprehensive final project. Each assignment is implemented as a Jupyter Notebook (`.ipynb`), combining code, visualizations, and written analysis in a single interactive document.

---

## 📁 Repository Structure

```
MachineLearing/
│
├── Data Exploration and Preprocessing/   →  Data Exploration & Preprocessing
├── Supervised Learning/   →  Supervised Learning — Regression & Classification
├── Model Evaluation and Optimization/   →  Model Evaluation & Optimization
├── Unsupervised Learning/   →  Unsupervised Learning & Dimensionality Reduction
├── End-to-End ML Projects/   →  End-to-End ML Pipeline
└── README.md
```

---

## 📂 Elements

### `Data Exploration and Preprocessing`
Introduction to machine learning workflows. Topics covered include loading and inspecting datasets, handling missing values, feature engineering, and basic statistical analysis to prepare data for modeling.

### `Supervised Learning` - Regression & Classification
Implementation and evaluation of core supervised learning algorithms. Covers linear and logistic regression, decision trees, and performance metrics such as accuracy, precision, recall, and mean squared error.

### `Model Evaluation and Optimization'
Deep dive into model selection and performance tuning. Topics include cross-validation, bias-variance tradeoff, hyperparameter tuning with grid search, and regularization techniques (L1/L2).

### `Unsupervised Learning` Dimensionality Reduction
Exploration of unsupervised approaches. Covers clustering algorithms (e.g., K-Means), principal component analysis (PCA), and techniques for visualizing high-dimensional data.

---


`End-to-End ML Projects`

An end-to-end machine learning project that demonstrates the full data science pipeline — from raw data ingestion and exploratory data analysis (EDA), through feature engineering and model training, to evaluation and interpretation of results. The project synthesizes concepts from all four elements.

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| Python 3 | Primary programming language |
| Jupyter Notebook | Interactive development environment |
| NumPy & Pandas | Data manipulation and analysis |
| Matplotlib & Seaborn | Data visualization |
| Scikit-learn | Machine learning algorithms and utilities |

---

## 🚀 Getting Started

### Prerequisites
Make sure you have Python 3 and Jupyter installed. You can install the required libraries with:

```bash
pip install numpy pandas matplotlib seaborn scikit-learn jupyter
```

### Running the Notebooks
1. Clone the repository:
   ```bash
   git clone https://github.com/Berniac/MachineLearning.git
   cd MachineLearning
   ```
2. Launch Jupyter:
   ```bash
   jupyter notebook
   ```
3. Open any `.ipynb` file from the folder of your choice.

---

## 📌 Notes

- All notebooks are self-contained and include markdown explanations alongside the code.

---

## 📦 Datasets

Some datasets are too large to keep in the repository, and two files (`diamonds.csv`, `census.csv`) are empty placeholders. Download each missing file and save it **in the same folder as the notebook that loads it**, under the filename shown below, since the notebooks read them with relative paths.

| Notebook folder | File | Status | Source |
|---|---|---|---|
| `Data Exploration and Preprocessing` | `boston_housing.csv` | ✅ included | — |
| `Data Exploration and Preprocessing` | `diamonds.csv` | ⚠️ empty, replace | [seaborn-data `diamonds.csv`](https://raw.githubusercontent.com/mwaskom/seaborn-data/master/diamonds.csv) (same data as [Kaggle: Diamonds](https://www.kaggle.com/datasets/shivam2503/diamonds)) |
| `Supervised Learning` | `breast_cancer.csv`, `mobile.csv`, `boston_housing.csv` | ✅ included | — |
| `Model Evaluation and Optimization` | `census.csv` | ⚠️ empty, replace | [UCI Adult / Census Income](https://archive.ics.uci.edu/dataset/2/adult) (`adult.data`, 32,561 rows) |
| `Model Evaluation and Optimization` | `census_new.csv` | ✅ included | — |
| `Unsupervised Learning` | `train.csv`, `test.csv` | ❌ missing | [Kaggle: Digit Recognizer (MNIST)](https://www.kaggle.com/c/digit-recognizer/data) |
| `End-to-End ML Projects` | `e-commerce_transaction_data.csv` | ❌ missing | [Kaggle: Fraudulent E-Commerce Transactions](https://www.kaggle.com/datasets/shriyashjagtap/fraudulent-e-commerce-transactions) (`Fraudulent_E-Commerce_Transaction_Data.csv`, the larger ~1.47M-row file) |

### Setup steps

Run these from the repository root. The Kaggle commands need the [Kaggle CLI](https://github.com/Kaggle/kaggle-api) (`pip install kaggle`) with an API token in `~/.kaggle/kaggle.json`.

**Diamonds** (direct download, the columns match the notebook exactly):

```bash
curl -L -o "Data Exploration and Preprocessing/diamonds.csv" \
  https://raw.githubusercontent.com/mwaskom/seaborn-data/master/diamonds.csv
```

**Census** (the raw UCI file has no header row, so rename the columns to what the notebook expects):

```python
import pandas as pd

cols = ['age', 'workclass', 'fnlwgt', 'education', 'educ_num', 'marital_status',
        'occupation', 'relationship', 'race', 'sex', 'capital_gain', 'capital_loss',
        'hrs_per_week', 'native_country', 'income']
url = 'https://archive.ics.uci.edu/ml/machine-learning-databases/adult/adult.data'
census = pd.read_csv(url, header=None, names=cols, skipinitialspace=True, na_values='?')
census.to_csv('Model Evaluation and Optimization/census.csv', index=False)
```

**MNIST digits** (accept the competition rules on the Kaggle page first):

```bash
kaggle competitions download -c digit-recognizer -p "Unsupervised Learning"
unzip -o "Unsupervised Learning/digit-recognizer.zip" train.csv test.csv -d "Unsupervised Learning"
```

**E-commerce fraud transactions:**

```bash
kaggle datasets download -d shriyashjagtap/fraudulent-e-commerce-transactions -p "End-to-End ML Projects" --unzip
mv "End-to-End ML Projects/Fraudulent_E-Commerce_Transaction_Data.csv" \
   "End-to-End ML Projects/e-commerce_transaction_data.csv"
```

> The census and e-commerce files used in the course may have been lightly cleaned, so results from a fresh download can differ slightly from the saved notebook outputs.
