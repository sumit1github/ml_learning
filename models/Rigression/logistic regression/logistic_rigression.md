# Logistic Regression on Placement Data

## 📘 Objective
We want to predict whether a student will get **placed (1)** or **not placed (0)** based on their:
- **CGPA**
- **IQ**

---

## 📥 Step 1: Import Libraries

```python
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import train_test_split
from sklearn.metrics import classification_report, confusion_matrix
```

---

## 📄 Step 2: Load the Dataset

```python
df = pd.read_csv("placement_data.csv")  # assuming your CSV is saved with this name
print(df.head())
```

---

## 📊 Step 3: Prepare the Data

```python
# Features (X) and Target (y)
X = df[['cgpa', 'iq']]
y = df['placement']

# Train-Test Split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
```

---

## 🧠 Step 4: Train the Logistic Regression Model

```python
model = LogisticRegression()
model.fit(X_train, y_train)
```

---

## 📈 Step 5: Evaluate the Model

```python
y_pred = model.predict(X_test)

# Confusion Matrix
print(confusion_matrix(y_test, y_pred))

# Classification Report
print(classification_report(y_test, y_pred))
```

---

## 🔍 Step 6: Predict Placement for a New Student

```python
def predict_placement(cgpa, iq):
    return model.predict([[cgpa, iq]])[0]

# Example
print("Predicted:", predict_placement(7.0, 130))  # Output: 1 (Placed)
```

---

## 🎨 Step 7: Visualize the Data and Decision Boundary (Optional)

```python
plt.figure(figsize=(10,6))
plt.scatter(df[df.placement==1].cgpa, df[df.placement==1].iq, color='green', label='Placed')
plt.scatter(df[df.placement==0].cgpa, df[df.placement==0].iq, color='red', label='Not Placed')
plt.xlabel('CGPA')
plt.ylabel('IQ')
plt.legend()
plt.title('Placement Based on CGPA and IQ')
plt.grid(True)
plt.show()
```

---

## ✅ Summary

- Logistic Regression is ideal here because the target (`placement`) is **binary**.
- It models the **probability** that a student is placed based on their CGPA and IQ.
- Uses a **sigmoid function** to convert outputs between `0` and `1`.

---

## 📌 Logistic Regression vs Linear Regression (Recap)

| Feature              | Logistic Regression        | Linear Regression          |
|---------------------|----------------------------|----------------------------|
| Target Type          | Categorical (0 or 1)       | Continuous (e.g. salary)   |
| Output               | Probability (0 to 1)       | Real number                |
| Use Case             | Classification             | Regression                 |
