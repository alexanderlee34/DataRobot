Please note that in order for me to get the predictions using R from the model built from the Google Prediction API,
I need the googlepredictionapi R package.  However, I was not able to install the package, because it was out-of-date, 
and it was the only one available online.  I got the predictions from the Google Prediction API and R separately.

Using R, I found the 95 percent confidence interval using the two-sample t-test to see if the difference between the 
number of accidents per day when the speed limit was enforced and the number of accidents per day when the speed limit
was not enforced is statistically significant or not.  The 95 percent CI is [-6.666816, -1.767967].  Since zero is not
within the CI, we can say that at alpha=0.05, the difference is statistically significant.  In fact, the mean number of
accidents per day when the speed limit was enforced is 18.91304, while the mean number of accidents per day the when
speed limit was not enforced is 23.13043.

Also, for the Google Prediction API, I modified the given data, so that 1 represents "yes" (speed limit enforced), 
and 2 represents "no" (speed limit not enforced) for the class binary variable.  After training the given data through
the Prediction API, if I enter the data parameters 1962, 30, and 25 for the year, day, and the number of accidents 
respectively, the output yields 1.667458, which indicates that it is likely that the speed limit was not enforced for
that case.  On the other hand, if I enter the data parameters 1962, 30, and 5, the output yields 1.411050, which 
indicates that it is likely that the speed limit was enforced for that case.

However, the predictions are not very good.  If we use 10-fold cross validation through R, where 80 percent of the
data is trained, and 20 percent of the data is tested to predict the class assigned to them, the prediction accuracy 
is only 55.56 percent.  The accuracy is based on the whether the predicted classes match the actual assigned classes 
or not for the tested data.  The results are shown in the confusion matrix that show the number of correct predictions
for "yes" and "no", false positives, and false negatives.  Please note that the value of the prediction accuracy will
vary if the R code is run multiple times.  In fact, the 95 percent CI of the prediction accuracy is [0.381, 0.7206].

Based on the 95 percent CI of the prediction accuracy, on average the 10-fold cross validation is 55 percent accurate. 
Hence, the predictions are not very accurate.  Such prediction accuracy is very similar to the odds of you winning 
when you hold pocket queen's in a Texas Hold'em heads up poker game after you call your opponent's preflop all-in, 
and your opponent shows that he has ace king suited.  In fact, the odds of you winning in this scenario is 54 percent.
Your opponent can beat you if he gets a straight, a flush, or if either an ace or king hits among the community cards.
Hence, it is hard to predict who will win at the end; the odds of winning is more like a coin-flip.

In addition, based on research papers that I have read on accident rates vs. increased speed limit in journals such as
Transporation Research and Accident Analysis / Prevention for my research, they concluded that increasing the speed
limit by 10 miles per hour either does not significantly affect the accident rate, or increases the accident rate by 
5 to 10 percent (although the authors of the papers did find that the severity of accidents did increase with the speed
limit hike).  However, according to my research advisor, an increase by 5 to 10 percent is not significant enough to
justify that increasing the speed limit increases accident rates.  Going back to the dataset that I used for my 
analysis, we can treat the lack of speed limit enforcement as if the speed limit increased, since drivers tend to 
drive faster when the speed limit is not enforced.

Furthermore, if we take a close look into the data of 184 datapoints, we can see that around 2/3 of the data is 
classified as "no", while the other 1/2 of the data is classified as "yes".  It would be better if the ratio of the
class assigned for the given data is around 50/50, and if we have more datapoints for the given dataset.  Also, if we
use the head function under the R package caret, the subset of predictions that is shown for the testing portion of
the data yield a 55-65 percent class probability in terms of predicting the class for the data.  Moreoever, the 
dataset does not take into consideration weather factors.  If it was raining or snowing, the number of accidents per
day would very likely increase regardless of whether the speed limit was enforced or not.

