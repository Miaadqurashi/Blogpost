# AirBnB Data Blog

### Table of Contents

1. [Installation](#installation)
2. [Project Motivation](#motivation)
3. [CRISP-DM Process](#crispdmprocess)
4. [File Descriptions](#files)
5. [Licensing, Authors, and Acknowledgements](#licensing)

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

3. ### Prepare Data: 

   For price analysis on the listings data. We first removed columns that had 1 value (or mostly one value with very few other values) and also data that is all NaNs or almost all NaNs. 

   Next looked at individual columns to asses the distribution of variables, dropped columns that had very little values or too much values. These would be problematic on creating dummy variables. 

   Chose only one neighborhood attribute the cleansed feature was more compact. 

   Next I converted the boolean variable from t/f to True/False. 

   Some other columns were processed separately as described in the notebook.

   

   For Calendar prices analysis,  first the listings that had prices all year long were analyzed first. String data were changed from t/f to True/False and from $## to ##.00. Some random trends were plotted to get an idea of the distribution of prices. A recurrent change was present, that is listings have a different price on weekend nights (Friday and Saturday). 

4. ### Model Data:

   For price analysis on the listings data, we apparently needed to use regression models to predict the price. Three models were compared and tuned: Support Vector Machine Regression (Linear Kernel performed best), Gradient Boosted Trees Regressors and the plain old Linear Regression. Their results were almost the same and no model was chosen over the other. 

   

   For Calendar prices analysis,  later on we wanted to visualize the trends of multiple trends together. To do that we normalized each graph and added them all together and then normalized the output. In order to add the trends of the listings that did not have values all year long, the missing values was filled with the mean of the available prices. Only listings with at least prices available half-year long. My reasoning of filling with mean is that on normalizing it will have no affect when adding the variables. 

5. ### Results:

   1. #### How well can we predict the listing prices ? 

      Our model has a Mean Absolute Error of $32 which means that we can trust our model price accuracy in the range of about 32 dollars, which is not a strong model. The R2 score is around 0.57 which says that our model is intermediately good.  

   2. #### What correlates with Prices ? 

      We find really nteresting and sane results from the previous two graphs. 

      There is a positive postive correlation between number of accomadates, beds, bathrooms, bedrooms and guests_included and price. Which is quite sensible. 

      This gives insight for people who want to add listings to do their best to make their listings accomodate more people and guests. 

      On the other hand, being a private room or a shared room is affiliated with smaller prices which makes sense as other types of apartments are bigger and tend to be more expensive. This idea is confirmed by having room type home/apartment at the top of features correlating to higer prices. 

      On the side of neighbourhood, Other neighborhoods, Northgate, Deliridge and Rainer valley are correlating with lower prices while Queen anne has a positive correlation.

      Looking at the host attributes, superhosts usually have higher prices. Also, rows that had missing acceptance and response rates are attributed with a higher price which needs some investigation on why that is the case. Having a high response rate is attributed with lower prices, which means that picky hosts usually have higher prices. 

      Having a Doorman also is attributed to higher prices. 
      
   3.  #### Can we find a specific distribution of price changes during a whole calendar year ?

      Yes, we find two finding from analyzing the trend of prices:

      1. A majority of hosts have a higher price on weekend nights i.e. Fridays and Saturdays.
      2. There appears to be a trend of increase of prices from the beginning of the year and it peaks during the summer period especially from June to Septembers. After that the prices decrease a little back to the mean value. 

   4. #### What are the similarities and differences between the Boston and Seattle Data? 

      1. Prices:

         Our best model performed worse than on the Seattle Data set with $43 of mean absolute error an 0.50 R2 score.

         Comparing the top weights of LinearSVR model we find several similarities and differences. 

         Number of bedrooms, accommodates and being an Entire home are among the top features that correlate positively with the price in both datasets.  Also, being an Entire home or shared are among the top features that correlate negatively with the price in both datasets.  

         The main difference noticed is the presence of longitude and latitude in the top positively correlating features. The suggest that the easter and norther you get the higher the prices tend to be. 

      2. Calender Price trends:

         In addition to the normal trend of difference between Weekends and Weekdays in price, there appears to be spikes in prices in mid June, mid July and in October. 

6. ### Deploy:

   Price Analysis:

   Based on our analysis we think this info in addition to some NLP analysis of the description can be used to help hosts better tune their listings to attract customers and inform them about the expected range of the prices.

   For Calendar prices analysis:

   

## File Descriptions <a name="files"></a>

1. Understanding.ipynb: This notebooks imports the datasets for the first time and begin to get the data and business understanding. 
2. PrepareAssesQ1_andQ2.ipynb: This notebook analyzes the listings.csv data and attempts to predict prices and find correlations between features and price. This is the main notebook used to answer questions 1 and 2. 
3. PrepareAssesQ1_andQ2_boston.ipynb: Same process repeated on the Boston data in an attempt to compare them together. 
4. Calendar_analysis.ipynb: This notebook aims to analyze the prices troughout the year from the calendar.csv data.
5. Calendar_analysis_boston.ipynb: Same process repeated on the Boston data in an attempt to compare them together. 
6. seattle/* and boston-airbnb-open-data/* hold the data sets used for analysis. sources are in the next session.

## Licensing, Authors, Acknowledgements<a name="licensing"></a>

Must give credit to AirBnB for the data.  You can find the Licensing for the data and other descriptive information at the Kaggle links available [here](https://www.kaggle.com/airbnb/seattle/data) and [here](https://www.kaggle.com/airbnb/boston).  Otherwise, feel free to use the code here as you would like! 
