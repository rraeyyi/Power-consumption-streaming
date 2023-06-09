# Power-consumption-streaming

The data is modified from the [UCI machine learning repository](https://archive.ics.uci.edu/ml/datasets/Power+consumption+of+Tetouan+city). 
+ Date Time: Each ten minutes.
+ Temperature: Weather Temperature of Tetouan city.
+ Humidity: Weather Humidity of Tetouan city.
+ Wind Speed of Tetouan city.
+ general diffuse flows
+ diffuse flows
+ power consumption of zone 1 of Tetouan city.
+ power consumption of zone 2 of Tetouan city.
+ power consumption of zone 3 of Tetouan city.

This project contains two parts: modeling part and streaming part:

+ For modeling part, I did some summarization and used pyspark’s MLlib module to set up a pipeline for Elastic Net fit including PCA transformer. Then I used cross validation to select the best model and evaluate model performace via RMSE metric.

+ For streaming part, I used model transformer to obtain predictions from the incoming data. Then I created second pipeline that would take all the predictor columns from original data with transforamtion. After combining two dataframes, I wrote those out to the console. 

Finally, I can monitor the prediction on incoming data by randomly sampling three rows through loop and pause for 10 seconds in between outputting of data sets, then output those to a .csv file in the folder:

import pandas as pd   
import numpy as np 
import time  

power = pd.read_csv("power_streaming_data.csv")   
for i in range(0,50):  
    temp = power.loc[np.random.randint(power.shape[0], size = 3)]  
    temp.to_csv("csv_power/power" + str(i) + ".csv", index = False, header = False)  
    time.sleep(10)   
