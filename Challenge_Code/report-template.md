# Module 12 Report Template

## Overview of the Analysis

The purpose of this analysis is to fit and train a supervised machine learning model in order to predict which borrowers had a high-risk loan. The data used to train the model included information such as:

* the size of the loan
* the interest rate on the loan 
* the annual income of the client
* the client's debt-to-income ratio (DTI)
* the client's total debt
* the client's total number of bank accounts
* the status of the loan (healthy or high-risk)

The y-variable in this model was, of course, the loan status and so it was separated from the rest of the data. A brief count of this variable in the training dataset showed that the bank in question had far more healthy loans than high-risk loans. Out of almost 78,000 loans, only about 3% were considered unhealthy.

A logistic regression was chosen as the preferred model. This is because the data in question is discrete and needs to be classified. Logistic regressions are best for predicting binary outcomes which is the case with this data since a loan will either be healthy(0) or high-risk(1).<br><br> 


## Results

Two regressions were run on this data. The first using a random sample, and the second using oversampled data.

* Machine Learning Model 1: 

After fitting a logistic regression to a training dataset (80% of the original data, random sample), the model was then validated using a testing dataset (20% of the original y-values, random sample). This resulted in an accuracy score of .99 meaning that the model correctly classified healthy and high risk loans 99% of the time. the balanced accuracy score differs from the accuracy score in that it calculates the accuracy score for each class and then combines the two. In this case, the balanced accuracy score was .95 meaning that the model was missing one class more often then the other. 

The confusion matrix proved this to be true. The model had 102 false positives and 56 false negatives. The precision score for high-risk loans was .85 meaning that the model classified high-risk loans as healthy 15% of the time. The recall score for high-risk loans was .91 so the model was classifying healthy loans as unhealthy for 9% of the misclassified loans. 

These numbers were possibly due to the fact that there were so few high-risk loans in the original dataset. While the model was very accurate, high-risk loans were being disproportionately misclassified.


  * Description of Model 1 Accuracy, Precision, and Recall scores.

Accuracy Score: .99<br>
Balanced Accuracy Score: .95<br>
Precision Score for Healthy Loans: 1.00<br>
Recall Score for Healthy Loans: .99<br>
Precision Score for High-Risk Loans: .85<br>
Recall Score for High-Risk Loans: .91<br><br>  


* Machine Learning Model 2:

Using an oversampler from imblearn, the training data was resampled to include equal amounts of healthy and unhealthy loans. The same sort of logistic regression was run again on the original testing data. 

The classification report for validating the model showed a balanced accuracy score of .99 which is an improvement from .95. The precision and recall scores for healthy loans were the same as the first model. However, the precision score for high-risk loans actually fell by .01 to .84 meaning the rate of false positives actually increased. The recall of high-risk loans marked as healthy improved to .99.

To summarize, there were very few misclassifed loans but most of them were false positve high-risk loans.

  * Description of Model 2 Accuracy, Precision, and Recall scores.

Accuracy Score: .99<br>
Balanced Accuracy Score: .99<br>
Precision Score for Healthy Loans: 1.00<br> 
Recall Score for Healthy Loans: .99<br>
Precision Score for High-Risk Loans: .84<br>
Recall Score for High-Risk Loans: .99<br><br>

## Summary

The balanced accuracy score of the second logistic regression conclusively shows that the oversampled model performed the best. This is because it proves that the model is correctly classifying both types of loans with nearly equal measure. However, when the model misclassifies a loan, it often a healthy loan that is labeled high-risk. This happens even with the oversampled model. <br>
Because this is not a life or death project, and because both models are considered 99% accurate, either model would be useful. I would recommend the oversampled one because it cuts back on false negatives and trains the model with a balanced number of healthy and unhealthy loans.<br> 
For future analysis it would be interesting to use the same sort of model with oversampled data that is not half-and-half. In order to avoid the possibility of overtraining the model, the testing data should be more than 3% high-risk loans but less than 50%.