### **Overview**

This notebook demonstrates several techniques for **handling missing (null) values** in a dataset. Missing values can distort data analysis and model performance, so it’s important to either replace (impute) or remove them carefully.
The notebook focuses on two main approaches:

1. **Imputation** – Filling missing values with a suitable replacement (mean, median, or mode).
2. **Dropping** – Removing rows or columns that contain missing values.

---

### **1. Importing the Required Libraries**

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

* **pandas** is used for data manipulation and handling datasets.
* **matplotlib** and **seaborn** are used for visualizing the data distributions to understand missing values and patterns.

---

### **2. Loading the Dataset**

```python
dataset = pd.read_csv('/content/Placement_Dataset.csv')
dataset.head()
dataset.shape
```

* The dataset (`Placement_Dataset.csv`) is loaded into a pandas DataFrame named `dataset`.
* `dataset.head()` displays the first few rows to preview the data.
* `dataset.shape` shows the number of rows and columns, giving an idea of dataset size.

---

### **3. Checking for Missing Values**

```python
dataset.isnull().sum()
```

This command counts how many null (missing) entries are in each column.
It helps identify where data is missing and which columns may need cleaning.

---

### **4. Analyzing Data Distribution**

```python
fig, ax = plt.subplots(figsize=(8, 8))
sns.distplot(dataset['salary'])
plt.show()
```

A histogram is plotted for the **`salary`** column to visualize how the data is distributed.
This helps in deciding whether to replace missing values using **mean**, **median**, or **mode**:

* If data is **normally distributed**, mean imputation is suitable.
* If it’s **skewed**, median imputation is more appropriate.

---

### **5. Imputation Methods**

#### **a. Replacing Missing Values with Median**

```python
dataset['salary'].fillna(dataset['salary'].median(), inplace=True)
```

* Fills all missing values in the `salary` column with the **median** salary.
* `inplace=True` updates the dataset directly.

#### **b. Alternative Methods (Commented Examples)**

```python
# dataset['salary'].fillna(dataset['salary'].mean(), inplace=True)
# dataset['salary'].fillna(dataset['salary'].mode(), inplace=True)
```

* **Mean** imputation replaces missing values with the column’s average.
* **Mode** imputation replaces them with the most frequent value.
* These lines are commented out as alternatives for demonstration.

#### **Verification**

```python
dataset.isnull().sum()
```

After imputation, this confirms that all missing values have been replaced.

---

### **6. Dropping Missing Values**

```python
salary_datasets = pd.read_csv('/content/Placement_Dataset.csv')
salary_datasets.isna().sum()
salary_datasets.dropna(how='any', inplace=True)
salary_datasets.isna().sum()
```

* Reloads the dataset to demonstrate the **dropping** approach separately.
* `dropna(how='any')` removes all rows containing **any** missing values.
* After dropping, `isna().sum()` confirms that no missing values remain.

---

### **7. Summary of Concepts**

| Method                | Description                                    | When to Use                                  |
| --------------------- | ---------------------------------------------- | -------------------------------------------- |
| **Mean Imputation**   | Replace missing value with the column average. | When data is normally distributed (no skew). |
| **Median Imputation** | Replace with the middle value.                 | When data is skewed or has outliers.         |
| **Mode Imputation**   | Replace with the most frequent value.          | When data is categorical.                    |
| **Dropping**          | Remove rows or columns with missing values.    | When missing data is minimal and random.     |

---

### **8. Visualization and Insights**

The use of **Seaborn’s distplot** helps visualize how imputation affects the dataset’s shape and whether it introduces bias. By comparing before and after plots, we can ensure the chosen imputation preserves the distribution as much as possible.

---

### **9. Final Takeaway**

This notebook provides a hands-on understanding of how to:

* Detect missing values.
* Choose the right imputation strategy based on data distribution.
* Alternatively drop missing records if appropriate.
* Validate changes using `isnull().sum()` or `isna().sum()`.

These preprocessing steps are essential before performing statistical analysis or training machine learning models.

---
