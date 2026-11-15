# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
## Date: 15 - 11 - 2026

# AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

# ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

# PROGRAM:

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

from statsmodels.tsa.seasonal import seasonal_decompose

# Step 1: Load the dataset and set Date as index
url = 'https://raw.githubusercontent.com/jbrownlee/Datasets/master/daily-min-temperatures.csv'

data = pd.read_csv(url, parse_dates=['Date'], index_col='Date')

# Step 2: Perform seasonal decomposition
decomposition = seasonal_decompose(
    data['Temp'],
    model='additive',
    period=365
)

# Step 3: Plot the decomposition
plt.figure(figsize=(12, 10))

# Original Data
plt.subplot(411)
plt.plot(data['Temp'], label='Daily Temperatures')
plt.legend(loc='upper left')
plt.title('Original Time Series Data')

# Trend Plot
plt.subplot(412)
plt.plot(decomposition.trend, label='Trend', color='orange')
plt.legend(loc='upper left')
plt.title('Trend Plot')

# Seasonal Plot
plt.subplot(413)
plt.plot(decomposition.seasonal, label='Seasonal', color='green')
plt.legend(loc='upper left')
plt.title('Seasonality Plot')

# Residual Plot
plt.subplot(414)
plt.plot(decomposition.resid, label='Residual', color='red')
plt.legend(loc='upper left')
plt.title('Residual Plot')

plt.tight_layout()
plt.show()
```

### OUTPUT:

### Original Data
<img width="1852" height="385" alt="{Original Data}" src="https://github.com/user-attachments/assets/709494ec-bc96-4fe9-9ec3-8a919b270bf6" />

### Trend Plot
<img width="1851" height="380" alt="{Trend Plot}" src="https://github.com/user-attachments/assets/d350d0a0-1c7e-49cd-9461-d749d31b4026" />

### Seasonal Plot
<img width="1851" height="377" alt="{Seasonal Plot}" src="https://github.com/user-attachments/assets/9c7cc77e-15c2-4a76-944a-3d6ed42f7c49" />

### Residual Plot
<img width="1852" height="388" alt="{Residual Plot}" src="https://github.com/user-attachments/assets/66115c65-ac50-4055-8856-2861a30e6831" />


# RESULT:
Thus we have created the python code for the time series analysis and decomposition.
