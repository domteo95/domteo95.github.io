---
theme: jekyll-theme-minimal
layout: default
title: "Predicting if Android Apps will be Successful"
permalink: /android-apps-success/
---

# Predicting the success of Mobile Applications in the Google Play Store

This project was developed by Dominic Teo, Grace Prakaisriroj and Alessandro Luciano as our capstone group project for the undergraduate final year Statistics course ST309. 

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">

<p class="view"><a href="https://github.com/domteo95/ios-app-nba-players"><i class="fa fa-github" style="font-size:24px"></i>  View the Project on GitHub</a></p>

The more detailed report on the entire project can be found in the [pdf document](https://github.com/domteo95/predicting-popular-mobile-apps/blob/main/Final_report.pdf). Unfortunately, the **Rmarkdown file has been lost.** 

## Introduction

The global app economy is estimated to be worth 6.3 trillion USD by 2021, up from 1.3 trillion USD in 2018 (AppAnnie,2019). Over this period the user base will almost double from 3.4 billion people using apps to around 6.3 billion (AppAnnie, 2019).

This rapid market growth has produced no shortage of stories of individual app developers making great fortunes from their apps. However, the majority of developers are still struggling to break even (AppSurvey, 2013). For those unsuccessful app developers, a clear analysis of the characteristics of existing successful apps would provide a useful insight into creating apps that users want (Tian,2015). 

Therefore, the main goal of this project is to identify the characteristics that successful apps share and investigate which of these factors is important for success. This study is relevant for both developers and consumers, since both parties will benefit from a greater alignment of demand and supply in the app market; consumers will have a greater choice of apps they enjoy and developers will reap the financial gains of their work.

## Dataset Variables

Our final cleaned-dataset used in modelling has 13 predictor-variables (Android.Ver has been removed through EDA) in 8 dimensions and 6738 obervations in total.

The 8 dimensions we used for our analysis are:
- Success: For our outcome variable, we transformed the ‘installs’ feature into a numeric value and then defined a new variable, success, as those apps having more than 500,000 app downloads. Apps are typically profitable with 500,000 downloads (Louis,2013).58% of the observations were classified as successful.

![success](/assets/img/app-success/success-proportion.jpg)

- Rating: The rating factor is the overall user rating of the app. Higher rated apps have been shown tohave more downloads (Lanza,2012). Apps are rated from 1 to 5. 

- Size: The “Size of App” factor captures various information on the app. Large apps might contain more features or better functionality. Thus, they might have better ratings. On the other hand, larger apps also imply a higher probability to contain a bug and therein might have lower ratings (Zimmermann,2007).

- Category: For the category the app belongs to, we choose to recode the categories so that there were simply 4 categories: “Hobbies”, “Entertainment”, “Lifestyle”, and “Productivity”. We coded these 4 categories as 4 mutually exclusive and collectively exhaustive binary variables.

![categories](/assets/img/app-success/app-cat.jpg)

- Content Rating: For content rating we defined three age ratings: “Everyone”, “Mature 17+” and “Teen”. We recoded “Everyone 10+” and “Unrated” as “Everyone” and “Adults only 18+” as “Mature 17+” for simplicity. We coded these 3 ratings as 3 mutually exclusive and collectively exhaustive binary variables.

![rating](/assets/img/app-success/rating.jpg)

- Price: For the price of an app, we coded the input at a numeric value. The vast majority of apps are priced as free or for a very small fee (<$1). However, there are some outliers that charge >$300. These outlier apps could be classified as “Staus Apps” whereby customers purchase them to highlight their wealth e.g. VIP BLACK. With our definition of success, free apps tends to be more successful than paid by large. We expect price to be a significant variable that is negatively correlated to success in our model.

![paid](/assets/img/app-success/app-paid.jpg)

- Reviews: For the number of reviews, we simply coded this variable as a numeric value. There is a positive correlation between the number of reviews and the number of app downloads.

- Days Since Last Updated: As the variable “Last Updated” could impact the number of installs via appearing in the ‘newly updated tab’(thus attracting more traffic as there are more appstore users through time) in the google app store, we expect this variable to be significant. As the original “Last Updated” variable is a character class, we transformed it into a date and created a new variable,
“DaysSinceLastup”. This variable shows how many days ago the app was last updated (negative days) since 10/12/18, the day we downloaded the dataset.


## Methodology

Our project has two research questions:
1. What characteristics do successful apps share?
2. What factors are important for app success on the Google Play Store?

We applied 3 different classification modeling approaches to the data in order to find significant variables in determining the success of mobile apps. 
1. Logistic Regression

2. Decision Trees and Pruned Decision Trees

3. Random Forest 

## Results and Conclusion 

From our study and use of the 4 different models, we can conclude that the **random forest model** is most effective in predicting the success of mobile applications. Our random forest model demonstrates that **Price, Rating, DaysSinceLastUpdated and Size** are the most important variables used in the construction of the model.

This is important for developers who want to develop successful mobile applications. They should hence develop free applications with the aim of receiving high ratings in the Google Play Store. This could mean that developers trying to make money from their apps could stand to make their apps free but concentrate on in-app monetization opportunities instead. Making consumers pay for the app itself seems to be a major deterrent for users to download the app.

More interestingly, developers should also continuously and consistently update the app as we found that apps that were more recently updated tend to be more successful. We also found that overall, apps that were larger in size were more successful (although less significant than the other three variables). We think that size could be a good proxy for complexity and sophistication, hence apps that are more complex and developed tend to be more popular.

![result](/assets/img/app-success/android-success.jpg)

