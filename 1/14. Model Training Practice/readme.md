# 📘 Rock vs Mine Prediction System

### Logistic Regression-based Classification using Sonar Data

---

## 1. Introduction

This project implements a **binary classification system** to distinguish between **rocks (R)** and **mines (M)** using sonar signal data. The model is trained using **Logistic Regression**, a widely used supervised learning algorithm for classification tasks.

The dataset consists of numerical features representing sonar signal returns, and the goal is to predict whether an object is a rock or a mine.

---

## 2. Dependencies and Imports

```python
import numpy as np
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score
```

### Description

* **NumPy (`np`)**: Provides support for numerical computations and array operations.
* **Pandas (`pd`)**: Used for data manipulation and analysis.
* **train_test_split**: Splits dataset into training and testing subsets.
* **LogisticRegression**: Implements the logistic regression classification algorithm.
* **accuracy_score**: Evaluates model performance.

---

## 3. Data Loading

```python
sonar_data = pd.read_csv('/content/sonar data.csv', header=None)
```

### Description

* Loads the dataset into a **Pandas DataFrame**.
* `header=None` indicates that the dataset does not contain column names.

---

## 4. Data Exploration

### 4.1 Preview Dataset

```python
sonar_data.head()
```

Displays the first 5 rows of the dataset for quick inspection.

---

### 4.2 Dataset Shape

```python
sonar_data.shape
```

Returns:

* Number of rows (samples)
* Number of columns (features + label)

---

### 4.3 Statistical Summary

```python
sonar_data.describe()
```

Provides statistical measures such as:

* Mean
* Standard deviation
* Minimum and maximum values

---

### 4.4 Class Distribution

```python
sonar_data[60].value_counts()
```

### Description

* Column **60** represents the target label:

  * `'R'` → Rock
  * `'M'` → Mine
* This step checks whether the dataset is balanced.

---

### 4.5 Group-wise Feature Mean

```python
sonar_data.groupby(60).mean()
```

### Description

* Groups data by class label.
* Computes mean values for each feature per class.
* Helps identify patterns and differences between classes.

---

## 5. Data Preprocessing

### 5.1 Feature and Label Separation

```python
X = sonar_data.drop(columns=60, axis=1)
Y = sonar_data[60]
```

### Description

* **X (Features)**: All columns except column 60.
* **Y (Labels)**: Column 60 (target variable).

---

### 5.2 Data Inspection

```python
print(X)
print(Y)
```

Ensures that:

* Features and labels are correctly separated.

---

## 6. Train-Test Split

```python
X_train, X_test, Y_train, Y_test = train_test_split(
    X, Y, test_size=0.1, stratify=Y, random_state=1
)
```

### Parameters

* **test_size=0.1** → 10% data used for testing
* **stratify=Y** → Maintains class distribution
* **random_state=1** → Ensures reproducibility

---

### 6.1 Shape Verification

```python
print(X.shape, X_train.shape, X_test.shape)
```

Confirms:

* Correct data splitting proportions.

---

### 6.2 Training Data Preview

```python
print(X_train)
print(Y_train)
```

---

## 7. Model Initialization

```python
model = LogisticRegression()
```

### Description

* Initializes a **Logistic Regression classifier**.
* Suitable for binary classification tasks.

---

## 8. Model Training

```python
model.fit(X_train, Y_train)
```

### Description

* Trains the model using training data.
* Learns relationships between features and labels.

---

## 9. Model Evaluation

### 9.1 Training Accuracy

```python
X_train_prediction = model.predict(X_train)
training_data_accuracy = accuracy_score(X_train_prediction, Y_train)
```

```python
print('Accuracy on training data : ', training_data_accuracy)
```

### Description

* Predicts labels for training data.
* Measures how well the model fits training data.

---

### 9.2 Test Accuracy

```python
X_test_prediction = model.predict(X_test)
test_data_accuracy = accuracy_score(X_test_prediction, Y_test)
```

```python
print('Accuracy on test data : ', test_data_accuracy)
```

### Description

* Evaluates model performance on unseen data.
* Important for detecting overfitting.

---

## 10. Making Predictions on New Data

```python
input_data = (0.0307, 0.0523, ..., 0.0055)
```

### 10.1 Convert to NumPy Array

```python
input_data_as_numpy_array = np.asarray(input_data)
```

### 10.2 Reshape Input

```python
input_data_reshaped = input_data_as_numpy_array.reshape(1, -1)
```

### 10.3 Prediction

```python
prediction = model.predict(input_data_reshaped)
```

### 10.4 Output Interpretation

```python
if prediction[0] == 'R':
    print("The object is a Rock")
else:
    print("The object is a Mine")
```

---


Just tell me 👍
