# Teaching Random Forest Algorithm

## What is Random Forest?

**Random Forest** is a popular and powerful ensemble machine learning algorithm. It combines multiple decision trees to create a more accurate and stable model. It can be used for both **classification** and **regression** tasks.


## Why is it Called "Random Forest"?

- **Random**: It introduces randomness in two ways:
  1. It selects random samples of the training data (bootstrapping).
  2. It chooses a random subset of features at each split in the tree.
- **Forest**: It builds many decision trees (a "forest") instead of just one.


## 🔁 Step-by-Step: How Random Forest Works

1. **Bootstrap Sampling** (Bagging):
   - From the original training dataset, create multiple **random samples** (with replacement).
   - Each sample is used to train a separate decision tree.

2. **Random Feature Selection**:
   - When growing each tree, instead of checking all features to find the best split, only a **random subset of features** is considered.
   - This ensures that trees are **decorrelated**, meaning they won't make the same mistakes.

3. **Training Trees**:
   - Each tree is grown fully or until stopping criteria is met (like `max_depth` or `min_samples_split`).

4. **Making Predictions**:
   - **Classification**: Each tree gives a class prediction, and the **majority vote** is the final result.
   - **Regression**: Each tree gives a numeric value, and the **average** of all predictions is returned.

---

## Visual Diagram (Text-Based)
```
Training Data
└── Tree 1 (random sample + random features)
└── Tree 2 (random sample + random features)
└── Tree 3 (random sample + random features)
...
└── Tree N

Final Prediction:
└── Classification: Majority vote
└── Regression: Average of outputs
```

## Advantages of Random Forest

- Reduces overfitting compared to a single decision tree.
- Works well for both `classification` and `regression`.
- Handles missing values and categorical features well.
- `Robust to outliers and noise.`


## Disadvantages

- Can be computationally intensive with many trees.
- Less interpretable than a single decision tree.


## 📌 Example: Classification (Spam Detection)

You want to classify whether an email is spam or not.

- You collect thousands of emails labeled as "spam" or "not spam."
- You train a Random Forest classifier on this data.
- Each tree learns slightly different rules based on random samples and features.
- When a new email arrives, each tree votes "spam" or "not spam."
- Final decision = **majority vote** across all trees.


# ✅ Advantages

- Handles large datasets well
- Works with both numerical and categorical data
- Automatically handles missing values
- Less prone to overfitting than single decision trees
- Robust to outliers and noise


# ❌ Disadvantages

- Slower and more memory-intensive than a single tree
- Harder to interpret (less explainable)
- May not work well on very sparse datasets (like text data without preprocessing)


# Important Hyperparameters to Tune

| Parameter           | Description                                        |
| ------------------- | -------------------------------------------------- |
| `n_estimators`      | Number of trees in the forest                      |
| `max_depth`         | Maximum depth of the tree                          |
| `max_features`      | Number of features to consider for the best split  |
| `min_samples_split` | Minimum samples required to split an internal node |
| `bootstrap`         | Whether bootstrap samples are used                 |


# Summary

1. Random Forest is an ensemble of decision trees.
2. It improves accuracy and reduces overfitting.
3. Suitable for both classification and regression.
4. It is one of the most used algorithms in real-world applications.


# 🎓 Teaching Random Forest with a Real-World Dataset

In this lesson, we will **learn Random Forest** using a **real-world dataset**: the **Titanic survival dataset**.

## 🛳️ Real-World Problem: Titanic Survival Prediction

### Problem Statement:
Given information about passengers on the Titanic, can we **predict whether a passenger survived or not**?

### Objective:
Use Random Forest Classification to predict survival based on features like age, gender, ticket class, etc.


### 📦 Step 1: Dataset Introduction

We'll use the Titanic dataset from Kaggle or Seaborn. It contains:

| Feature    | Description                                                                                          |
| ---------- | ---------------------------------------------------------------------------------------------------- |
| `Survived` | Survival status (0 = No, 1 = Yes)                                                                    |
| `Pclass`   | Passenger class (1 = 1st, 2 = 2nd, 3 = 3rd)                                                          |
| `Sex`      | Gender of the passenger (`male` or `female`)                                                         |
| `Age`      | Age in years (can be fractional for babies)                                                          |
| `SibSp`    | Number of siblings/spouses aboard the Titanic                                                        |
| `Parch`    | Number of parents/children aboard the Titanic                                                        |
| `Fare`     | Ticket fare paid (in British Pounds)                                                                 |
| `Embarked` | Port of Embarkation (`C` = Cherbourg, France; `Q` = Queenstown, Ireland; `S` = Southampton, England) |
