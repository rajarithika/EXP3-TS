# EXPERIMENT 3: LOG TRANSFORMATION OF INTERNATIONAL AIRLINE PASSENGER DATA

**Name:** RAJA RITHIKA M

**Reg. No.:** 2305001029

## 1. Aim

To apply logarithmic transformation to the International Airline Passenger time series and compare the original and transformed data.

## 2. Software Required

- Python 3
- Google Colab or Jupyter Notebook
- Pandas
- NumPy
- Matplotlib

## 3. Procedure

1. Import the required libraries.
2. Load the AirPassengers dataset.
3. Plot the original time series.
4. Apply logarithmic transformation using `np.log()`.
5. Plot the transformed series.
6. Compare the original and transformed data.

## 4. Program

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Load AirPassengers dataset
url = "https://raw.githubusercontent.com/jbrownlee/Datasets/master/airline-passengers.csv"
df = pd.read_csv(url)

# Rename columns and convert Month to datetime
df.columns = ["Month", "Passengers"]
df["Month"] = pd.to_datetime(df["Month"])
df.set_index("Month", inplace=True)

print("Original Data:")
print(df.head())

# Plot original time series
plt.figure(figsize=(12, 5))
plt.plot(df.index, df["Passengers"], marker="o")
plt.title("International Airline Passengers")
plt.xlabel("Year")
plt.ylabel("Passengers (Thousands)")
plt.grid(True)
plt.show()

# Apply log transformation
df["Log_Passengers"] = np.log(df["Passengers"])

print("\nLog Transformed Data:")
print(df.head())

# Plot log-transformed series
plt.figure(figsize=(12, 5))
plt.plot(df.index, df["Log_Passengers"], marker="o")
plt.title("Log-Transformed Airline Passenger Data")
plt.xlabel("Year")
plt.ylabel("Log(Passengers)")
plt.grid(True)
plt.show()

# Compare original and transformed series
fig, axes = plt.subplots(2, 1, figsize=(12, 8))

axes[0].plot(df.index, df["Passengers"])
axes[0].set_title("Original Airline Passenger Series")
axes[0].set_ylabel("Passengers")
axes[0].grid(True)

axes[1].plot(df.index, df["Log_Passengers"])
axes[1].set_title("Log-Transformed Airline Passenger Series")
axes[1].set_ylabel("Log(Passengers)")
axes[1].set_xlabel("Year")
axes[1].grid(True)

plt.tight_layout()
plt.show()

# Compare variance
print("Original Variance:", df["Passengers"].var())
print("Log-Transformed Variance:", df["Log_Passengers"].var())
```

## 5. Expected Output

- Original airline passenger time-series graph.
<img width="1250" height="585" alt="image" src="https://github.com/user-attachments/assets/6abb97a3-e842-428e-b5ea-c4b107587928" />

- Log-transformed airline passenger graph.
<img width="1258" height="571" alt="image" src="https://github.com/user-attachments/assets/45736820-6566-441f-9497-4ac2e39bbc3d" />

- Comparison plots of original and transformed data.
<img width="1482" height="482" alt="image" src="https://github.com/user-attachments/assets/083395bb-8a32-42f1-94b9-002c858966ff" />
<img width="1486" height="512" alt="image" src="https://github.com/user-attachments/assets/f5a35ef7-1c61-43c6-89d7-57df2f8297ac" />


- Original and transformed variance values.
<img width="787" height="587" alt="image" src="https://github.com/user-attachments/assets/057cd5f8-5610-4dcb-a16e-dddf81904fc4" />


## 6. Observation

Before log transformation, the passenger series shows an increasing trend and larger fluctuations as passenger numbers increase.

After log transformation, larger values are compressed more strongly than smaller values. This can reduce changing variability and make the series easier to model.

## 7. Result

Thus, logarithmic transformation was applied successfully to the International Airline Passenger time series, and the original and transformed data were visualized and compared.
