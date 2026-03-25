# 📘 Data Splitting into Training and Testing Sets

## 1. Introduction

In supervised machine learning, a dataset is divided into separate subsets to train and evaluate a model. This process ensures that the model’s performance is assessed on unseen data, thereby providing a reliable estimate of its generalization capability.

---

## 2. Feature Matrix (X) and Target Vector (Y)

Before splitting the dataset, it is necessary to separate the input features and the target variable.

* **Feature Matrix (X):** Contains independent variables used for prediction
* **Target Vector (Y):** Contains the dependent variable (label)

### Steps to Obtain X and Y

Assume a dataset stored in a DataFrame:

```python
import pandas as pd

# Load dataset
data = pd.read_csv("data.csv")

# Display first few rows
print(data.head())
```

### Case 1: Target column is known

```python
# Example: predicting 'price'
X = data.drop(columns=['price'])   # all features
Y = data['price']                 # target variable
```

### Case 2: Using last column as target

```python
X = data.iloc[:, :-1]   # all columns except last
Y = data.iloc[:, -1]    # last column
```

---

## 3. Splitting the Dataset

The dataset is divided into:

* **Training Set:** Used to train the model
* **Testing Set:** Used to evaluate the model

This is commonly performed using the `train_test_split` function from **scikit-learn**.

---

## 4. Syntax of train_test_split

```python
from sklearn.model_selection import train_test_split

X_train, X_test, Y_train, Y_test = train_test_split(
    X, Y, test_size=0.2, random_state=2
)
```

---

## 5. Parameter Description

* **X:** Feature matrix
* **Y:** Target vector
* **test_size=0.2:** 20% of data allocated for testing
* **random_state=2:** Ensures reproducibility of the split

---

## 6. Demonstration Using a Sample Dataset

The following example uses a built-in dataset for clarity.

```python
from sklearn.datasets import load_iris
import pandas as pd

# Load dataset
iris = load_iris()

# Convert to DataFrame
data = pd.DataFrame(iris.data, columns=iris.feature_names)
data['target'] = iris.target

# Separate features and target
X = data.drop(columns=['target'])
Y = data['target']

# Split the dataset
from sklearn.model_selection import train_test_split

X_train, X_test, Y_train, Y_test = train_test_split(
    X, Y, test_size=0.2, random_state=2
)

# Display shapes
print("Training Features Shape:", X_train.shape)
print("Testing Features Shape:", X_test.shape)
```

---

## 7. Output Interpretation

* `X_train.shape` → Number of training samples and features
* `X_test.shape` → Number of testing samples and features

Example:

* `(120, 4)` → 120 samples, 4 features
* `(30, 4)` → 30 samples, 4 features

---

## 8. Workflow Summary

1. Load dataset
2. Identify target variable
3. Separate features (X) and target (Y)
4. Apply `train_test_split()`
5. Train model using training data
6. Evaluate model using testing data

---

