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
