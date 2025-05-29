# K-Nearest Neighbors (KNN) - A Complete Guide

## 📌 Introduction

K-Nearest Neighbors (KNN) is a **supervised machine learning algorithm** used for **classification** and **regression** problems. However, it's more commonly used for classification.

KNN is a **non-parametric**, **lazy learning** algorithm, meaning it doesn't assume any specific form of the function mapping input to output and doesn’t train a model in the traditional sense.

---

## 🚀 How Does KNN Work?

1. **Store** all the training data.
2. When a new input arrives:
   - **Calculate** the distance between the new input and all training samples.
   - **Select** the `K` nearest neighbors (data points with the smallest distance).
   - **Vote** (for classification) or **average** (for regression) based on these neighbors.
   - **Assign** the most common class (or average value) to the new input.

---

## 📏 Distance Metrics

K-Nearest Neighbors (KNN) determines similarity between data points based on **distance**. Choosing the right distance metric significantly affects the performance and accuracy of the model.

Below are the most common distance metrics used in KNN:

---

### ✅ Euclidean Distance (default for most cases)

**Formula:**

d(p, q) = sqrt((p1 - q1)^2 + (p2 - q2)^2 + ... + (pn - qn)^2)

**Explanation:**

- Measures the **straight-line distance** between two points in n-dimensional space.
- Best suited for continuous and normalized data.
- Most commonly used when features are on the same scale.

**Example:**

For points p = (2, 3) and q = (6, 7):

d = sqrt((2 - 6)^2 + (3 - 7)^2) = sqrt(16 + 16) = sqrt(32) ≈ 5.66

---

### ✅ Manhattan Distance

**Formula:**

d(p, q) = |p1 - q1| + |p2 - q2| + ... + |pn - qn|

**Explanation:**

- Also called **Taxicab** or **City Block** distance.
- Measures distance as the sum of absolute differences.
- Useful when movement is restricted to grid-like paths (e.g., city blocks).
- Less sensitive to outliers than Euclidean distance.

**Example:**

For points p = (2, 3) and q = (6, 7):

d = |2 - 6| + |3 - 7| = 4 + 4 = 8

---

### ✅ Minkowski Distance (generalized form)

**Formula:**

d(p, q) = (|p1 - q1|^p + |p2 - q2|^p + ... + |pn - qn|^p)^(1/p)

**Explanation:**

- A **generalized metric** that includes both Euclidean and Manhattan distances as special cases:
  - If p = 1 → Manhattan Distance
  - If p = 2 → Euclidean Distance
- Offers flexibility depending on the value of `p`.
- Can be tuned as a hyperparameter in models to improve accuracy.

**Example (p = 3):**

For points p = (2, 3) and q = (6, 7):

d = (|2 - 6|^3 + |3 - 7|^3)^(1/3) = (64 + 64)^(1/3) = (128)^(1/3) ≈ 5.04

---

### ⚠️ Note:

All distance metrics **except Hamming** require numerical input and are **sensitive to feature scale**. If your features have different ranges (e.g., age vs. income), use:

- **Normalization** (Min-Max Scaling)  
- or **Standardization** (Z-score Scaling)

to ensure meaningful distance comparisons.



## 🧠 Key Concepts

- **K (Number of Neighbors)**:  
  A hyperparameter that significantly affects model performance.
  - Small K → More sensitive to noise (high variance)
  - Large K → More stable but less flexible (high bias)

- **Lazy Learning**:  
  No explicit training phase; computation happens during prediction.

- **Feature Scaling**:  
  KNN is sensitive to the scale of the data. Apply normalization or standardization.

---

## 🔢 KNN Algorithm Steps (Classification)

1. Choose the number of neighbors `K`.
2. Calculate the distance between the test sample and all training samples.
3. Sort the distances and choose the K nearest neighbors.
4. Count the number of data points in each class among the K neighbors.
5. Assign the class with the highest count.

---

## 📊 Example (Intuition)

Imagine plotting fruit data with features like weight and color intensity. A new fruit is introduced. KNN looks at its "K" closest points and labels it based on the majority class.

If 3 out of 5 neighbors are apples, the new fruit is classified as an apple.

---

## 🟢 Advantages

- Simple and intuitive
- No training phase, so it’s fast for small datasets
- Works well with multi-class problems
- Adaptable to both classification and regression

---

## 🔴 Disadvantages

- Computationally expensive for large datasets
- Sensitive to irrelevant features and the scale of data
- Struggles with high-dimensional data (curse of dimensionality)
- Requires careful selection of K and distance metric

---

## 🧪 KNN for Regression

Instead of voting, take the **average (mean)** of the K nearest neighbors.

\[
\hat{y} = \frac{1}{K} \sum_{i=1}^{K} y_i
\]

---

## 📦 KNN in Python (Using scikit-learn)

```python
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.neighbors import KNeighborsClassifier
from sklearn.metrics import accuracy_score

# Load dataset
data = load_iris()
X, y = data.data, data.target

# Split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)

# Scale
scaler = StandardScaler()
X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)

# Model
knn = KNeighborsClassifier(n_neighbors=3)
knn.fit(X_train, y_train)

# Predict
y_pred = knn.predict(X_test)
print("Accuracy:", accuracy_score(y_test, y_pred))

# Accuracy

Accuracy= Total Number of Predictions / Number of Correct Predictions
​