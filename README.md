# AirBnB Data Blog

### Table of Contents

1. [Installation](#installation)
2. [Project Motivation](#motivation)
3. [CRISP-DM Process](#crispdmprocess)
4. [File Descriptions](#files)
5. [Results](#results)
6. [Licensing, Authors, and Acknowledgements](#licensing)

## Installation <a name="installation"></a>

There should be no necessary libraries to run the code here beyond the Anaconda distribution of Python.  The code should run with no issues using Python versions 3.*.

## Project Motivation<a name="motivation"></a>

For this project, I was interested in using AirBnB data to better understand:

1. How well can we predict the listing prices ? 

2. Which attributes correlate the most with the price of the listing? 

3. Can we find a specific distribution of price changes during a whole calendar year ? 

4. What are the similarities and differences between the Boston and Seattle Data? 

## CRISP-DM Process <a name="crispdmprocess"></a> 

1. ### Business Understanding:  

   Using the data given from Seattle and Boston we intend to answer the questions mentioned above.

2. ### Data Understanding: 

   We have three tables for each city: i. listings, ii. calendar, iii. reviews.

   We will primary use the listings data for the price analysis. It has some descriptive textual data about the listing itself and the host. In addition to some categorical,  ordinal and numeric features. Our target variable here is numeric and is the price. 

2. ### Prepare Data: 

   For price analysis on the listings data. We first removed columns that had 1 value (or mostly one value with very few other values) and also data that is all NaNs or almost all NaNs. 

   Next looked at individual columns to asses the distribution of variables, dropped columns that had very little values or too much values. These would be problematic on creating dummy variables. 

   Chose only one neighborhood attribute the cleansed feature was more compact. 

   Next I converted the boolean variable from t/f to True/False. 

   Some other columns were processed separately as described in the notebook.

3. ### Model Data:

   For price analysis on the listings data, we apparently needed to use regression models to predict the price. Three models were compared and tuned: Support Vector Machine Regression (Linear Kernel performed best), Gradient Boosted Trees Regressors and the plain old Linear Regression. Their results were almost the same and no model was chosen over the other. 

4. ### Results:

   1. #### How well can we predict the listing prices ? 

      Our model has a Mean Absolute Error of $33~36 which means that we can trust our model price accuracy in the range of 33~36 dollars, which is not a strong model. The R2 score is around 0.5 which says that our model is intermediately good.  

   2. #### What correlates with Prices ? 

      We find really nteresting and sane results from the previous two graphs. 

      There is a positive postive correlation between number of accomadates, beds, bathrooms, bedrooms and guests_included and price. Which is quite sensible. 

      This gives insight for people who want to add listings to do their best to make their listings accomodate more people and guests. 

      On the other hand, being a private room or a shared room is affiliated with smaller prices which makes sense as other types of apartments are bigger and tend to be more expensive. This idea is confirmed by having room type home/apartment at the top of features correlating to higer prices. 

      On the side of neighbourhood, Other neighborhoods, Northgate, Deliridge and Rainer valley are correlating with lower prices while Queen anne has a positive correlation.

      Looking at the host attributes, superhosts usually have higher prices. Also, rows that had missing acceptance and response rates are attributed with a higher price which needs some investigation on why that is the case. Having a high response rate is attributed with lower prices, which means that picky hosts usually have higher prices. 

      Having a Doorman also is attributed to higher prices. 

5. ### Deploy:

   Price Analysis:

   Based on our analysis we think this info in addition to some NLP analysis of the description can be used to help hosts better tune their listings to attract customers and inform them about the expected range of the prices.

## File Descriptions <a name="files"></a>

There are 2 notebooks available here to showcase work related to the above questions.  Each of the notebooks is exploratory in searching through the data pertaining to the questions showcased by the notebook title.  Markdown cells were used to assist in walking through the thought process for individual steps.  

## Results<a name="results"></a>

Work-In-Progress

## Licensing, Authors, Acknowledgements<a name="licensing"></a>

Must give credit to AirBnB for the data.  You can find the Licensing for the data and other descriptive information at the Kaggle links available [here](https://www.kaggle.com/airbnb/seattle/data) and [here](https://www.kaggle.com/airbnb/boston).  Otherwise, feel free to use the code here as you would like! 
