# Overview
Credit risk is an inherently unbalanced classification problem, as good loans easily outnumber risky loans. This work uses different techniques to train and evaluate models with unbalanced classes. Imbalanced-learn and scikit-learn libraries are used to build and evaluate models using resampling.

Using the credit card credit dataset from LendingClub, a peer-to-peer lending services company, the data is sampled using the RandomOverSampler and SMOTE algorithms, and undersampled using the ClusterCentroids algorithm. Then a combinatorial approach of over- and undersampling using the SMOTEENN algorithm is employed. Finally, e two new machine learning models that reduce bias are compared , BalancedRandomForestClassifier and EasyEnsembleClassifier, to predict credit risk. 

The performance of these models are analysed and compared and make a written recommendation on whether they should be used to predict credit risk.

# Results

To determine which model is best able to predict high credit risk clients we will focus on the balanced accuracy score, precision and recall score of the prediction models.
  
  accuracy score: The precentage of predictions that are correct (y_pred/y_test * 100)
  
  precision: precision is a measure of how reliable a positive classification is. It is calculated as                True Positives / (True Positives + False Positives)

  recall: Recall is a measure of what proportion of true events were classified as true. It is                     calculated as True Positives/(True Positives + False Negatives)
  
## Naive Random Oversampling
  
  The balanced accuracy score is 66.4%. The model is very good as predicting low risk individuals but poor at predicting high risk ones 1 vs. 0.01. Recall for high risk is fair at 71% and 62% for low risk. In other words the model makes too many false positives, classifies clients as high risk while the are in fact low risk.
  
![NaiveRandomOversampling.png](https://github.com/andrej-arsovski/Credit_Risk_Analysis_m17/blob/main/screenshots/NaiveRandomOversampling.png).

## SMOTE Oversampling

This method performs similarly to the previous. The balanced accuracy score is 66.4%. The model is very good as predicting low risk individuals but poor at predicting high risk ones 1 vs. 0.01. Recall for high risk is 65% and 67% for low risk. Again the model makes too many false positives, classifies clients as high risk while the are in fact low risk. 

![smote.png](https://github.com/andrej-arsovski/Credit_Risk_Analysis_m17/blob/main/screenshots/smote.png).

## Undersampling

This undersampling method performs similarly to the previous two. The balanced accuracy score is 66.4%. The model is very good as predicting low risk individuals but poor at predicting high risk ones 1 vs. 0.01. Recall for high risk is 67% and 40% for low risk. Again the model makes too many false positives, classifies clients as high risk while the are in fact low risk. 

![undersampling.png](https://github.com/andrej-arsovski/Credit_Risk_Analysis_m17/blob/main/screenshots/undersampling.png)

## Combination (Over and Under) Sampling

The combination method performs worse than the others. The balanced accuracy score is 53.9%. The model is very good as predicting low risk individuals but poor at predicting high risk ones 1 vs. 0.01. Recall for high risk is 73% and 56% for low risk. Again the model makes too many false positives, classifies clients as high risk while the are in fact low risk.

![combination.png](https://github.com/andrej-arsovski/Credit_Risk_Analysis_m17/blob/main/screenshots/combination.png)

## Balanced Random Forest

This ansemble algorithm performs better than the previous four. The balanced accuracy score is 78.9%. The model is very good as predicting low risk individuals but poor at predicting high risk ones 1 vs. 0.03. Recall for high risk is 70% and 87% for low risk. While the model makes considerably fewer false positives then the first 4 models it is still too many false positives, classifies clients as high risk while the are in fact low risk. 

![brf.png](https://github.com/andrej-arsovski/Credit_Risk_Analysis_m17/blob/main/screenshots/brf.png)

## Easy Ensemble AdaBoost Classifier

This ansemble algorithm is the strongest performing model. The balanced accuracy score is 93.2%. However, the model is again very good as predicting low risk individuals but poor at predicting high risk ones 1 vs. 0.09. Recall for high risk is 92% and 94% for low risk. While the model makes considerably fewer false positives then the first 5 models it is still too many false positives, classifies clients as high risk while the are in fact low risk.

![eec.png](https://github.com/andrej-arsovski/Credit_Risk_Analysis_m17/blob/main/screenshots/eec.png)

# Conclusion

While there are varying levels of performance amongst these models with the Easy Ensemble Classifier performing best, it is difficult to recomend any of these models as ready to use. All models are very poor at identifying high risk applications which is the main purpose of the models. The precision of the models does not even reach 10% for this group. What this means in practice is that an unacceptavbly high number of applicants will either get denied or they need to be further vetted. This is clear in the F1 scores of the models, the highest of which is 0.16. These scores are not acceptable for an in-use model. Further work is required to optimize and fine tune a model such as the Easy Assemble Classifier before it can be used in practice.
