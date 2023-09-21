# Hateful Speech Classification
## Summary
### Models Considered
- Logistic Regression
- MultinomialNB
- XGBoost
- Extra Trees Classifier
- VotingClassifier
### Other libraries used
- TPOT: Python Automated Machine Learning tool that optimizes machine learning pipelines using genetic programming. Can output pipelines that combines/stack multiples models + preprocessors in its default state.
- Optuna: Hyperparameter tuning framework which can find the optimal machine learning in a large search space comparable to that of Random Grid Search, but with smarter choices of hyperparameters in each iteration and faster rate of model evaluation, ultimately leading to faster convergence.
### Approaches to model training/evaluation
Evaluate all the above models using Stratified 3 Fold Cross Validation; most of them are optimised using Optuna
Utilise TPOT to search for machine learning pipelines that was not previously considered.
### How we arrived at final model
ExtraTreesClassifier performed well on public dataset.
Pipelines output from TPOT also performed well on public dataset.
In order to prevent overfitting and improve model performance through the use of independent classifiers, we created a Voting Classifier with soft voting from a few classifier pipelines from TPOT (which we called cl0, cl2 and cl12) with an Extra Trees Classifier (which we called etc).
We then used Optuna to optimise the weights assigned to each of the above classifiers.
