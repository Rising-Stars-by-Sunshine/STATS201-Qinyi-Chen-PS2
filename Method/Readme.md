## Problem Set 2
![Flow_Chart](https://github.com/Rising-Stars-by-Sunshine/STATS201-Qinyi-Chen-PS2/blob/main/Method/Flow_Chart.png))
### Research Question Formulation:
**Objective**: The sleep quality may differ between seasons, influenced by changed temperature, exercise, and workload. Therefore, this research aims to find out whether season influences sleep quality. The question is: "How do seasonal changes and temperature variations affect sleep quality as measured by sleep scores?"

**Significance**: Understanding the impact of seasonal changes and temperature on sleep quality is crucial for developing personalized sleep improvement strategies and for public health policies enhancing overall well-being. Sleep quality directly affects mental health, physical health, and daily functioning, making this question paramount in sleep research and health studies.

### Operational Measures:

### Variables:

**Dependent (Y) variable**: Sleep Quality, measured by SLEEP_SCORES.

**Independent (X) variables**: Days, used to infer seasonality, and potentially temperature (although temperature is not directly analyzed in the regression discontinuity design, it is implied in the seasonal analysis).

**Data Type**: The dataset is time-series data, capturing daily observations of sleep quality over several months, allowing for the analysis of trends and changes over time.
Hypothesis Development:

**Prediction Hypothesis**: It is hypothesized that seasonal changes, marked by differences in environmental temperature and daylight hours, significantly predict variations in sleep quality. Specifically, we expect to find a discontinuity in sleep quality during the transition between seasons (from Winter to Spring), as these periods are characterized by significant environmental changes that can affect human circadian rhythms and sleep patterns.

**Justification**: The rationale behind this hypothesis stems from existing literature suggesting that environmental factors such as light exposure, temperature, and seasonal affective disorders can influence sleep quality. Seasonal changes are associated with variations in these environmental factors, thus likely impacting sleep.

**Machine Learning Algorithm Selection**: The selected machine learning algorithm for this analysis is the Regression Discontinuity Design (RDD) framework. This research focuses on estimating the causal impact of seasonal transition on sleep quality. Linear Regression is suitable for capturing linear relationships between the time, as a proxy of season, and sleep quality, while the RDD approach allows for a quasi-experimental design to infer causality at the cutoff point between winter and spring.
Model Development:

**Data Processing**: The data will be cleaned to remove any missing values, especially in the dependent variable (SLEEP_SCORES). A binary variable indicating the season based on a specific cutoff day will be created to facilitate the RDD analysis. The independent variable Days will be centered around this cutoff to improve numerical stability in regression analysis.

### Results Presentation:

**Training and Testing**: The model does not explicitly involve a train-test split due to the nature of RDD, which focuses on the discontinuity at a specific threshold (the start of the spring) rather than predicting future outcomes. The analysis will instead focus on estimating the immediate impact of the seasonal transition.

**Data Visualization**: Results will be visualized using scatter plots to show the distribution of sleep scores across days, with fitted regression lines on either side of the seasonal cutoff to illustrate the estimated discontinuity. This will help convey the immediate effect of the transition from Winter to Spring on sleep quality.

### Model Evaluation:

**Evaluation Criteria**: The primary metric for model evaluation will be the estimated size and significance of the discontinuity at the threshold (start of Spring). This will be assessed through the regression coefficients and their confidence intervals.

**Iterative Improvement**: If initial results suggest model refinements are needed, adjustments may include exploring non-linear relationships, considering additional covariates that might influence sleep quality (e.g., temperature, daylight hours), or using different bandwidths around the cutoff for sensitivity analysis. This iterative process aims to ensure that the model accurately captures the relationship between season change and sleep quality, enhancing its predictive accuracy.

### References
Anslan, R. (2022, May 1). Sleep data from Fitbit Tracker. Kaggle. https://www.kaggle.com/datasets/riinuanslan/sleep-data-from-fitbit-tracker 

![Grammarly_2](https://github.com/Annieqyc/STATS201-Qinyi-Chen/blob/main/Method/Grammarly_2.png)

