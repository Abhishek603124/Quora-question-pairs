# Duplicate Question Classifier (Quora Question Pairs)

This project implements a **binary classification model** to detect whether two questions are semantically similar or not. The dataset is sourced from a Quora question pairs dataset (public Kaggle dataset), and the model leverages extensive preprocessing, feature engineering, and machine learning algorithms (XGBoost & Random Forest) to achieve high accuracy.

---

## 📌 Problem Statement

Given two questions, determine whether they are duplicates — i.e., whether both questions are semantically equivalent even if worded differently. This is a classic **Natural Language Processing (NLP)** task often used in question-answering platforms to avoid redundant content.

---

## 📁 Dataset

- **Source**: [Question Pairs Dataset (Kaggle)](https://www.kaggle.com/datasets)
- **Files Used**:
  - `questions.csv`
- **Columns**:
  - `qid1`, `qid2`: unique IDs for the questions
  - `question1`, `question2`: the actual text of the questions
  - `is_duplicate`: target label (1 if duplicate, else 0)

---

## ⚙️ Workflow

### 1. Data Loading and Cleaning
- Loaded `questions.csv` using pandas.
- Handled missing values and checked for duplicates.

### 2. Text Preprocessing
- Lowercased text and removed special characters and HTML tags using `BeautifulSoup`.
- Replaced contractions (e.g., "can't" → "cannot") for text normalization.
- Removed mathematical tags (`[math]`) and other noise.

### 3. Feature Engineering
- Calculated:
  - Question lengths
  - Number of words
  - Number of common words between question pairs
  - Word share ratio between questions
- Vectorized both `question1` and `question2` using `CountVectorizer` (max 3000 features each).
- Concatenated all features into a final feature matrix of shape **(70000, 6008)**.

### 4. Modeling
- Split data using `train_test_split`.
- Trained two models:
  - ✅ **XGBoost Classifier**: Accuracy ~ **77.4%**
  - ✅ **Random Forest Classifier**: Accuracy ~ **78.3%**

---

## 🧪 Evaluation

| Model              | Accuracy  |
|-------------------|-----------|
| XGBoostClassifier | 77.4%     |
| RandomForest      | 78.3%     |

---

## 🛠️ Tech Stack

- **Language**: Python
- **Libraries**:
  - `pandas`, `numpy`, `seaborn`, `matplotlib`
  - `BeautifulSoup` (HTML cleaning)
  - `re` (Regex)
  - `scikit-learn`: CountVectorizer, classifiers, train-test split, metrics
  - `xgboost`: XGBClassifier

---

## 🚀 How to Run

1. Clone the repo:
   ```bash
   git clone https://github.com/yourusername/duplicate-question-classifier.git
   cd duplicate-question-classifier
