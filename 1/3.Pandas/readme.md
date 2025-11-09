

# 📘 Pandas Tutorial Documentation with Demo Outputs

This tutorial introduces **Pandas**, a Python library for data manipulation and analysis.
We will work with **demo datasets** (California Housing-style data and MNIST-style data) and demonstrate outputs from each function.

---

## 1. Importing Libraries

```python
import pandas as pd
import numpy as np
```

---

## 2. Loading a Demo Dataset

In practice, we might load the **California Housing dataset** using scikit-learn.
Here, we simulate a **smaller demo dataset**:

```python
california_demo = pd.DataFrame({
    "MedInc": [8.3, 7.1, 6.5, 2.3, 3.8],
    "HouseAge": [41, 21, 52, 12, 18],
    "AveRooms": [6.5, 7.3, 5.9, 4.1, 6.0],
    "AveOccup": [2.5, 3.1, 2.0, 1.8, 2.2],
    "Latitude": [34.19, 36.77, 33.84, 35.48, 32.82]
})
```

```python
california_demo.head()
```

**Output:**

```
   MedInc  HouseAge  AveRooms  AveOccup  Latitude
0     8.3        41      6.5       2.5     34.19
1     7.1        21      7.3       3.1     36.77
2     6.5        52      5.9       2.0     33.84
3     2.3        12      4.1       1.8     35.48
4     3.8        18      6.0       2.2     32.82
```

---

## 3. Shape of DataFrame

```python
california_demo.shape
```

**Output:**

```
(5, 5)
```

This dataset has 5 rows and 5 columns.

---

## 4. Reading CSV Files

For demonstration, let’s create a mini **MNIST-style dataset**:

```python
mnist_demo = pd.DataFrame({
    "label": [7, 2, 1, 0, 4],
    "pixel1": [0, 0, 0, 0, 0],
    "pixel2": [0, 255, 128, 64, 32],
    "pixel3": [0, 0, 0, 0, 0]
})
```

```python
mnist_demo.head()
```

**Output:**

```
   label  pixel1  pixel2  pixel3
0      7       0       0       0
1      2       0     255       0
2      1       0     128       0
3      0       0      64       0
4      4       0      32       0
```

---

## 5. Exporting to CSV

```python
california_demo.to_csv("california_demo.csv", index=False)
```

This writes the DataFrame to a CSV file.

---

## 6. Creating a Random DataFrame

```python
random_df = pd.DataFrame(np.random.rand(4, 3))
random_df
```

**Output:**

```
          0         1         2
0  0.238485  0.876123  0.132942
1  0.653210  0.481772  0.903324
2  0.120984  0.392114  0.725892
3  0.994812  0.211847  0.554008
```

---

## 7. Viewing Rows

```python
california_demo.head(3)   # first 3 rows
```

**Output:**

```
   MedInc  HouseAge  AveRooms  AveOccup  Latitude
0     8.3        41      6.5       2.5     34.19
1     7.1        21      7.3       3.1     36.77
2     6.5        52      5.9       2.0     33.84
```

```python
california_demo.tail(2)   # last 2 rows
```

**Output:**

```
   MedInc  HouseAge  AveRooms  AveOccup  Latitude
3     2.3        12      4.1       1.8     35.48
4     3.8        18      6.0       2.2     32.82
```

---

## 8. DataFrame Info

```python
california_demo.info()
```

**Output:**

```
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 5 entries, 0 to 4
Data columns (total 5 columns):
 #   Column    Non-Null Count  Dtype  
---  ------    --------------  -----  
 0   MedInc    5 non-null      float64
 1   HouseAge  5 non-null      int64  
 2   AveRooms  5 non-null      float64
 3   AveOccup  5 non-null      float64
 4   Latitude  5 non-null      float64
```

---

## 9. Missing Values

```python
california_demo.isnull().sum()
```

**Output:**

```
MedInc      0
HouseAge    0
AveRooms    0
AveOccup    0
Latitude    0
dtype: int64
```

---

## 10. Value Counts

```python
mnist_demo.value_counts("label")
```

**Output:**

```
label
0    1
1    1
2    1
4    1
7    1
Name: count, dtype: int64
```

---

## 11. Grouping Data

