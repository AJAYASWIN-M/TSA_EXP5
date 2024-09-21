### Developed By: AJAY ASWIN M
### Register No: 212222240005
### Date: 

# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION

### AIM:
To Illustrates how to perform time series analysis and decomposition on the Petrol price dataset.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose


df = pd.read_csv('petrol.csv') 

print(df.head())

df['Date'] = pd.to_datetime(df['Date'])
df.set_index('Date', inplace=True)

price_data = df['Chennai']

new_index = pd.date_range(start=price_data.index.min(), periods=len(price_data), freq='B')[:len(price_data)]
price_data.index = new_index

decomposition = seasonal_decompose(price_data, model='additive', period=30) 

trend = decomposition.trend
seasonal = decomposition.seasonal
residuals = decomposition.resid

plt.figure(figsize=(12, 6))
plt.plot(price_data, label='Original petrol Prices')
plt.title('Original petrol Prices')
plt.legend()
plt.show()

plt.figure(figsize=(12, 6))
plt.plot(seasonal, label='Seasonal Component', color='orange')
plt.title('Seasonal Component')
plt.legend()
plt.show()

plt.figure(figsize=(12, 6))
plt.plot(trend, label='Trend Component', color='green')
plt.title('Trend Component')
plt.legend()
plt.show()

plt.plot(residuals, label='Residuals', color='red')
plt.legend(loc='best')
plt.tight_layout()
plt.show()
```

### OUTPUT:
FIRST FIVE ROWS:

![image](https://github.com/user-attachments/assets/02b0d3d9-3341-4553-81fc-ae5470051954)

PLOTTING THE DATA:

![image](https://github.com/user-attachments/assets/0c1c936e-6ed9-4fa8-98df-1a95c9d38ee9)


SEASONAL PLOT REPRESENTATION :

![image](https://github.com/user-attachments/assets/3b46a6a7-4b01-419d-937c-6765d441abc3)


TREND PLOT REPRESENTATION :

![image](https://github.com/user-attachments/assets/e5cc97af-4121-4b70-ae1a-ac4a1dd63c19)


OVERAL REPRESENTATION:

![image](https://github.com/user-attachments/assets/e9c8a5ef-537f-48ae-b7de-3c273c119e54)



### RESULT:
Thus  the python code for the time series analysis and decomposition is executed sucessfully.
