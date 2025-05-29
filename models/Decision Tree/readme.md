# Decision Trees - Machine Learning Explained

## 📄 What is a Decision Tree?

A **Decision Tree** is a supervised machine learning algorithm that can be used for both **classification** and **regression** tasks. It mimics human decision-making using a tree-like structure of decisions and their possible consequences.

---

## 🌳 Intuition

Think of playing a guessing game like **"20 Questions"**:

* Is it an animal?
* Is it bigger than a loaf of bread?
* Does it live in water?

Each question helps you narrow down the possibilities. A decision tree works similarly: it asks a series of **yes/no** or **threshold** based questions to reach a decision.

---

## 🌐 Real-World Example: Movie Recommendation

Suppose you're recommending movies:

* Is the movie's genre "Action"?
* Does it have a rating above 8?
* Was it released after 2010?

Each question helps filter the dataset and leads to a decision (recommend or not).

---

## 🧹 Key Terminology

* **Root Node**: The first question or split.
* **Decision Node**: A node that asks a question.
* **Leaf/Terminal Node**: The final output (a class or value).
* **Branch**: The outcome of a split.

---

## ⚖️ How Does It Decide the Splits?

The tree chooses the best feature and threshold to split data based on a metric:

### ✅ For Classification:

* **Gini Impurity**
* **Entropy (Information Gain)**

### 📈 For Regression:

* **Mean Squared Error (MSE)**
* **Mean Absolute Error (MAE)**

### Gini Impurity Formula:

```math
Gini = 1 - ∑ p_i^2
```

Where `p_i` is the probability of class `i` in a node.

Lower Gini ➔ better purity ➔ better split.

---

## 🔧 How to Build a Decision Tree in Python (Scikit-Learn)

```python
from sklearn.datasets import load_iris
from sklearn.tree import DecisionTreeClassifier
from sklearn import tree
import matplotlib.pyplot as plt

# Load data
iris = load_iris()
X, y = iris.data, iris.target

# Build model
clf = DecisionTreeClassifier(criterion='gini', max_depth=3)
clf.fit(X, y)

# Visualize the tree
plt.figure(figsize=(12, 8))
tree.plot_tree(clf, filled=True, feature_names=iris.feature_names, class_names=iris.target_names)
plt.show()
```

---

## ❗ Pros and Cons

### ✅ Advantages:

* Easy to understand and interpret
* No feature scaling needed
* Can handle numerical and categorical data

### ❌ Disadvantages:

* Prone to overfitting (fixable via pruning or ensembles)
* Can be biased with imbalanced datasets

---

## 🚀 Use Cases

* Credit scoring
* Medical diagnosis
* Loan approval
* Spam detection

---

## 🧰 Tips for Better Trees

* Use `max_depth`, `min_samples_split` to control overfitting.
* Use `RandomForestClassifier` for better generalization.

---

## 📃 Summary

* Decision Trees split data based on feature thresholds.
* Use Gini or Entropy for classification.
* Easy to visualize and interpret.
* Powerful but can overfit if not pruned or regularized.

---

## 📊 Difference Between KNN and Decision Tree

| Aspect                  | KNN (K-Nearest Neighbors)                              | Decision Tree                                   |
|-------------------------|--------------------------------------------------------|--------------------------------------------------|
| **Type of Learning**    | Lazy learning (instance-based)                         | Eager learning (model-based)                     |
| **Training Time**       | Very low (no actual model training)                    | High (builds the tree structure during training) |
| **Prediction Time**     | High (needs to compute distance with all data points)  | Low (traverses the tree path)                    |
| **Model Complexity**    | Simple to implement, no model building                 | Can get complex with pruning and depth handling  |
| **Interpretability**    | Less interpretable                                     | Highly interpretable and visualizable            |
| **Handling Noisy Data** | Sensitive to noise and irrelevant features             | More robust to noise (especially with pruning)   |
| **Feature Scaling**     | Requires feature scaling (distance-based)              | Not required                                     |
| **Use Cases**           | Recommendation systems, pattern recognition            | Medical diagnosis, customer segmentation         |
| **Memory Usage**        | High (stores all training data)                        | Low (stores only the tree structure)             |
| **Works Well When**     | The data is uniformly distributed                      | The data is hierarchical or categorical          |

---

# 🌳 Simple Decision Tree Example

## 🎯 Goal: Decide Whether to Go Outside

We’ll use a small dataset to decide if someone should go outside based on the weather.

---

## 📊 Dataset

| Weather | Temperature | GoOutside |
|---------|-------------|-----------|
| Sunny   | Hot         | No        |
| Sunny   | Mild        | Yes       |
| Rainy   | Cold        | No        |
| Rainy   | Mild        | Yes       |
| Sunny   | Cold        | Yes       |

---

## 🛠️ Step-by-Step Tree Construction

### 🎯 Target: `GoOutside` (Yes/No)

Let’s check what feature gives us the best split.

---

### Step 1: Choose the best root node

Let’s consider `Weather`:

- **Sunny (3 samples)** → [No, Yes, Yes] → 2 Yes, 1 No
- **Rainy (2 samples)** → [No, Yes] → 1 Yes, 1 No

Since both branches are mixed, let's use another split.

---

### Step 2: Try `Temperature`:

- **Hot (1 sample)** → No
- **Mild (2 samples)** → Yes, Yes
- **Cold (2 samples)** → No, Yes

Mild gives a pure split (100% Yes). So we choose `Temperature` as the root.

---

## 🌳 Final Tree Structure
```
     [Temperature]
     /     |     \
  Hot   Mild   Cold
   No     Yes   [Weather]
                /     \
             Sunny   Rainy
              Yes      No

```
## 🧠 Sample Predictions

- Temperature = Mild → ✅ Yes
- Temperature = Cold, Weather = Rainy → ❌ No
- Temperature = Cold, Weather = Sunny → ✅ Yes

---

## ✅ Summary

- Decision Tree splits based on best feature (here, `Temperature`).
- Then it goes deeper only where needed (e.g., Cold needs further splitting by `Weather`).
- It’s easy to visualize and understand.

### 📌 Summary:

- Use **KNN** when you want a quick and simple method and when the dataset is not too large.
- Use **Decision Tree** when interpretability is important and you want a model that learns feature relationships clearly.
    

## ⬆️ Next Topic: Random Forests (Ensemble of Trees)
