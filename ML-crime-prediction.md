---
theme: jekyll-theme-minimal
layout: default
title: "Machine Learning Project - Predicting Violent Crime"
permalink: /ml-crime/
---

# Predicting Occurence of Violent Crime in Chicago

## Project Introduction

Final Project for CAPP 30254 - Machine  Learning for Public Policy. Completed by Dominic Teo, Eunjung Choi and Ya-Han Cheng.

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">

<p class="view"><a href="https://github.com/domteo95/ML-project"><i class="fa fa-github" style="font-size:24px"></i>  View the Project on GitHub</a></p>

Our project is titled **“Predicting whether a violent crime is likely to occur in Chicago based on past reported crime data, socio-economic indicators and weather data”**. This repository will contain both the relevant datasets that we use as well as the Jupyter Notebooks that we use to clean the data and also to create the various Machine Learning models that we use. 

# Datasets 
There are 4 different datasets that we use but only 3 datasets can be found in our repository, under the ‘Datasets’ folder, with the 4th one being downloaded in our Jupyter Notebook and they are titled as follows:

1. Reported crimes dataset (source: City of Chicago data portal): The file is too big to push into our repo. However, it can be easily downloaded at https://data.cityofchicago.org/Public-Safety/Crimes-2001-to-present/ijzp-q8t2. We utilized the 2015 data to present. 
2. Chicago boundaries neighbourhood dataset: "Boundaries-Neighborhoods.geojson"
3. Weather dataset (source: NOAA): “2162082.csv”

# Data Cleaning
The reported crimes dataset divides the types of crimes committed to many different types. The distribution of the top 15 types of crime can be seen below. 

![type](/assets/img/ML-crime/crime-type.jpg)

We then divided the different types of crimes into 2 types: violent and non-violent. 

![violent](/assets/img/ML-crime/violent.jpg)

However, we also provided the cleaned csv files that can be used directly without having to run through the data cleaning process. The full csv (around 1.2 million rows) is unfortunately too big to be pushed to our repository so we instead created a randomly sampled csv (10% of ‘crime.csv’), titled “crime_reduced.csv”. These csv files can then be used to run the other Jupyter Notebooks meant to create and evaluate the different machine learning models. 


# Methodology

We will assessing 4 different models and determining which model is best suited in predicting the occurence of violent crime. The following models will be assessed:

1. Decision Tree classifier
2. Random Forest classifier
3. Ada-Boost classifier
4. Logistic Regression classifier

For each model, we train the selected model using various parameters in order to choose the parameter combination that produces the highest accuracy score. With the identified combination we refit the model, and evaluate using confusion matrix and feature importances. 

For example, for our decision tree model, we run the following code for hyperparameter tuning::

```
tree_para = {'criterion': ['gini', 'entropy'],
             'max_depth': [3,5,7,9,11,13],
             'min_samples_split': [2,5,10]}

scorers = {'precision_score': make_scorer(precision_score),
           'recall_score': make_scorer(recall_score),
           'accuracy_score': make_scorer(accuracy_score)}

clf = GridSearchCV(DecisionTreeClassifier(random_state=0), tree_para, cv=10, 
                   scoring=scorers,refit=False)

clf.fit(X_train, y_train)

cv_results_df = pd.DataFrame(clf.cv_results_)

results = cv_results_df[['param_criterion', 'param_max_depth', 'param_min_samples_split', 
                         'mean_test_precision_score', 'mean_test_recall_score', 'mean_test_accuracy_score']]	
```

We then identify the parameter combination that produces the highest accuracy score

```
results[results['mean_test_accuracy_score']==max(results['mean_test_accuracy_score'])]
```

In this case it is the following combination:
- Parameter Criteria: Gini
- Parameter Max Depth: 9
- Parameter Min Samples Split: 5
- Mean Test Precision Score: 0.58472
- Mean Test Recall Score: 0.460015
- Mean Test Accuracy Score: 0.63754

We then refit our model with the identified parameter combination and identify which features are important to the model.

```
dt = DecisionTreeClassifier(criterion='gini', max_depth=9, min_samples_split=5)
model = dt.fit(X_train, y_train)
fi = pd.DataFrame({'feature': list(X_train.columns),
                   'importance': model.feature_importances_}).\
                    sort_values('importance', ascending = False)
                    fig, ax = plt.subplots(figsize=(12,6))
plot = sns.barplot(x=fi.feature[:12], y=fi.importance[:12], ax=ax)
plot.set_xticklabels(plot.get_xticklabels(), rotation=90, horizontalalignment='right')
``` 

![feature-importance](/assets/img/ML-crime/feature-importance.jpg)

We then repeat through the process for a random forest, logistic regression and ada-boost classifier. A quick clarification on the ada-boost classifier. It is a boosting ensemble model that works especially well with decision trees. Boosting model’s key is learning from the previous mistakes, e.g. misclassification data points - AdaBoost learns from the mistakes by increasing the weight of misclassified data points.