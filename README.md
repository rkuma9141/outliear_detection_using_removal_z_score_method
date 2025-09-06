# Outlier Detection using Removal (Z-Score Method)

## Introduction
Outliers are extreme values that deviate significantly from most of the data points.  
The **Z-Score Method** is a widely used statistical technique to detect and remove such outliers.

The idea is simple:
- The **Z-score** tells how many standard deviations a data point is from the mean.
- If the absolute Z-score is too high, the point is considered an outlier.

---

## Formula
For a data point `x`:

\[
Z = \frac{x - \mu}{\sigma}
\]

Where:
- \( \mu \) = Mean of the dataset  
- \( \sigma \) = Standard Deviation of the dataset  

---

## Steps

1. **Calculate Mean and Standard Deviation** of the dataset.
2. **Compute Z-score** for each value.
3. **Set a Threshold** (commonly **|Z| > 3**).
4. **Remove Outliers** (data points with Z-score beyond the threshold).

---

## Example in Python

```python
import numpy as np

# Sample dataset
data = [10, 12, 12, 13, 13, 14, 15, 16, 100]

# Convert to numpy array
data = np.array(data)

# Calculate mean and standard deviation
mean = np.mean(data)
std = np.std(data)

# Calculate Z-scores
z_scores = [(x - mean) / std for x in data]

# Set threshold
threshold = 3

# Detect and remove outliers
filtered_data = [x for x, z in zip(data, z_scores) if abs(z) <= threshold]

print("Original Data:", data)
print("Z-Scores:", z_scores)
print("Filtered Data (Outliers Removed):", filtered_data)
