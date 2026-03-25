# **Handling Imbalanced Dataset — Documentation**

## **1. Introduction**

In many real-world machine learning problems, datasets are often **imbalanced**, meaning that one class significantly outnumbers the other. This imbalance can lead to biased models that perform well on the majority class but poorly on the minority class.

A common example is **fraud detection**, where fraudulent transactions are much rarer than legitimate ones.

---

## **2. Importing Dependencies**

The required libraries are imported for data manipulation and numerical computation:

```python
import numpy as np
import pandas as pd
```

* **NumPy**: Used for numerical operations.
* **Pandas**: Used for data loading and preprocessing.

---

## **3. Loading the Dataset**

The dataset is loaded into a Pandas DataFrame:

```python
credit_card_data = pd.read_csv('/content/credit_data.csv')
```

This dataset contains transaction records, including features and a target variable indicating whether a transaction is fraudulent or not.

---

## **4. Exploring the Dataset**

To understand the structure of the dataset:

```python
credit_card_data.head(5)
```

This displays the first five rows, helping to inspect:

* Feature columns
* Target variable
* Data format

---

## **5. Understanding Class Distribution**

In an imbalanced dataset:

* **Majority Class** → Normal transactions
* **Minority Class** → Fraudulent transactions

You typically check distribution like:

```python
credit_card_data['Class'].value_counts()
```

This reveals how skewed the dataset is.

---

## **6. Problem with Imbalanced Data**

If not handled properly:

* Model becomes biased toward majority class
* High accuracy but poor real-world performance
* Fails to detect minority class (important cases)

---

## **7. Separating Features and Target**

The dataset is divided into:

* **X (features)** → input variables
* **Y (target)** → output label

Example:

```python
X = credit_card_data.drop(columns='Class', axis=1)
Y = credit_card_data['Class']
```

---

## **8. Handling Imbalance (Undersampling)**

One common technique used here is **undersampling**.

### **Step 1: Separate Classes**

```python
legit = credit_card_data[credit_card_data.Class == 0]
fraud = credit_card_data[credit_card_data.Class == 1]
```

### **Step 2: Count Samples**

```python
print(legit.shape)
print(fraud.shape)
```

### **Step 3: Undersample Majority Class**

```python
legit_sample = legit.sample(n=len(fraud))
```

This randomly selects the same number of samples as the minority class.

### **Step 4: Combine Data**

```python
new_dataset = pd.concat([legit_sample, fraud], axis=0)
```

Now the dataset becomes **balanced**.

---

## **9. Verifying New Distribution**

```python
new_dataset['Class'].value_counts()
```

Both classes should now have equal representation.

---

## **10. Splitting Data**

The dataset is split into training and testing sets:

```python
from sklearn.model_selection import train_test_split

X = new_dataset.drop(columns='Class', axis=1)
Y = new_dataset['Class']

X_train, X_test, Y_train, Y_test = train_test_split(X, Y, test_size=0.2, random_state=2)
```

---

## **11. Model Training**

A machine learning model (e.g., Logistic Regression) is trained:

```python
from sklearn.linear_model import LogisticRegression

model = LogisticRegression()
model.fit(X_train, Y_train)
```

---

## **12. Model Evaluation**

Evaluate performance on:

* Training data
* Testing data

Example:

```python
from sklearn.metrics import accuracy_score

X_train_prediction = model.predict(X_train)
training_data_accuracy = accuracy_score(X_train_prediction, Y_train)

X_test_prediction = model.predict(X_test)
test_data_accuracy = accuracy_score(X_test_prediction, Y_test)
```

---
