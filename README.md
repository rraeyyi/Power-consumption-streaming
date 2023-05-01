# Power-consumption-streaming

The data is modified from the UCI machine learning repository. The study was about relating power consumption from different zones of Tetouan city to various factors like time of day, temperature, and humidity.

This project contains two parts: modeling part and streaming part:

For modeling part, I did some summarization and used pyspark’s MLlib module to set up a pipeline for Elastic Net fit including PCA transformer. Then I used cross validation to select the best model and evaluate model performace via RMSE metric.

For streaming part, I used model transformer to obtain predictions from the incoming data. Then I created second pipeline that would take all the predictor columns from original data with transforamtion. After combining two dataframes, I wrote those out to the console. Finally, I can monitor the prediction on incoming data by randomly sampling three rows and output those to a .csv file in the folder.
