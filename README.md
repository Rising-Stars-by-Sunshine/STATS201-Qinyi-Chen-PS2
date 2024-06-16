# Problem Set II: Applying Regression Discontinuity to investigate the impact of season on sleep quality
 
This research aims to explore the impact of seasonal changes and temperature variations on sleep quality. With an objective to understand how different seasons affect sleep scores, the study poses the crucial question: 

**"How do seasonal changes and temperature variations affect sleep quality as measured by sleep scores?"**

The significance of this inquiry lies in its potential to inform personalized sleep improvement strategies and public health policies, given the profound influence of sleep quality on mental and physical health, and daily functioning.

Employing time-series data to capture daily observations of sleep quality over several months, the study defines sleep quality (SLEEP_SCORES) as the dependent variable, with time (days) serving as the independent variable to infer seasonality. The hypothesis predicts that seasonal transitions, particularly from Winter to Spring, marked by environmental changes such as temperature fluctuations and daylight variations, significantly affect sleep quality. This prediction is grounded in literature suggesting the influence of environmental factors on sleep patterns and circadian rhythms.

**Method**

To analyze the causal impact of seasonal change on sleep quality, the Regression Discontinuity Design (RDD) framework is chosen for its suitability in quasi-experimental designs. The analysis will focus on the discontinuity at the seasonal transition point, without a conventional train-test split, highlighting the immediate effects of seasonal change. Results will be visualized through scatter plots with fitted regression lines to demonstrate sleep score distributions and the discontinuity at the seasonal cutoff. The study will evaluate the significance of the seasonal impact on sleep quality, with iterative model refinements aimed at enhancing predictive accuracy and understanding of the relationship between seasonality and sleep.

**Results**

![RDD](https://github.com/Rising-Stars-by-Sunshine/STATS201-Qinyi-Chen-PS2/blob/main/Code/RDD.png)


## Table of Content

1.  Method
   [Method](https://github.com/Rising-Stars-by-Sunshine/STATS201-Qinyi-Chen-PS2/tree/main/Method)

3.  Data
   
   [Quired_Data](https://github.com/Rising-Stars-by-Sunshine/STATS201-Qinyi-Chen-PS2/tree/main/Data/Processed-Data/Sleep_data.xlsx)

   [Data_Dictionary](https://github.com/Rising-Stars-by-Sunshine/STATS201-Qinyi-Chen-PS2/tree/main/Data)
   
3. Code
   
   [Data_query](https://github.com/Rising-Stars-by-Sunshine/STATS201-Qinyi-Chen-PS2/tree/main/Code)

   [Data_analysis](https://github.com/Annieqyc/STATS201-Qinyi-Chen/blob/main/Code/Problem_Set_2_RDD.ipynb)

# Author
![Headshot](https://github.com/Rising-Stars-by-Sunshine/STATS201-Qinyi-Chen-PS2/blob/main/Qinyi_Chen.jpg)
<img src="https://github.com/Rising-Stars-by-Sunshine/STATS201-Qinyi-Chen-PS2/blob/main/Qinyi_Chen.jpg" width="200" />
I'm Qinyi Chen from the class of 2026 in Duke Kunshan University. My intended major is Behavioral Science, with a focus on the Neuroscience track. I have a deep interest in unraveling the intricate mechanisms underlying human behaviors. To this end, I am eager to engage in research that bridges the gap between theoretical knowledge and practical application in the field of neuroscience. My goal is to master various algorithms and data processing techniques, as these are crucial tools for analyzing complex behavioral data and contributing to our understanding of the brain's function. I look forward to applying these skills in neuroscientific research to uncover new insights into human behavior.
