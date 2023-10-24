# credit-risk-classification
For this challenge, I will utilize diverse methodologies to construct and assess a loan risk model. This process will involve working with a dataset comprising historical lending transactions from a peer-to-peer lending company to facilitate the evaluation of borrower creditworthiness.

### Instructions
1. Split the Data into Training and Testing Sets
    * Read the lending_data.csv data from the Resources folder into a Pandas DataFrame.
    * Create the labels set (y) from the “loan_status” column, and then create the features (X) DataFrame from the remaining columns.
    * Split the data into training and testing datasets by using train_test_split.

2. Create a Logistic Regression Model with the Original Data
    * Fit a logistic regression model by using the training data (X_train and y_train).
    * Save the predictions for the testing data labels by using the testing feature data (X_test) and the fitted model.
    * Evaluate the model’s performance by doing the following:
        1. Generate a confusion matrix.
        2. Print the classification report.

3. Write a Credit Risk Analysis Report
    Write a brief report that includes a summary and analysis of the performance of the machine learning models that you used in this homework. You should write this report as the README.md file included in your GitHub repository.
</br>


# Credit Risk Analysis Report

1. [Overview of the Analysis](#An-overview-of-the-analysis)

2. [Model Results](#results)

3. [Summary](#summary)
</br>

## **An overview of the analysis**
* The primary purpose of this challenge is to employ a range of methodologies for training and assessing a loan risk-based model. Leveraging a dataset of past lending transactions from a peer-to-peer lending services company, the objective is to construct a model capable of assessing the creditworthiness of borrowers. 

* Following the data split into training and testing sets, it becomes evident that the distribution of target values between healthy and unhealthy loans is imbalanced. There is a larger amount of data available for healthy loans in comparison to unhealthy ones.
```
# code
y.value_counts()

# output
0    75036
1     2500
Name: loan_status, dtype: int64
```

* The prediction accuracy rate is 95% , but the recall value (0.91) for unhealthy loans is lower than the recall value (0.99) for healthy loans. 
![classification report](/images/report.png)
</br>

* In order to improve the accuracy and enhance the model's ability to detect errors in the classification of unhealthy loans, we can employ data oversampling. This involves using the RandomOverSampler module from the imbalanced-learn library to introduce additional instances of the minority class (unhealthy loans), thus achieving a more balanced dataset.
```
# code
y_oversampled.value_counts()

# output
0    56271
1    56271
Name: loan_status, dtype: int64
```
* The Logistic Regression Model, when trained with oversampled data, achieved an impressive accuracy score of 99%. Furthermore, the recall value for identifying unhealthy loans increased from 0.91 to 0.99. This improvement indicates that the model excels in its ability to detect errors, particularly in situations where high-risk loans are incorrectly labeled as low-risk or healthy.
![classification report oversampled](/images/oversampledreport.png)
## **results**
### Logistic Regression Model fitted with Imbalanced Data: 
</br>

* Accuracy score : 
    An accuracy score of 95% suggests that the model performed admirably. It accurately predicted the outcomes for 95% of the cases, which is indicative of its overall effectiveness. 
![accuracyScore rate](/images/accuracyScore.png)
* Precision score : 
    In this context, when it comes to the low risk class, the precision is 1.00, signifying that the model's predictions for the low-risk class were almost always accurate. On the other hand, for the high risk class, the precision is 0.85, indicating that when the model made predictions for the high-risk class, it was correct about 85% of the time.

* Recall score:  
    The recall values for both classes are notable. For the low risk class, the recall is 1.00, which means that the model correctly identified 100% of the actual low-risk cases. As for the high risk class, the recall is 0.88, indicating that the model accurately identified 88% of the actual high-risk cases.
</br>

### Logistic Regression Model fitted with oversampled Data:
<br>

* Accuracy score : 
    An accuracy score of 99% indicates that the model performed exceptionally well and achieved near-perfect accuracy. It accurately predicted the outcomes for 99% of the cases, suggesting a high level of performance and precision. 
![accuracyScore rateOverSample](/images/accuracyScoreOversampled.png)
* Precision score : 
    In this scenario, regarding the low risk class, the precision is 1.00, which implies that when the model made predictions for the low-risk class, it was almost always accurate. Conversely, for the high risk class, the precision is 0.84, indicating that when the model predicted the high-risk class, it was correct about 84% of the time.

* Recall score:  
   The recall values for both classes are remarkable. For the low risk class, the recall is 0.99, signifying that the model correctly identified 99% of the actual low-risk cases. Similarly, for the high risk class, the recall is also 0.99, indicating that the model accurately identified 99% of the actual high-risk cases.
</br>

## **summary**
The Logistic Regression model, when trained with Oversampled data, outperformed the model trained with Imbalanced data. This improvement is attributed to the balanced data, resulting in a significantly higher accuracy score and an increased recall value. These improvements indicate that the model is likely to make far fewer errors when classifying unhealthy loans, thereby enhancing its performance.
    
* Logistic Regression Model: 
  
    * 56 (FALSE POSITIVES) -->Incorrectly identified as unhealthy, these 56 instances were actually healthy.
    * 102 (FALSE NEGATIVES) -->"In truth, the loans were high-risk, but the predictions erroneously classified them as low-risk or healthy.
    ![Matrix](/images/matrix.png)
</br>

* Logistic Regression Model trained with RandomOverSampler: 
  
    * 4 (FALSE POSITIVES) --> Incorrectly identified as unhealthy, these 4 instances were actually healthy.
    * 116 (FALSE NEGATIVES) --> "In truth, the loans were high-risk, but the predictions erroneously classified them as low-risk or healthy.
    ![Oversampled matrix](/images/oversampledMatrix.png)