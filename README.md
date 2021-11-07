# Credit Risk Analysis

## Overview of Analysis

The purpose of this analysis is to assess the accuracy of different machine learning techniques to correctly predict whether a loan application is considered “low risk” or “high risk” based on given characteristics of the applicant. Having a machine learning model that performs well would allow us to easily and quickly make decisions in the future about whether to approve or deny a loan application as we could ‘deny’ anything that would be considered ‘high risk’. To test the accuracy, we have used sample data that includes characteristics for each applicant as well as their final score of high or low risk. 

## Results

We know from our sample set that there were 68,470 “low risk” loans, and 347 “high risk” loans, for a total of 68,817 loans we have data on- this means that about 0.50% of loans are considered to be “high risk”, a very low amount. 

### Naïve random oversampling

![Random oversample results](https://user-images.githubusercontent.com/85597801/140631300-109a1e59-42b9-4a4a-906f-da78a0ddfd3f.png)
-	Accuracy score of 0.64 means the model correctly predicted the outcome only 64% of the time- not a very strong result
-	Precision of 0.01 for high risk means that only 1% of loans predicted to be high risk were actually high risk; 99% were a false positive, so a ‘low risk’ loan would potentially be denied. The model predicted a vastly higher number of “high risk” loans than there should be. 
-	Recall of 0.62 for high risk means that 62% of the loans that are high risk were predicted to be high risk, which means that 38% were a false negative, so a ‘high risk’ loan would potentially be approved. 
-	Final result: despite vastly over-classifying loan as “high risk”, it also misses over 1/3 of the actual high risk loans. this model has good scores on predicting low risk loans, which are the vast majority of the loans; it does not do very good with false positives or false negatives on the high risk loans, which is what we were hoping to better predict. The 0.02 F1 score also supports this not being a strong model for predicting a high risk loan. 

### SMOTE oversampling

![SMOTE Results](https://user-images.githubusercontent.com/85597801/140631305-04ffb1c4-cf75-4d99-8e2c-739089da55e9.png)
-	Accuracy score of 0.65 means the model correctly predicted the outcome only 65% of the time, not a very strong result; essentially the same as our random oversampling result.
-	Precision of 0.01 for high risk means that only 1% of loans predicted to be high risk were actually high risk; 99% were a false positive, so a ‘low risk’ loan would potentially be denied. The model predicted a vastly higher number of “high risk” loans than there should be. 
-	Recall of 0.66 for high risk means that 66% of the loans that are high risk were predicted to be high risk, which means that 34% were a false negative, so a ‘high risk’ loan would potentially be approved. 
-	Final result: this model performed a very slight bit better than the random oversampling method, but not enough to make a meaningful difference; it is still vastly overclassifying loans as “high risk” while still missing a lot of the actual “high risk” loans. It actually did slightly worse than random oversampling at predictions on the low risk loan group. F1 scores remain weak. 

### Cluster Centroid undersampling

![Undersampling results](https://user-images.githubusercontent.com/85597801/140631314-e9518c68-f463-4675-bd89-5f8da11dabc8.png)
-	Accuracy score of 0.52 means that 52% of the time this model correctly predicted the outcome- essentially the same as a random 50/50 chance. 
-	Precision of 0.01 for high risk means that only 1% of loans predicted to be high risk were actually high risk; 99% were a false positive, so a ‘low risk’ loan would potentially be denied. The model predicted a vastly higher number of “high risk” loans than there should be. 
-	Recall of 0.60 for high risk means that 60% of the loans that are high risk were predicted to be high risk, which means that 40% were a false negative, so a ‘high risk’ loan would potentially be approved.
-	Final result: this model performed worse than either of the previous oversampling models, and actually saw a significant decline on the correct prediction of the low risk loans as well- with no corresponding increase its ability to correctly predict high risk loans. This is supported by F1 scores for both high & low risk being lower than both of the previous tests. 

### Combination Sampling (SMOTEENN- combination over and under sampling)

![SMOTEENN Results](https://user-images.githubusercontent.com/85597801/140631321-f93ee909-75f2-4758-bb2d-7681f1ce37a0.png)
-	Accuracy score of 0.64 means the model correctly predicted the outcome only 64% of the time- not a very strong result. Very similar to our two oversampling results. 
-	Precision of 0.01 for high risk means that only 1% of loans predicted to be high risk were actually high risk; 99% were a false positive, so a ‘low risk’ loan would potentially be denied. The model predicted a vastly higher number of “high risk” loans than there should be.
-	Recall of 0.69 for high risk means that 69% of the loans that are high risk were predicted to be high risk, which means that 31% were a false negative, so a ‘high risk’ loan would potentially be approved. 
-	Final result: this model is the most accurate so far on the high risk loans, by a small margin. Compared to SMOTE oversampling, our precision remained the same, and recall increased by 5% for high risk loans, with a corresponding decrease in recall for the low risk loans. Our F1 score has still not been able to climb above 0.02 for high risk loans. 

### Balanced Random Forest Classifier

![forest results](https://user-images.githubusercontent.com/85597801/140631328-91c3364f-9366-482e-bb67-55554593f9a5.png)
-	Accuracy score of 0.79 means that 79% of the time the model correctly predicted the result; this is the highest we have seen thus far, by a decent margin.
-	Precision of 0.04 for high risk means that only 4% of loans predicted to be high risk were actually high risk; 96% were a false positive, so a ‘low risk’ loan would potentially be denied. This model continues to predict a vastly higher number of “high risk” loans than there should be.
-	Recall of 0.67 for high risk means that 67% of the loans that are high risk were predicted to be high risk, which means that 33% were a false negative, so a ‘high risk’ loan would potentially be approved. 
-	Final result: this model is our most accurate so far, which is not saying a lot, but it is definitely an improvement! We were able to get the F1 score for high risk loans up to 0.07, and the low risk score all the way to 0.95, which is a fairly good result. Recall of 91% on the low risk loans is a significant improvement over all of the previous models. 

### Easy Ensemble Classifier

![Ensemble results](https://user-images.githubusercontent.com/85597801/140631332-1ff71a38-ca48-483a-a7d5-d14aec1e9cf7.png)
-	Accuracy score of 0.93 means that the model predicted the correct result 93% of the time- by far the best so far! That is actually looking to be a promising number. 
-	Precision of 0.07 for high risk means that only 7% of loans predicted to be high risk were actually high risk; 93% were a false positive, so a ‘low risk’ loan would potentially be denied. This model continues to predict a vastly higher number of “high risk” loans than there should be, though a slight improvement. 
-	Recall of 0.91 for high risk means that 91% of the loans that are high risk were predicted to be high risk, which means that 9% were a false negative, so a ‘high risk’ loan would potentially be approved. 
-	Final result: Our F1 score for the high risk loans has gone up to 0.14, which is still a pretty low number, but is over twice what the next highest result yielded. This model scored a 0.97 F1 for low risk loans, which is a good score. Using this model, we would still have a decent number of false positives, but the false negatives has become a much more tolerable number. 

## Summary

All of the models performed better on predicting the low risk loans, which we expected to see, as that was clearly the skew of our available data. Given the limitations of machine learning, and available funds to give out for loans, we would prefer to have false positives (identify a loan as ‘high risk’ and deny it, when it really would have been a good, ‘low risk’ loan) than to have false negatives (identify a loan as ‘low risk’ and approve it, when really it is a bad investment, a ‘high risk’ loan). 

This can be seen in a simple calculation- the mean loan amount of our data set is $16,678, with an interest rate of 13%- which we will assume is the total percentage over the life of the loan for simplicity. The loan would earn $2,168 over its life- so one bad loan, $16,678 (mean) lost would take 8 good loans to make up for. Because of this risk/reward trade off, we would prefer to “err on the side of caution” and deny loans that would have been a good investment than risk funding a bad loan. 

Because of this preference, I would recommend using the “Easy Ensemble AdaBoost Classifier”, as it had by far the highest recall rate of any of our models, 91%, for high risk loans (the next highest is 69% with the combination method). 

If we look at the confusion matrix for the chosen model, and assumed we were going to approve all of the loans that were classified as “low risk” by the model, then we would be funding 16,139 low risk loans, and 8 high risk loans. Even assuming that the 8 high risk loans go into default immediately with no payments, we would have $35M in profits (16,139 * $2,168) and $133,424 in losses (8 * $16,678), which would be a huge win!


