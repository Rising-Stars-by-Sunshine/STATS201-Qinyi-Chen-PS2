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
Output:
![head](https://github.com/Rising-Stars-by-Sunshine/STATS201-Qinyi-Chen-PS2/blob/main/Data/Processed-Data/Glance.png)

