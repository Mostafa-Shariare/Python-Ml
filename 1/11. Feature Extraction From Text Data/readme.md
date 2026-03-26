# 📘 Feature Extraction of Text Data

## 1. Introduction

Feature extraction is a fundamental step in Natural Language Processing (NLP) and Machine Learning. It refers to the process of converting textual data into numerical (real-valued) vectors so that machine learning algorithms can understand and process it.

Since machine learning models cannot directly interpret raw text, feature extraction techniques are used to represent text in a structured numerical format.

---

## 2. Bag of Words (BoW)

### Definition

Bag of Words (BoW) is one of the simplest and most widely used techniques for text feature extraction. It represents text as a collection of words, ignoring grammar and word order but keeping track of word frequency.

### Key Idea

* Create a list of **unique words (vocabulary)** from the entire text corpus.
* Count how many times each word appears in a document.

### Example

#### Corpus:

```
Document 1: "I love machine learning"
Document 2: "Machine learning is fun"
```

#### Vocabulary:

```
[I, love, machine, learning, is, fun]
```

#### BoW Representation:

| Document | I | love | machine | learning | is | fun |
| -------- | - | ---- | ------- | -------- | -- | --- |
| Doc 1    | 1 | 1    | 1       | 1        | 0  | 0   |
| Doc 2    | 0 | 0    | 1       | 1        | 1  | 1   |

---

## 3. Term Frequency – Inverse Document Frequency (TF-IDF)

TF-IDF is an improved version of BoW that considers not only the frequency of words but also their importance.

---

### 3.1 Term Frequency (TF)

Term Frequency measures how frequently a term appears in a document.

[
TF(t) = \frac{\text{Number of times term } t \text{ appears in a document}}{\text{Total number of terms in the document}}
]

---

### 3.2 Inverse Document Frequency (IDF)

Inverse Document Frequency measures how important a word is across the entire corpus.

[
IDF(t) = \log\left(\frac{N}{n}\right)
]

Where:

* ( N ) = Total number of documents
* ( n ) = Number of documents containing the term ( t )

### Interpretation:

* Rare words → **High IDF**
* Frequent words → **Low IDF**

---

### 3.3 TF-IDF Formula

[
TF\text{-}IDF(t) = TF(t) \times IDF(t)
]

### Key Idea:

* Words that are frequent in a document but rare across documents get **higher importance**.
* Common words (like "is", "the") get **lower importance**.

---

## 4. Implementation using Scikit-learn

TF-IDF can be easily implemented using `TfidfVectorizer` from the `sklearn` library.

### Example Code:

```python
from sklearn.feature_extraction.text import TfidfVectorizer

# Sample text data
X = [
    "I love machine learning",
    "Machine learning is fun"
]

# Initialize vectorizer
vectorizer = TfidfVectorizer()

# Fit the model (learn vocabulary and IDF)
vectorizer.fit(X)

# Transform text into TF-IDF features
X_transformed = vectorizer.transform(X)

# Print result
print(X_transformed)
```

---

## 5. Workflow Explanation

1. **Initialize Vectorizer**

   * Create an instance of `TfidfVectorizer`.

2. **Fit**

   * Learns:

     * Vocabulary (unique words)
     * IDF values

3. **Transform**

   * Converts text data into TF-IDF feature vectors.

4. **Output**

   * Sparse matrix representing numerical features of text.

---

## 6. Advantages of TF-IDF

* Reduces importance of common words
* Highlights meaningful words
* Improves model performance compared to BoW
* Works well for text classification problems

---

## 7. Limitations

* Ignores word order (like BoW)
* Cannot capture semantic meaning
* High dimensional for large vocabulary

