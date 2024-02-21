# Data Query

## Query Process
The dataframe "Sleep_data" is found in an open datasource from kaggle. [sleep_record](https://www.kaggle.com/datasets/riinuanslan/sleep-data-from-fitbit-tracker) The data is a record of the sleep data of an individual from November to April, down by her FitBit tracker. This dataframes includes detailed parameters of the sleep data, such as deep_sleep, sleep_hours. The overall sleep quality is measured by "SLEEP_SCORES", which can be used for this research. In my research, I wonder whether the sleep quality can be influecned by seasonal changes, for instance, from winter to spring. Therefore, this time-series data can be applied for conducting regression discontinuity. I first cleaned a few NAs in the data set. Then, I added the number of days since the author started recording, which can make the data processing easier. The days are splited at day 92, which is the last day of January marking the end of the winter.
## Regression Discontinuity
[View Problem Set 2 RDD Notebook on nbviewer](https://nbviewer.jupyter.org/github/Rising-Stars-by-Sunshine/STATS201-Qinyi-Chen-PS2/blob/main/Code/Problem_Set_2_RDD.ipynb)

```python
# Environmental Setting
import pandas as pd
import numpy as np
import plotnine as p
import statsmodels.api as sm
import statsmodels.formula.api as smf

import os
from operator import itemgetter
import warnings

import fsspec
import json
import matplotlib.pyplot as plt
import networkx as nx
import numpy as np
import pandas as pd

warnings.filterwarnings("ignore")
test_run = bool(os.environ.get("TEST_RUN", False))  # used by testing to run the notebook as a script

# Load the Sleep Data
sleep_data_path = 'Sleep_data.xlsx'
df = pd.read_excel(sleep_data_path)

# Display the first few rows of the dataframe to understand its structure
df.head()
```

![head](https://github.com/Rising-Stars-by-Sunshine/STATS201-Qinyi-Chen-PS2/blob/main/Data/Processed-Data/Glance.png)

```python
!pip install stargazer
import matplotlib.pyplot as plt
import seaborn as sns
```

```python
#Clean the NAs in the data frame
df = df.dropna(subset=['SLEEP_SCORE'])

# Create a binary variable for season: 0 for Winter (Day=1-92), 1 for Spring (Day=93-181)
df['Season'] = (df['Day'] >= 93).astype(int)

# Plotting
plt.figure(figsize=(12, 6))
sns.scatterplot(x='Day', y='SLEEP_SCORE', hue='Season', data=df, palette='coolwarm', style='Season', markers=True)
plt.axvline(x=93, color='grey', linestyle='--', label='Start of Spring')
plt.title('Sleep Score by Day with Season Change')
plt.xlabel('Day')
plt.ylabel('Sleep Score')
plt.legend(title='Season', labels=['Winter', 'Spring'])
plt.grid(True)
plt.show()
```
![output1](https://github.com/Rising-Stars-by-Sunshine/STATS201-Qinyi-Chen-PS2/blob/main/Code/output1.png)

```python
from sklearn.linear_model import LinearRegression
import numpy as np

# Prepare the data for regression
# Independent variable (centered around the cutoff to improve numerical stability)
X = df['Day'] - 93
# Dependent variable
Y = df['SLEEP_SCORE']

# Split the data based on the season
X_winter = X[df['Day'] < 93].values.reshape(-1, 1)
Y_winter = Y[df['Day'] < 93]
X_spring = X[df['Day'] >= 93].values.reshape(-1, 1)
Y_spring = Y[df['Day'] >= 93]

# Fit linear regression models on either side of the cutoff
reg_winter = LinearRegression().fit(X_winter, Y_winter)
reg_spring = LinearRegression().fit(X_spring, Y_spring)

# Predictions for visualization
X_vis = np.linspace(X.min(), X.max(), 100).reshape(-1, 1)

Y_pred_winter = reg_winter.predict(X_vis[X_vis.flatten() < 0].reshape(-1, 1))
Y_pred_spring = reg_spring.predict(X_vis[X_vis.flatten() >= 0].reshape(-1, 1))


# Plotting the results
plt.figure(figsize=(12, 6))
plt.scatter(df['Day'], Y, c=df['Season'], cmap='coolwarm', label=None, alpha=0.6)
plt.plot(X_vis[X_vis < 0] + 93, Y_pred_winter, color='blue', label='Winter Regression')
plt.plot(X_vis[X_vis >= 0] + 93, Y_pred_spring, color='red', label='Spring Regression')
plt.axvline(x=93, color='grey', linestyle='--', label='Start of Spring')
plt.title('Regression Discontinuity: Sleep Score by Season')
plt.xlabel('Day')
plt.ylabel('Sleep Score')
plt.legend()
plt.grid(True)
plt.show()

# Estimate of the discontinuity
discontinuity_estimate = reg_spring.intercept_ - reg_winter.intercept_
discontinuity_estimate
```

![output2](https://github.com/Rising-Stars-by-Sunshine/STATS201-Qinyi-Chen-PS2/blob/main/Code/output2.png)

discontinuity_estimate=-3.0675216979097826

```python
# Correctly reshaping the X_vis_clean array for predictions
X_vis_reshaped = X_vis.reshape(-1, 1)

# Recalculating predictions with the correctly reshaped array
Y_pred_winter_clean = reg_winter.predict(X_vis_reshaped[X_vis_reshaped.flatten() < 0])
Y_pred_spring_clean = reg_spring.predict(X_vis_reshaped[X_vis_reshaped.flatten() >= 0])

# Re-plotting the results with the corrected data
plt.figure(figsize=(12, 6))
plt.scatter(df['Day'], Y, c=df['Season'], cmap='coolwarm', label=None, alpha=0.6)
plt.plot(X_vis_reshaped[X_vis_reshaped.flatten() < 0] + 93, Y_pred_winter_clean, color='blue', label='Winter Regression')
plt.plot(X_vis_reshaped[X_vis_reshaped.flatten() >= 0] + 93, Y_pred_spring_clean, color='red', label='Spring Regression')
plt.axvline(x=93, color='grey', linestyle='--', label='Start of Spring')
plt.title('Regression Discontinuity: Sleep Score by Season (Corrected)')
plt.xlabel('Day')
plt.ylabel('Sleep Score')
plt.legend()
plt.grid(True)
plt.show()

# Recalculate the estimate of the discontinuity with the corrected data
discontinuity_estimate_corrected = reg_spring.intercept_ - reg_winter.intercept_
discontinuity_estimate_corrected
```

![output3](https://github.com/Rising-Stars-by-Sunshine/STATS201-Qinyi-Chen-PS2/blob/main/Code/output3.png)



