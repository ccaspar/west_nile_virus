# west_nile_virus

|Table of Contents |
|---|
| [Overview](#overview) |
| [Data](#data) |
| [Key Insights](#key-insights) |

## Overview
West Nile virus was first spotted in North America in 1999. Since then, it has spread across the United States and arrived in Chicago in 2002. The goal of this project was to correctly predict the occurrence of West Nile virus in the Chicago area given data on weather and mosquitos caught in numerous traps throughout the city. This project was inspired by a Kaggle competition (www.kaggle.com/c/predict-west-nile-virus). The metric used in this competition is the Area Under the Receiver Operating Curve (AUROC or AUC), which measures the tradeoff between sensitivity (true positive rate) and specificity (true negative rate).


## Data
The data consisted of four main csv files. First a ‘train’ file giving locations of mosquito traps throughout Chicago, with entries for each time a different species of mosquito was caught. Finally, there was a column indicating whether West Nile virus was present among the mosquitos captured. Next, there was a ‘test’ file with the same format as the train file, but without the West Nile virus indicator column. Next, there was a ‘weather’ file with daily weather data for two locations in Chicago. Last was a ‘spray’ file with data on times and locations where mosquito spray had been deployed.

## Key Insights
There were a number of moving parts in this project, largely due to the segmented data sets. The majority of the cleaning was in the weather data. First, I grabbed a new package called geopy to calculate the distance from each trap to each of the two weather stations (using vincenty distance, which calculates the distance from two points on an ellipsoid). Then I made a function to map each trap to the weather from whichever station was closer. There were a number of missing values and repetitive variables (such as heating degree days and cooling degree days, which are measures of the number of degrees the average temperature is below or above 65F respectively). Lastly, it was necessary to bootstrap training data on West Nile virus cases, as there was understandably a very lopsided case on unbalanced classes.

I fit a random forest and a neural network for this project, and the best model was ultimately the neural network. This was a great exercise in tuning neural networks, as the model was initially not learning at all. After much regularization and playing around with the learning rate, I found that largely increasing the batch size was the key to getting an effective model. The training AUC score was 0.82, obviously not perfect but it was not a bad result for a tricky data set like this one. The competition was asking for the best AUC score. In the end, I think it may be more effective to focus just on sensitivity, so that the focus is just on correctly predicting outbreaks of the virus instead of also optimizing predictions of the common case where there is no virus found.




## Concepts and Skills used
Pandas <br>
SKLearn <br>
Tensorflow <br>
Keras <br>
Boostrapping <br>
AUC ROC <br>
Random Forest <br>
Feed Forward Neural Networks <br>