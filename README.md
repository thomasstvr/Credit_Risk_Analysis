# Credit Risk Analysis
In this project, we employ different techniques to train and evaluate models to predict credit risk. This can be tricky due to the inherent imbalance between the two classes: high risk and low risk. That is, the low-risk cases vastly outnumber the high-risk cases. 

To accomplish this, we employ six different models: RandomOverSampler, SMOTE, ClusterCentroids, SMOTEENN, BalancedRandomForestClassifer, and EasyEnsembleClassifier.

## Results
The results of these models vary widely and can be seen below:

* The RandomOverSampler model selects random instances of the under-represented class to balance the classes used in the training set. Here, RandomOverSampler had a balanced accuracy of 66.2%. The imbalanced classification report is shown below:

![]( https://github.com/thomasstvr/Credit_Risk_Analysis/blob/main/Resources/RandomOversampler.png)
