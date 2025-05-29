# 🧪 Outlier Detection - Teaching Guide

## 🎯 What is an Outlier?

An **outlier** is a data point that is **significantly different** from other observations.  
It "lies outside" the overall pattern in the data.

---

## 🧑‍🏫 Real-Life Examples:
- A student who scored **100** when everyone else scored around **50**.
- A person with a **height of 8 feet** in a dataset where most people are around **5-6 feet**.

---

## 🤔 Why are Outliers Important?

- They can **skew statistical results** (like mean).
- They can **impact model performance** (especially in linear regression, clustering).
- Sometimes they are **errors**, other times they are **important anomalies** (e.g., fraud detection).

---

## 📈 Methods to Detect Outliers

### 1. Using Visualization
#### - Box Plot

```python
import pandas as pd
import matplotlib.pyplot as plt

# Sample data with an outlier
data = [45, 48, 46, 47, 50, 49, 100]  # 100 is an outlier
df = pd.DataFrame(data, columns=["Score"])

# Box Plot
plt.boxplot(df["Score"])
plt.title("Box Plot for Score")
plt.ylabel("Score")
plt.show()
```

## 2. Using the IQR (Interquartile Range)

**Steps:**

1. **Q1** = 25th percentile  
2. **Q3** = 75th percentile  
3. **IQR** = Q3 - Q1  

### Outliers are:

- Values **below**: `Q1 - 1.5 × IQR`  
- Values **above**: `Q3 + 1.5 × IQR`

```
Q1 = df["Score"].quantile(0.25)
Q3 = df["Score"].quantile(0.75)
IQR = Q3 - Q1
```

# Outlier conditions
lower_bound = Q1 - 1.5 * IQR
upper_bound = Q3 + 1.5 * IQR

```
outliers = df[(df["Score"] < lower_bound) | (df["Score"] > upper_bound)]
print("Outliers:\n", outliers)

```

## Using Z-Score (Standard Score)

Z-Score tells us how many standard deviations a data point is from the mean.

```
from scipy.stats import zscore

df["z_score"] = zscore(df["Score"])
outliers_z = df[df["z_score"].abs() > 3]  # Threshold is 3
print("Outliers using Z-Score:\n", outliers_z)

```