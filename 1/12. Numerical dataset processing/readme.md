# 📘 Numerical Dataset Processing Documentation

## 1. Introduction

Numerical dataset processing is a crucial step in the Machine Learning pipeline. It involves preparing raw numerical data into a structured and standardized format so that machine learning algorithms can learn effectively.

This documentation explains the step-by-step preprocessing of a numerical dataset using **Python**, **Pandas**, and **Scikit-learn**.

---

## 2. Importing Required Libraries

```python
import numpy as np
import pandas as pd
from sklearn.preprocessing import StandardScaler
from sklearn.model_selection import train_test_split
```

### Explanation

* **NumPy (`numpy`)** → Used for numerical computations
* **Pandas (`pandas`)** → Used for handling datasets (DataFrame)
* **StandardScaler** → Used for feature scaling (standardization)
* **train_test_split** → Used to divide dataset into training and testing sets

---

## 3. Loading the Dataset

```python
diabetes_dataset = pd.read_csv('diabetes.csv')
```

### Explanation

* The dataset is loaded from a CSV file into a Pandas DataFrame.
* Each row represents a data sample.
* Each column represents a feature.

---

## 4. Exploring the Dataset

```python
diabetes_dataset.head()
diabetes_dataset.shape
diabetes_dataset.describe()
```

### Explanation

* `head()` → Displays first 5 rows
* `shape` → Returns (rows, columns)
* `describe()` → Provides statistical summary:

  * Mean
  * Standard deviation
  * Min/Max values

---

## 5. Splitting Features and Target Variable

```python
X = diabetes_dataset.drop(columns='Outcome', axis=1)
Y = diabetes_dataset['Outcome']
```

### Explanation

* **X (Features):**

  * Contains all input variables
  * Example: glucose level, BMI, age, etc.

* **Y (Target):**

  * Contains output label (`Outcome`)
  * Typically:

    * `0` → Non-diabetic
    * `1` → Diabetic

👉 This separation is necessary because:

* ML models learn from **X**
* And predict **Y**

---

## 6. Data Standardization

```python
scaler = StandardScaler()
standardized_data = scaler.fit_transform(X)
X = standardized_data
```

### Explanation

Standardization transforms data so that:

* Mean = 0
* Standard Deviation = 1

### Why it is important:

* Prevents features with large values from dominating
* Improves model performance
* Helps faster convergence in training

---

## 7. Train-Test Split

```python
X_train, X_test, Y_train, Y_test = train_test_split(
    X, Y, test_size=0.2, random_state=2
)
```

### Explanation

* Dataset is divided into:

  * **Training Data (80%)**
  * **Testing Data (20%)**

### Parameters:

* `test_size=0.2` → 20% data for testing
* `random_state=2` → Ensures reproducibility

---

## 8. Verifying Data Split

```python
print(X.shape, X_train.shape, X_test.shape)
```

### Explanation

* Confirms:

  * Total dataset size
  * Training set size
  * Testing set size

---

## 9. Workflow Summary

The complete numerical data processing pipeline:

1. Import libraries
2. Load dataset
3. Explore dataset
4. Split into features (X) and labels (Y)
5. Standardize features
6. Split into training and testing sets

---

