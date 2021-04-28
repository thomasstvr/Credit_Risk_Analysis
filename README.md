# Credit Risk Analysis
In this project, we employ different techniques to train and evaluate models to predict credit risk. This can be tricky due to the inherent imbalance between the two classes: high risk and low risk. That is, the low-risk cases vastly outnumber the high-risk cases. 

To accomplish this, we employ six different models: RandomOverSampler, SMOTE, ClusterCentroids, SMOTEENN, BalancedRandomForestClassifer, and EasyEnsembleClassifier.

## Results
The results of these models vary widely and can be seen below:

* The RandomOverSampler model selects random instances of the under-represented class to balance the classes used in the training set. Here, RandomOverSampler had a balanced accuracy of 66.25%. The imbalanced classification report is shown below:

![]( https://github.com/thomasstvr/Credit_Risk_Analysis/blob/main/Resources/RandomOversampler.png)

With a precision of 1.00, this model does very well at predicting low-risk loans but fails to predict high-risk loans with a precision of .01. The recall is the same for both at .66 which yields an f1 score of .02 for high-risk and .80 for low-risk loans.

* The SMOTE (Synthetic Minority Oversampling Technique) model is another oversampling model but instead of randomly selecting instances of the underrepresented class it interpolates new instances. That is, new instances are created based upon the values of the current instances until the classes are balanced. With this data set, SMOTE had an accuracy of 66.21%. The imbalanced classification report can be seen below:

![]( https://github.com/thomasstvr/Credit_Risk_Analysis/blob/main/Resources/SMOTE.png)

Just as with the RandomOverSampler model, SMOTE does a great job at predicting low-risk loans while performing poorly at predicting high-risk loans. The precision is the same as the previous model but the recall is slightly different with a high-risk value of .63 and low-risk value of .69. This results in f1 scores of .02 and .82 for high-risk and low-risk, respectively.

* The ClusterCentroids is an under-sampling model that down sizes the class which is over represented in the data set. In particular, this model identifies clusters of the larger class then interpolates new instances based on the location of these clusters. This model yielded an accuracy of 54.43%, more results of using ClusterCentroids are shown below:

![]( https://github.com/thomasstvr/Credit_Risk_Analysis/blob/main/Resources/ClusterCentroids.png)

The outcome is much like what has been seen before with the exception being a drop in the low-risk recall which has a value of .4. So far, the ClusterCentroids under sampling model has been the worst predictor out of the set for this reason. 

* SMOTEENN is a combination of both over and under-sampling and is specifically a combination of SMOTE and Edited Nearest Neighbors. The model first uses SMOTE to over sample the data then cleans it by dropping points whose two nearest neighbors belong to different classes. The accuracy of this model was 64.47% with further results being shown below:

![]( https://github.com/thomasstvr/Credit_Risk_Analysis/blob/main/Resources/SMOTEENN.png)

The precision is once again .01 and 1.00 for high-risk and low-risk respectively but the recall comes in at .72 and .57. This results in an f1 score for high-risk loans of .02 and .72 for low-risk loans. Unfortunately, the SMOTE model performed better in predicting loan risk.

* The next model is an ensemble classifier called BalancedRandomForestClassifer. This model balances the weight of the classes and uses several decision trees (in our case 100) built from a random subset of features to collectively predict an outcome. This model worked quite well with an accuracy of 99.97%. More results are shown below:

![]( https://github.com/thomasstvr/Credit_Risk_Analysis/blob/main/Resources/BalancedRandomForestClassifier.png)

With a precision of .90 and 1.00, a recall of 1.00 and 1.00, and an f1 score of .95 and 1.00 for high-risk and low-risk, respectively, this is our best model yet.

* The last model used is the EasyEnsembleClassifier which uses random under-sampling to reach a balance between the classes then uses AdaBoost learners trained on different boostrap samples, that is, according to the [documentation]( https://imbalanced-learn.org/stable/references/generated/imblearn.ensemble.EasyEnsembleClassifier.html). We employed this model with 100 samples. This model was our best yet with an accuracy of 1.0 and a perfect performance everywhere else, see below:

![]( https://github.com/thomasstvr/Credit_Risk_Analysis/blob/main/Resources/EasyEnsembleClassifier.png)


## Summary 
In conclusion, the two ensemble models (BalancedRandomForestClassifer and EasyEnsembleClassifier) performed better than any of the other models. Although this looks good on paper, it does have me concerned about overfitting. Overfitting occurs when a model is to well fit to its specific set of training and testing data that it does not perform well in the real world. 

Of the six models, I would choose to employ the BalancedRandomForestClassifer model due to the lower possibility of it being over fit and its high performance. With such a low precision and recall for high-risk loans, RandomOverSampler, SMOTE, ClusterCentroids, and SMOTEENN just aren’t viable models for predicting high-risk loans. If the goal were to only predict low-risk loans 
