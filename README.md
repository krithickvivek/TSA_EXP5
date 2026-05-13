# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 


## AIM:
To perform time series analysis and decomposition on the Apple stock price dataset using Python and to analyze its trend, seasonal, and residual components.
## DATASET
Apple 2009-2005
## SOFTWARE REQUIRED
Google Colab
## ALGORITHM

1. Import the required libraries such as pandas, numpy, matplotlib, and seasonal_decompose from statsmodels.
2. Read the Apple CSV dataset using pandas.
3. Convert the Date column into datetime format.
4. Set the Date column as the index of the dataset.
5. Select the required stock price column for analysis.
6. Perform time series decomposition using the additive or multiplicative model.
7. Extract the trend, seasonal, and residual components from the dataset.
8. Plot the original data, trend, seasonality, and residual graphs.
9. Display the decomposition results and analyze the behavior of the Apple stock data.

## PROGRAM:
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

#Load the dataset
data = pd.read_csv("Apple 2009-2024.csv")
data.head()

# Set year as index directly
data.set_index('year', inplace=True)

# Convert Revenue column to numeric
data['Revenue (millions)'] = (
    data['Revenue (millions)']
    .replace('[\$,]', '', regex=True)
    .astype(float) )

# Perform decomposition
decomposition = seasonal_decompose(
    data['Revenue (millions)'],
    model='additive',
    period=2
)

# Original Data
plt.plot(data.index, data['Revenue (millions)'])
plt.title('Original Revenue Data')
plt.xlabel('Year')
plt.ylabel('Revenue')

# Trend
plt.plot(data.index, decomposition.trend, color='orange')
plt.title('Trend Plot')
plt.xlabel('Year')

# Seasonal
plt.plot(data.index, decomposition.seasonal, color='green')
plt.title('Seasonality Plot')
plt.xlabel('Year')

# Residual
plt.plot(data.index, decomposition.resid, color='red')
plt.title('Residual Plot')
plt.xlabel('Year')
```

## OUTPUT:
### FIRST FIVE ROWS

<img width="930" height="254" alt="image" src="https://github.com/user-attachments/assets/0965279a-d26a-4f4e-8be1-a60259fe99f5" />

### PLOTTING THE DATA

<img width="803" height="530" alt="image" src="https://github.com/user-attachments/assets/1141eed2-c99d-489a-b26a-dea40a686338" />

### SEASONAL PLOT REPRESENTATION 

<img width="695" height="522" alt="image" src="https://github.com/user-attachments/assets/89f771db-1b53-48d5-ae3b-e6b7c59fa582" />

### TREND PLOT REPRESENTATION 

<img width="713" height="528" alt="image" src="https://github.com/user-attachments/assets/51be3a1d-b5c6-428a-9a33-b1c8c3fe4a75" />

## RESULT:
Thus we have created the python code for the time series analysis and decomposition.
