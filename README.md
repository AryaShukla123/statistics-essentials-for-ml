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
