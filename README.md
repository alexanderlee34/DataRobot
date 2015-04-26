# DataRobot
The dataset that I used for the prediction analysis is the traffic data in Sweden dated back in 1961-1962 for Day i, 
where i is from 1 to 92.  It shows the number of vehicular accidents y (fourth column) on a particular year (first 
column) and day (second column), and whether the speed limit was enforced on that day or not (limit - third column).  The dataset is name Traffic, which is found in the R package MASS. 

I used 10-fold cross-validation (80 percent training; 20 percent testing) to determine the accuracy of the 
class prediction for the testing portion of the data.  I also used the two-sample t-test to see if there was a 
significant difference between the number of accidents per day when speed limit was enforced and the number of 
accidents per day when speed limit was not enforced.

Please note that for the Google Prediction API and for the t-test, I used traffic.txt, which is the modified version
of the original dataset.
