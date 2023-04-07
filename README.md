# CatBoost_Gini_Based_Confidence_Estimates
A method to deduce important decision rules from the CatBoost model architecture

CatBoost has crappy documentation, but it seems like that they in general, do not provide much capability in terms of extracting decision rules. Scouring the internet, I found no real contribution with regards to what i wanted. I was not confident in the compentency of the CatBoost models. Knowing that basing feature based importances, also SHAP values, would lead me to making wrong conclusions on any feature.

I needed some sort of confidence estimate to back up any claims or choices. It was quite self-evident that we could merely calculate gini impurities for each prediction. Catboost doest not provide functionality to actually traverse the tree and extract the exact splits. But CatBoost does provide, the calc_leaf_indexes function, which we can use to obtain the leaf node index for a given prediction and then calculate the class distribution in that leaf to finally calculate the gini impurity of that leaf node. 
