# Stability-of-Grid-System
Electrical grids require a balance between electricity supply and demand in order to be stable. Conventional systems achieve this balance through demand-driven electricity production. For future grids with a high share of inflexible (i.e., renewable) energy source, the concept of demand response is a promising solution. This implies changes in electricity consumption in relation to electricity price changes. In this work, we’ll build a binary classification model to predict if a grid is stable or unstable using the UCI Electrical Grid Stability Simulated dataset.
## Dataset description
In this work, we will be using the dataset from the link https://archive.ics.uci.edu/ml/datasets/Electrical+Grid+Stability+Simulated+Data+  
## Predictive Feature
>>'tau1' to 'tau4': the reaction time of each network participant, a real value within the range 0.5 to 10 ('tau1' corresponds to the supplier node, 'tau2' to 'tau4' to the consumer nodes);
>>'p1' to 'p4': nominal power produced (positive) or consumed (negative) by each network participant, a real value within the range -2.0 to -0.5 for consumers ('p2' to 'p4'). As the total power consumed equals the total power generated, p1 (supplier node) = - (p2 + p3 + p4);
>>'g1' to 'g4': price elasticity coefficient for each network participant, a real value within the range 0.05 to 1.00 ('g1' corresponds to the supplier node, 'g2' to 'g4' to the consumer nodes; 'g' stands for 'gamma');
## Dependent Variables
>>'stab': the maximum real part of the characteristic differential equation root (if positive, the system is linearly unstable; if negative, linearly stable);
>>'stabf': a categorical (binary) label ('stable' or 'unstable').

Because of the direct relationship between 'stab' and 'stabf' ('stabf' = 'stable' if 'stab' <= 0, 'unstable' otherwise), 'stab' should be dropped and'stabf' will remain as the sole dependent variable (binary classification).

## Modelling
The dataset was splitted into an 80-20 train-test split with a random state of “1”. Normalization technique of the standard scaler to transform the train set (x_train, y_train) and the test set (x_test). We trained a random forest and extra trees classifier. And use xgboost and lightgbm to train an extreme boosting model and a light gradient boosting model. Also we set the random_state = 1 for training all models and evaluate on the test set.
## Evaluation
`Accuracy`
## Hyperparameter tuning of the XTraTreeClassifier
To improve the model, we carried out a hyperparameter tuning of the `ExtraTreeClassifier` using the `RandomizedSearchCV` technique.
