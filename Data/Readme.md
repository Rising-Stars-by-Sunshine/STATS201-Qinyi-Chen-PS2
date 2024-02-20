# Data: Sleep Data from FitBit Tracker

## Queried Data: FitBit Record of Sleep 

This folder shows the queried data for this research. The data is downloaded from an online open source: https://www.kaggle.com/datasets/riinuanslan/sleep-data-from-fitbit-tracker.
![Website](https://github.com/Rising-Stars-by-Sunshine/STATS201-Qinyi-Chen-PS2/blob/main/Data/Queried-Data/Queried_Data.png)

According to the upoloader, this data is collected by her Fitbit Tracker about her physiological parameters during sleep. Additonally, the tracker will also provide an extimation of the sleep quality, which is presented as variable "SLEEP_SCORES". 
This data can be classified as a time-series data, which captures daily observations of sleep data. The datasource contains 6 files, recording the sleep quality from November to April.

## Processed Data

Since the monthly data were initially stored in separate files, it is necessary to merge the data in order to create a time-series data that contains data of 6 months. Additionally, I added the column "Days" to simplify the processing of time. 

Let's display the first few rows of the dataset:
![Glance](https://github.com/Rising-Stars-by-Sunshine/STATS201-Qinyi-Chen-PS2/blob/main/Data/Processed-Data/Glance.png)

### Data Dictionary
| Variable                | Definition                      | Description                                           | Frequency | Range          | Unit         | Type     | Sample Observations        |
|-------------------------|---------------------------------|-------------------------------------------------------|-----------|----------------|--------------|----------|-----------------------------|
| Day                     | Day of the month                | Integer value representing the day of the month       | Daily     | 1-31           | Day          | Integer  | 1, 2, 3                     |
| Month                   | Month of the year               | Name of the month                                      | Monthly   | January-December| Month        | String   | November                    |
| Weekday                 | Day of the week                 | Name of the weekday                                    | Weekly    | Monday-Sunday  | Day          | String   | Monday, Tuesday             |
| DATE                    | Date of the record              | The date when the sleep data was recorded              | Daily     | Date range     | Date         | Date     | 2021-11-01, 2021-11-02      |
| SLEEP_SCORE             | Sleep quality score             | A score representing the quality of sleep              | Daily     | 0-100          | Score        | Float    | 88.0, 83.0                  |
| HOURS_OF_SLEEP          | Total hours of sleep            | Total duration of sleep                                | Daily     | Time duration  | Hours:Minutes| Time     | 08:06:00, 07:57:00          |
| REM_SLEEP               | Ratio of REM sleep              | Proportion of sleep spent in REM phase                 | Daily     | 0-1            | Ratio        | Float    | 0.20, 0.12                  |
| DEEP_SLEEP              | Ratio of deep sleep             | Proportion of sleep spent in deep sleep phase          | Daily     | 0-1            | Ratio        | Float    | 0.13, 0.18                  |
| HEART_RATE_BELOW_RESTING| Time heart rate below resting   | Proportion of sleep time with heart rate below resting | Daily     | 0-1            | Ratio        | Float    | 0.84, 0.90                  |
| SLEEP_TIME              | Sleep start and end time        | String representing the start and end time of sleep    | Daily     | Time range     | Time         | String   | 10:41pm - 7:54am, 10:40pm - 7:55am |
| Steps                   | Number of steps taken           | Total number of steps taken during the day             | Daily     | Number         | Steps        | Integer  | 12643, 6958                 |



