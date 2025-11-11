

## 🧠 **Topic: Data Standardization**

**Definition:**
Data Standardization is the process of transforming features (columns) in a dataset so that they have a *mean of 0* and a *standard deviation of 1*.
This helps machine learning models perform better because it ensures that all features contribute equally to the learning process — no single feature dominates due to a larger scale.

---

### 🧩 **Code Explanation**

---

### **1️⃣ Importing Required Libraries**

```python
import numpy as np
import pandas as pd
from sklearn.preprocessing import StandardScaler
from sklearn.model_selection import train_test_split
```

**Explanation:**

* `numpy (np)` → used for numerical operations.
* `pandas (pd)` → used to handle datasets easily (DataFrames).
* `StandardScaler` → a tool from `sklearn.preprocessing` to standardize data.
* `train_test_split` → used to divide the dataset into training and testing sets.

---

### **2️⃣ Loading the Dataset**

```python
import sklearn
dataset = sklearn.datasets.load_breast_cancer()
```

**Explanation:**

* The code imports the **Breast Cancer dataset** available in scikit-learn.
* `dataset` contains both **features** (input data) and **target** (labels: cancer or not).

---

### **3️⃣ Understanding the Dataset**

```python
print(dataset)
```

**Explanation:**
This prints the entire dataset as a dictionary-like object containing:

* `data`: the numeric feature values.
* `target`: the output labels (0 or 1).
* `feature_names`: column names of features.
* `DESCR`: description of the dataset.

---

### **4️⃣ Converting Data into a DataFrame**

```python
df = pd.DataFrame(dataset.data, columns=dataset.feature_names)
df.head()
```

**Explanation:**

* Converts the dataset into a pandas DataFrame for easier manipulation.
* `dataset.data` → feature matrix.
* `dataset.feature_names` → column names.
* `df.head()` → shows the first 5 rows to get an overview of the dataset.

---

### **5️⃣ Checking Dataset Shape**

```python
df.shape
```

**Explanation:**
Returns the number of **rows** (samples) and **columns** (features).
Example output: `(569, 30)` means 569 samples and 30 features.

---

### **6️⃣ Splitting Data and Labels**

```python
X = df
Y = dataset.target
```

**Explanation:**

* `X` contains all feature columns.
* `Y` contains the labels (target output: 0 = malignant, 1 = benign).

---

### **7️⃣ Displaying X and Y**

```python
print(X)
print(Y)
```

**Explanation:**
Shows the independent variables (features) and dependent variable (target).

---

### **8️⃣ Splitting into Training and Test Sets**

```python
X_train, X_test, Y_train, Y_test = train_test_split(X, Y, test_size=0.2, random_state=3)
```

**Explanation:**

* `train_test_split()` divides data into:

  * `X_train`, `Y_train`: used to train the model (80% of data)
  * `X_test`, `Y_test`: used to evaluate model (20% of data)
* `random_state=3` ensures the split is the same each time (reproducible results).

---

### **9️⃣ Checking Dataset Sizes**

```python
print(X.shape, X_train.shape, X_test.shape)
```

**Explanation:**
Confirms how the dataset is divided.
Example output might be: `(569, 30) (455, 30) (114, 30)` → total, train, test shapes.

---

### **🔟 Checking Original Data Standard Deviation**

```python
print(dataset.data.std())
```

**Explanation:**
Calculates the overall standard deviation of the original data.
Usually, before standardization, features have very different scales — e.g., one may vary from 1–10 and another from 1–1000.

---

### **11️⃣ Creating a StandardScaler Object**

```python
scaler = StandardScaler()
```

**Explanation:**
Creates a `StandardScaler` instance which can compute:

* The **mean** and **standard deviation** for each feature (during `.fit()`).
* The **standardized values** (during `.transform()`).

Formula applied:
[
z = \frac{(x - \text{mean})}{\text{standard deviation}}
]

---

### **12️⃣ Fitting the Scaler**

```python
scaler.fit(X_train)
```

**Explanation:**

* The scaler **learns** the mean and standard deviation from the training data only.
* It’s important to fit only on training data to avoid data leakage (test data must remain unseen during training).

---

### **13️⃣ Transforming Training Data**

```python
X_train_standradized = scaler.transform(X_train)
print(X_train_standradized)
```

**Explanation:**

* Transforms each feature of the training set using the formula mentioned above.
* After standardization:

  * Mean ≈ 0
  * Standard Deviation ≈ 1
* Prints the standardized training data (as NumPy array).

---

### **14️⃣ Transforming Test Data**

```python
X_test_standradized = scaler.transform(X_test)
print(X_test_standradized)
```

**Explanation:**

* Applies the same transformation learned from training data to the test set.
* This ensures consistency and fairness during model evaluation.

---

## 🧾 **Summary**

| Step              | Purpose                             |
| ----------------- | ----------------------------------- |
| Load data         | Get dataset into Python             |
| Create DataFrame  | Easier handling                     |
| Split Data        | Prevent overfitting                 |
| Fit Scaler        | Learn mean & std from training data |
| Transform Data    | Convert to standardized form        |
| Apply to Test Set | Ensure same scale for evaluation    |

---

