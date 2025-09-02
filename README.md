# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
Date: 02.09.2025

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.
### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
### PROGRAM:

```
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

file_path = "India_GDP.csv"  
df = pd.read_csv(file_path, skiprows=1) 
data = df["GDP in (Billion) $"].dropna().values 

N = len(data)
lags = range(35)
```

## Pre-allocate autocorrelation table
```
autocorr_values = []
```

## Mean
```
mean_data = np.mean(data)
```

## Variance
```
variance_data = np.var(data)
```

## Normalized data
```
normalized_data = (data - mean_data) / np.sqrt(variance_data)
```

## Go through lag components one-by-one
```
for lag in lags:
    if lag == 0:
        autocorr_values.append(1)
    else:
        auto_cov = np.sum((data[:-lag] - mean_data) * (data[lag:] - mean_data)) / N
        autocorr_values.append(auto_cov / variance_data)
```

## Display the graph
```
plt.figure(figsize=(10, 6))
plt.stem(lags, autocorr_values)
plt.title('Autocorrelation of India GDP Data')
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.grid(True)
plt.show()
```

### OUTPUT:

<img width="1091" height="644" alt="image" src="https://github.com/user-attachments/assets/b5741760-10fd-49d6-947c-11477fce56f8" />


### RESULT:

Thus we have successfully implemented the auto correlation function in python.
