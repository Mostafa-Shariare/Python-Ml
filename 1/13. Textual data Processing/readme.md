

# 📘 Textual Data Processing Documentation

## 1. Overview

Textual Data Processing is a fundamental step in Natural Language Processing (NLP) that involves transforming raw text into a structured format suitable for machine learning models.

This workflow demonstrates how to:

* Load textual data
* Clean and preprocess text
* Apply stemming and stopword removal
* Convert text into numerical feature vectors using TF-IDF

---

## 2. Dependencies

The following libraries are required:

```python
import numpy as np
import pandas as pd
import re
import nltk
from nltk.corpus import stopwords
from nltk.stem.porter import PorterStemmer
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.model_selection import train_test_split
```

### Download Required Resources

```python
nltk.download('stopwords')
```

---

## 3. Stopwords

### Definition

Stopwords are commonly used words (e.g., *the, is, and, in*) that do not carry significant meaning for text analysis and are often removed.

### Example

```python
print(stopwords.words('english'))
```

---

## 4. Data Loading

The dataset is loaded using Pandas:

```python
news_dataset = pd.read_csv(
    '/content/fake_news_dataset.csv',
    engine='python',
    on_bad_lines='skip'
)
```

### Dataset Description

* `label = 0` → Real News
* `label = 1` → Fake News

---

## 5. Data Inspection

### View Dataset

```python
news_dataset.head()
```

### Check Shape

```python
news_dataset.shape
```

### Check Missing Values

```python
news_dataset.isnull().sum()
```

---

## 6. Data Preprocessing

### 6.1 Handling Missing Values

Missing values are replaced with empty strings:

```python
news_dataset = news_dataset.fillna('')
```

---

### 6.2 Feature Engineering

A new column `content` is created by combining `author` and `title`:

```python
news_dataset['content'] = news_dataset['author'] + ' ' + news_dataset['title']
```

---

### 6.3 Splitting Features and Target

```python
X = news_dataset.drop(columns='label', axis=1)
Y = news_dataset['label']
```

---

## 7. Text Normalization (Stemming)

### Definition

Stemming reduces words to their root form.

Example:

* *running → run*
* *played → play*

---

### 7.1 Initialize Stemmer

```python
port_stem = PorterStemmer()
```

---

### 7.2 Stemming Function

```python
def stemming(content):
    stemmed_content = re.sub('[^a-zA-Z]', ' ', content)
    stemmed_content = stemmed_content.lower()
    stemmed_content = stemmed_content.split()
    stemmed_content = [
        port_stem.stem(word)
        for word in stemmed_content
        if not word in stopwords.words('english')
    ]
    stemmed_content = ' '.join(stemmed_content)
    return stemmed_content
```

---

### 7.3 Apply Stemming

```python
news_dataset['content'] = news_dataset['content'].apply(stemming)
```

---

## 8. Final Feature and Target Extraction

```python
X = news_dataset['content'].values
Y = news_dataset['label'].values
```

---

## 9. Feature Extraction using TF-IDF

### Definition

TF-IDF (Term Frequency - Inverse Document Frequency) converts text into numerical vectors based on word importance.

---

### 9.1 Initialize Vectorizer

```python
vectorizer = TfidfVectorizer()
```

---

### 9.2 Fit and Transform

```python
vectorizer.fit(X)
X = vectorizer.transform(X)
```

---

### Output

* `X` becomes a sparse matrix of numerical features
* Each column represents a word
* Values indicate importance of words in documents

---

## 10. Final Output

```python
print(X)
```

* Shape: `(number_of_samples, number_of_features)`
* Ready for machine learning models

---

## 11. Summary of Workflow

1. Import libraries
2. Load dataset
3. Handle missing values
4. Combine text features
5. Remove stopwords
6. Apply stemming
7. Convert text to numerical vectors (TF-IDF)

---

## 12. Key Concepts

| Concept       | Description                                    |
| ------------- | ---------------------------------------------- |
| Stopwords     | Common words removed from text                 |
| Stemming      | Reducing words to root form                    |
| TF-IDF        | Converts text into weighted numerical features |
| Preprocessing | Cleaning and structuring raw data              |

---