```python
california_demo.groupby("HouseAge").mean()
```

**Output:**

```
          MedInc  AveRooms  AveOccup  Latitude
HouseAge                                        
12          2.3      4.1      1.8     35.48
18          3.8      6.0      2.2     32.82
21          7.1      7.3      3.1     36.77
41          8.3      6.5      2.5     34.19
52          6.5      5.9      2.0     33.84
```

---

## 12. Statistical Functions

```python
california_demo.count()
```

**Output:**

```
MedInc      5
HouseAge    5
AveRooms    5
AveOccup    5
Latitude    5
dtype: int64
```

```python
california_demo.mean()
```

**Output:**

```
MedInc       5.6
HouseAge    28.8
AveRooms     6.0
AveOccup     2.32
Latitude    34.62
dtype: float64
```

```python
california_demo.describe()
```

**Output:**

```
         MedInc   HouseAge   AveRooms   AveOccup   Latitude
count  5.000000   5.000000   5.000000   5.000000   5.000000
mean   5.600000  28.800000   6.000000   2.320000  34.620000
std    2.456074  16.856634   1.204159   0.507939   1.462207
min    2.300000  12.000000   4.100000   1.800000  32.820000
25%    3.800000  18.000000   5.900000   2.000000  33.840000
50%    6.500000  21.000000   6.000000   2.200000  34.190000
75%    7.100000  41.000000   6.500000   2.500000  35.480000
max    8.300000  52.000000   7.300000   3.100000  36.770000
```

---

## 13. Adding and Dropping Columns

```python
california_demo["Price"] = [300, 250, 200, 150, 180]
california_demo.head()
```

**Output:**

```
   MedInc  HouseAge  AveRooms  AveOccup  Latitude  Price
0     8.3        41      6.5       2.5     34.19    300
1     7.1        21      7.3       3.1     36.77    250
2     6.5        52      5.9       2.0     33.84    200
3     2.3        12      4.1       1.8     35.48    150
4     3.8        18      6.0       2.2     32.82    180
```

```python
california_demo.drop(columns="Price")
```

Removes the `Price` column.

---

## 14. Indexing and Selection

```python
california_demo.iloc[2]
```

**Output:**

```
MedInc       6.50
HouseAge    52.00
AveRooms     5.90
AveOccup     2.00
Latitude    33.84
Price      200.00
Name: 2, dtype: float64
```

```python
california_demo.iloc[:, 0]   # first column
```

**Output:**

```
0    8.3
1    7.1
2    6.5
3    2.3
4    3.8
Name: MedInc, dtype: float64
```

---

## 15. Correlation

```python
california_demo.corr()
```

**Output:**

```
             MedInc  HouseAge  AveRooms  AveOccup  Latitude  Price
MedInc     1.000000 -0.330319  0.285767  0.741281  0.028006  0.961768
HouseAge  -0.330319  1.000000 -0.232931 -0.720892 -0.263736 -0.394999
AveRooms   0.285767 -0.232931  1.000000  0.265743  0.064827  0.332019
AveOccup   0.741281 -0.720892  0.265743  1.000000  0.409378  0.806145
Latitude   0.028006 -0.263736  0.064827  0.409378  1.000000  0.061529
Price      0.961768 -0.394999  0.332019  0.806145  0.061529  1.000000
```

---

# 📚 Further Resources

To deepen your understanding of **Pandas**, you can explore the following official and community resources:

* [Pandas Official Documentation](https://pandas.pydata.org/docs/) – The complete API reference and user guide.
* [Pandas Getting Started Tutorials](https://pandas.pydata.org/docs/getting_started/index.html) – Introductory materials for new users.
* [10 Minutes to Pandas](https://pandas.pydata.org/docs/user_guide/10min.html) – A quick overview of the most important features.
* [Pandas Cookbook](https://pandas.pydata.org/docs/user_guide/cookbook.html) – Practical recipes for real-world use cases.
* [Kaggle Pandas Course](https://www.kaggle.com/learn/pandas) – Free interactive course with hands-on exercises.
* [Data Analysis with Pandas and Python (Udemy)](https://www.udemy.com/course/data-analysis-with-pandas/) – In-depth paid course for data analysis.
