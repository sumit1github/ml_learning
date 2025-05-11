# Multiple Linear Regression

## What is Multiple Linear Regression?

Multiple Linear Regression (MLR) is a statistical technique that models the relationship between one **dependent variable** and two or more **independent variables**. It extends simple linear regression, which involves only one independent variable.

The general form of the equation is:

```
Y = β₀ + β₁X₁ + β₂X₂ + ... + βₙXₙ + ε
```

Where:
- `Y` is the dependent variable
- `X₁, X₂, ..., Xₙ` are independent variables
- `β₀` is the intercept
- `β₁, β₂, ..., βₙ` are coefficients (slopes)
- `ε` is the error term

## Example

Suppose you want to predict a person's salary (`Y`) based on their years of experience (`X₁`) and education level (`X₂`).

```
Salary = β₀ + β₁*(YearsExperience) + β₂*(EducationLevel) + ε
```

## Assumptions of Multiple Linear Regression

1. **Linearity**: The relationship between dependent and independent variables is linear.
2. **Independence**: Observations are independent of each other.
3. **Homoscedasticity**: Constant variance of residuals.
4. **Normality**: Residuals should be approximately normally distributed.
5. **No Multicollinearity**: Independent variables should not be too highly correlated.

## Evaluation Metrics

- **R-squared (R²)**: Proportion of variance in `Y` explained by the model.
- **Adjusted R²**: Adjusts R² for the number of predictors.
- **Mean Squared Error (MSE)** and **Root Mean Squared Error (RMSE)**: Measures of average model error.

## Applications

- Predicting house prices
- Forecasting sales based on multiple factors
- Analyzing the impact of advertising on product demand

## Python Example (Using scikit-learn)

```python
from sklearn.linear_model import LinearRegression
import pandas as pd

# Sample data
data = {
    'Experience': [1, 2, 3, 4, 5],
    'EducationLevel': [2, 3, 4, 5, 6],
    'Salary': [40, 50, 60, 70, 80]
}
df = pd.DataFrame(data)

X = df[['Experience', 'EducationLevel']]
y = df['Salary']

model = LinearRegression()
model.fit(X, y)

print("Intercept:", model.intercept_)
print("Coefficients:", model.coef_)
```

## Conclusion

Multiple Linear Regression is a foundational technique for predictive modeling and understanding the impact of multiple factors on an outcome. It is widely used in business, economics, health sciences, and machine learning.



# explain
## Plotting a Multiple Linear Regression Line

This code snippet is used to **visualize the regression line** fitted to actual data points in a linear regression task.

```python
# Plotting
plt.scatter(x, y, color="red", label="Actual Data")
plt.plot(x, model.predict(x), color="blue", label="Regression Line")
plt.title("CGPA vs Package")
plt.xlabel("CGPA")
plt.ylabel("Package (LPA)")
plt.grid(True)
plt.legend()
plt.show()
```

### Explanation of Each Line:

1. **`plt.scatter(x, y, color="red", label="Actual Data")`**  
   - This line plots the **actual data points**.
   - `x`: Independent variable (e.g., CGPA).
   - `y`: Dependent variable (e.g., Salary/Package in LPA).
   - Red color is used for the actual data points.
   - A label "Actual Data" is assigned for use in the legend.

2. **`plt.plot(x, model.predict(x), color="blue", label="Regression Line")`**  
   - This line draws the **regression line** predicted by the model.
   - `model.predict(x)` calculates the predicted values of `y` based on the fitted regression model.
   - Blue color is used for the regression line.
   - Labelled as "Regression Line".

3. **`plt.title("CGPA vs Package")`**  
   - Sets the title of the graph.

4. **`plt.xlabel("CGPA")`**  
   - Labels the x-axis, indicating that CGPA is the independent variable.

5. **`plt.ylabel("Package (LPA)")`**  
   - Labels the y-axis, indicating the predicted package in Lakhs Per Annum.

6. **`plt.grid(True)`**  
   - Adds a grid to the plot for better readability.

7. **`plt.legend()`**  
   - Displays the legend using the labels provided in `scatter` and `plot`.

8. **`plt.show()`**  
   - Renders and displays the final plot.

### Purpose:
This plot provides a **visual representation** of how well the regression model fits the data. If the blue regression line closely follows the red points, the model has a good fit.



# Difference Between Simple Linear Regression and Multiple Linear Regression

| Feature | Simple Linear Regression | Multiple Linear Regression |
|--------|---------------------------|-----------------------------|
| **Definition** | Models the relationship between **one independent variable** and **one dependent variable** | Models the relationship between **two or more independent variables** and **one dependent variable** |
| **Equation** | `Y = β₀ + β₁X + ε` | `Y = β₀ + β₁X₁ + β₂X₂ + ... + βₙXₙ + ε` |
| **Number of Inputs** | One independent variable (`X`) | Two or more independent variables (`X₁, X₂, ..., Xₙ`) |
| **Visualization** | 2D Plot (straight line) | Cannot be visualized in 2D if more than 2 predictors; 3D possible with two predictors |
| **Complexity** | Simpler to implement and interpret | More complex and requires checking for multicollinearity, model fit, etc. |
| **Use Case Example** | Predicting salary based on years of experience | Predicting salary based on experience, education, and age |

### Summary

- **Simple Linear Regression** is ideal when analyzing how a single factor affects the outcome.
- **Multiple Linear Regression** is more powerful when the outcome depends on multiple inputs.

