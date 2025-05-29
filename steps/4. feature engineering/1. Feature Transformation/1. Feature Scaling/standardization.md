# Standardization in Machine Learning

**Standardization** is a preprocessing technique used in machine learning to transform features so that they have the characteristics of a standard normal distribution — i.e., a **mean of 0** and a **standard deviation of 1**.

## Why Do We Use Standardization?

Standardization is essential for many machine learning models because:

- **Different features may have different units and scales.** For example, one feature could be "age in years" (0–100), while another could be "salary in dollars" (0–100,000). Algorithms like SVM, KNN, and Logistic Regression are sensitive to feature magnitudes.
  
- **Gradient-based optimizers** (used in neural networks, logistic regression, etc.) converge faster when input data is standardized.

- **PCA (Principal Component Analysis)** assumes data is centered around zero, so standardization is required.


## How Standardization Works

The formula for standardizing a feature (column) is:

- `z = (x - μ) / σ`

Where:
- `x` is an original value,
- `μ` is the mean of the feature,
- `σ` is the standard deviation of the feature,
- `z` is the standardized value.

## Example

Suppose you have a feature "Age" with the following values: `[20, 30, 40]`.

1. Mean (μ) = (20 + 30 + 40) / 3 = 30
2. Standard Deviation (σ) = sqrt(((20-30)² + (30-30)² + (40-30)²)/3) = 8.16 (approx)

Standardized values:
- (20 - 30)/8.16 ≈ -1.22
- (30 - 30)/8.16 = 0
- (40 - 30)/8.16 ≈ 1.22


## When to Use Standardization?

### ✅ Use standardization when:

- Your algorithm assumes data is **normally distributed**  
  *(e.g., Logistic Regression, SVM)*

- You are using **distance-based algorithms**  
  *(e.g., KNN, K-Means)*

- Your data contains **outliers**  
  *(Standardization is less sensitive to outliers than normalization)*

---

### ❌ Avoid standardization when:

- Your data is already **scaled** or is **categorical**

- You are using a model that **does not require feature scaling**  
  *(e.g., Decision Trees, Random Forests)*


## Standardization in Code

```python
from sklearn.preprocessing import StandardScaler
import pandas as pd

df = pd.DataFrame({'Age': [20, 30, 40]})
scaler = StandardScaler()
df_scaled = scaler.fit_transform(df)

print(df_scaled)
