# 📊 Statistics for Machine Learning: Comprehensive Guide

This repository serves as a deep-dive reference for statistical fundamentals, transitioning from basic data types to complex bivariate analysis.

---

## 1. Introduction to Statistics
Statistics is the backbone of Machine Learning, providing the tools to separate "signal" from "noise."

* **Descriptive Statistics:** Tools used to describe the features of a specific dataset. It does not allow us to make conclusions beyond the data we have analyzed.
* **Inferential Statistics:** Uses a random sample of data taken from a population to describe and make inferences about the whole population. 
* **Population ($N$) vs. Sample ($n$):** * **Population:** The entire collection of items under consideration.
    * **Sample:** A representative subset of the population. We use sample statistics ($\bar{x}, s$) to estimate population parameters ($\mu, \sigma$).



---

## 2. Data Fundamentals
Before applying any model, you must identify the data type to choose the correct algorithm.

* **Numerical (Quantitative):**
    * **Discrete:** Whole numbers you can count (e.g., Number of children).
    * **Continuous:** Measurements that can take any value (e.g., Height, Temperature).
* **Categorical (Qualitative):**
    * **Nominal:** Categories with no inherent order (e.g., Gender, Nationality).
    * **Ordinal:** Categories with a clear ranking (e.g., Education level: High School < Bachelors < Masters).



---

## 3. Measures of Central Tendency
These metrics help identify the "typical" value in your dataset.

* **Mean:** The arithmetic average. Sensitive to outliers.
* **Median:** The middle value. Best for skewed data (e.g., Salary data).
* **Mode:** The value that appears most often. Useful for categorical data.
* **Weighted Mean:** Used when certain data points contribute more to the final result than others (e.g., calculating GPA).
* **Trimmed Mean:** Calculating the mean after removing a fixed percentage (e.g., 5% or 10%) of the top and bottom values. This reduces the impact of extreme outliers.

### 🐍 Python Implementation:
```python
import numpy as np
from scipy import stats

data = [10, 12, 12, 13, 15, 100] # 100 is an outlier

print(f"Mean: {np.mean(data)}")
print(f"Median: {np.median(data)}")
print(f"Mode: {stats.mode(data, keepdims=True).mode[0]}")
print(f"Trimmed Mean (10%): {stats.trim_mean(data, 0.1)}")
```



---

## 4. Measures of Dispersion
Dispersion tells us how "spread out" the data is around the center.

* **Range:** Simple but ignores the distribution of the internal data.
* **Variance ($\sigma^2$):** The average of the squared differences from the mean. It quantifies the degree of spread.
* **Standard Deviation ($\sigma$):** The square root of variance. It is expressed in the same units as the data, making it easier to interpret.
* **Coefficient of Variation (CV):** Expressed as a percentage. It allows you to compare the volatility of two different datasets (e.g., comparing the price fluctuations of Gold vs. Bitcoin).

### 🐍 Python Implementation:
```python
std_dev = np.std(data)
variance = np.var(data)
cv = (std_dev / np.mean(data)) * 100
```



---

## 5. Univariate Analysis (Visualizing One Variable)
Focuses on understanding the distribution of a single feature.

* **Categorical Data**
    * **Frequency Table:** Lists the count of each category.

    * **Cumulative Frequency:** Useful to see how many observations fall below a certain category (mostly for ordinal data).

* **Numerical Data**
    * **Histogram:** Displays the "density" of data across bins. It helps identify if data is Normal, Right-Skewed, or Left-Skewed.



---

## 6. Bivariate Analysis (Relationships)
Analyzing how two variables interact with each other.

* **Categorical -** Categorical (Contingency Table): Also known as a "Crosstab." It shows the relationship between two categories (e.g., Gender vs. Voting Preference).

* **Numerical -** Numerical (Scatter Plot): Used to check for linear or non-linear relationships. Essential for Linear Regression.

* **Categorical -** Numerical: Often analyzed using Grouped Box Plots or Bar Charts to see how a numeric value (e.g., Income) varies across categories (e.g., Job Title).

### 🐍 Python Implementation (Bivariate):
```python
import pandas as pd
import seaborn as sns

# Crosstab
pd.crosstab(df['Gender'], df['Purchased'])

# Scatter Plot
sns.scatterplot(x='Age', y='Salary', data=df)

# Box Plot (Categorical vs Numerical)
sns.boxplot(x='Category', y='Value', data=df)
```



---

## 🛠️ Getting Started & Installation

To run the statistical analysis and visualizations mentioned in this guide, you will need **Python 3.x** and the following data science libraries:

### 1. Install Dependencies
Run the following command in your terminal/command prompt:

```bash
pip install numpy pandas scipy matplotlib seaborn
```

### 2. Library Overview
* **NumPy:** Used for high-performance mathematical operations and arrays.

* **Pandas:** The primary tool for data manipulation and creating Frequency Tables/Crosstabs.

* **SciPy:** Essential for advanced statistics like Trimmed Mean, Z-Scores, and Hypothesis Testing.

* **Matplotlib/Seaborn:** Used for Univariate (Histograms) and Bivariate (Scatter plots, Box plots) visualizations.

### 3. Quick Setup Code
Copy this block at the top of your Python script to ensure all tools are ready:

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from scipy import stats

# Set visual style for plots
sns.set_theme(style="whitegrid")
```



---

## 📊 Summary Table: Choosing the Right Analysis

Use this table as a quick reference to determine which statistical method or visualization fits your data type.

| Analysis Type | Variable 1 | Variable 2 | Goal | Recommended Tool / Visualization |
| :--- | :--- | :--- | :--- | :--- |
| **Univariate** | Categorical | - | Distribution of categories | Bar Chart / Frequency Table |
| **Univariate** | Numerical | - | Distribution of values | Histogram / Box Plot / PDF |
| **Bivariate** | Categorical | Categorical | Relationship between groups | Contingency Table (Crosstab) / Heatmap |
| **Bivariate** | Numerical | Numerical | Correlation / Trend | Scatter Plot / Line Plot |
| **Bivariate** | Categorical | Numerical | Comparison of groups | Grouped Box Plot / Bar Chart |

---

### 🔍 Understanding the Box Plot
The Box Plot is a powerful univariate and bivariate tool that summarizes the **Median**, **Quartiles**, and **Outliers** in a single view.



* **Median (Q2):** The middle line in the box.
* **Interquartile Range (IQR):** The distance between the 25th (Q1) and 75th (Q3) percentiles (the box itself).
* **Whiskers:** Typically represent $1.5 \times IQR$.
* **Outliers:** Points that fall outside the whiskers.
