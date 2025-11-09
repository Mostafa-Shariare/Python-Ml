## 🧠 **Detailed Notes on the Seaborn Notebook**

### **1–4. Importing Libraries**

```python
import seaborn as sns
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
```

These lines import the essential Python libraries:

* **Seaborn (sns)** – For statistical data visualization.
* **Matplotlib (plt)** – The base plotting library Seaborn builds on.
* **NumPy (np)** – For numerical operations and arrays.
* **Pandas (pd)** – For handling and manipulating tabular data.

---

### **5. Load the “Tips” Dataset**

```python
#total bill vs tip dataset
tips = sns.load_dataset('tips')
```

Loads Seaborn’s built-in **“tips”** dataset, which records restaurant bills, tips, gender, smoking status, day, time, and party size.

---

### **6. Display First 5 Rows**

```python
tips.head()
```

Shows the first five rows of the dataset, giving a quick view of its structure and columns.

---

### **7. Set Plot Theme**

```python
#setting a theme for the plots
sns.set_theme()
```

Applies Seaborn’s default theme (improving plot aesthetics). It sets consistent colors, gridlines, and background.

---

### **8. Visualize Relationship Between Variables**

```python
# visualize the data
sns.relplot(data=tips, x='total_bill', y='tip', col='time', hue='smoker', style='smoker', size='size')
```

Creates **multiple scatter plots**:

* **x-axis:** Total bill
* **y-axis:** Tip
* **col='time':** Creates separate plots for Lunch and Dinner
* **hue & style='smoker':** Differentiates smokers vs non-smokers by color and marker style
* **size='size':** Represents party size with point size

📊 *This helps analyze how total bill, tip, and smoking status vary by time.*

---

### **9–10. Load and Preview the “Iris” Dataset**

```python
# load the iris fataset
iris = sns.load_dataset('iris')
iris.head()
```

Loads and displays the famous **Iris dataset**, containing petal and sepal measurements for 3 flower species: *setosa, versicolor, virginica.*

---

### **11. Relational Plot for Iris**

```python
sns.relplot(data=iris, x='sepal_length', y='sepal_width', hue='species', style='species', col='species')
```

Creates multiple scatter plots (one for each species):

* X: Sepal length
* Y: Sepal width
* Hue/Style: Flower species
  Helps visualize differences among species.

---

### **12. Scatter Plot**

```python
sns.scatterplot(data=iris, x='sepal_length', y='sepal_width', hue='species')
```

A single scatter plot comparing sepal length vs width with color separation by species.

---

### **13. Another Scatter Plot**

```python
sns.scatterplot(x='sepal_length', y='petal_length', hue='species', data=iris)
```

Shows relation between **sepal length** and **petal length**.
*This plot usually shows clearer species separation.*

---

### **14–16. Titanic Dataset**

```python
# loading the titanic dataset
titanic = sns.load_dataset('titanic')
titanic.head()
titanic.shape
```

* Loads Seaborn’s **Titanic dataset** (passenger details, survival, etc.)
* Displays first few rows and the dataset shape.

---

### **17. Count Plot by Sex**

```python
sns.countplot(data=titanic, x='sex')
```

Shows the number of **male vs female** passengers.
Useful for categorical data frequency visualization.

---

### **18. Count Plot for Survival**

```python
sns.countplot(x='survived', data=titanic)
```

Shows how many passengers **survived (1)** vs **did not (0)**.

---

### **19. Bar Plot for Survival by Class and Sex**

```python
sns.barplot(x='sex', y='survived', hue='class', data=titanic)
```

Displays **average survival rate** across classes and gender.

* Bars represent mean survival probability.
* Shows patterns like “female first-class passengers had higher survival rates.”

---

### **20–21. Load California Housing Dataset**

```python
# house price dataset
from sklearn.datasets import fetch_california_housing

data = fetch_california_housing()
print(data.feature_names)
```

Loads the **California housing dataset** from scikit-learn and prints feature names such as:
`['MedInc', 'HouseAge', 'AveRooms', 'AveBedrms', 'Population', 'AveOccup', 'Latitude', 'Longitude']`

---

### **22–23. Convert to DataFrame and Add Target**

```python
house = pd.DataFrame(data.data, columns=data.feature_names)
house.head()

house['PRICE'] = data.target
```

* Converts the NumPy array to a Pandas DataFrame.
* Adds a new column `'PRICE'` representing **median house value** in each area.

---

### **24. Print the Dataset Object**

```python
print(data)
```

Displays full metadata of the scikit-learn dataset (features, description, etc.).

---

### **25. Distribution Plot**

```python
sns.displot(house['PRICE'])
```

Plots the **distribution of house prices** using a histogram with KDE (kernel density estimation).
It shows how prices are spread — often right-skewed (more low-price houses).

---

### **26. Correlation Matrix**

```python
correlation = house.corr()
```

Computes pairwise **correlation coefficients** between numerical features to measure how strongly variables are related (from -1 to +1).

---

### **27. Heatmap Visualization**

```python
plt.figure(figsize=(10,10))
sns.heatmap(correlation, cbar=True, square=True, fmt='.1f', annot=True, annot_kws={'size':8}, cmap='Blues')
```

Creates a **heatmap** of correlations:

* `annot=True` → displays values in each cell
* `fmt='.1f'` → one decimal precision
* `cmap='Blues'` → color tone
  Helps identify which features most influence house price (e.g., income or location).

---

### ✅ **Summary**

This notebook demonstrates:

1. How to use **Seaborn’s built-in datasets** (tips, iris, titanic).
2. How to visualize relationships using:

   * `relplot()`, `scatterplot()`, `countplot()`, `barplot()`, `displot()`, and `heatmap()`.
3. How to analyze data distributions and correlations in real datasets.

---
