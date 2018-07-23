# flight_delays
General Assembly | Capstone project: predicting flight delays with aircrafts models and its makers


Kihoon Sohn | Data Science Immersive Student @ General Assembly | July 17, 2018

## Data Science Problem Statement

Can aircraft models or makers predict flights delays, in the local market?

## Executive Summary

Every year nearly 6 millions domestic passenger flights made in United States. We are certainly living in the world with air-travels. Despite the shortest travel time recorded between point A to point B, traveling with airplane requires passengers to have additional time needed before and after you are actually sitting in the aircraft; traveling to the airport, handling baggages, having security check, shopping some souvenirs and lined up for the boarding. After all, you are expecting to have your flight takes off on time to your destination. From the most recent monthly report that Bureau of Transportation Statistics, on-time performance is 80.33% for the year-to-date through April 2018.(https://www.bts.gov/content/summary-airline-time-performance-year-date-through-april-2018) In other words, one out of five you may experience any kinds of delays.

There are many prediction model on flight delays already out in the market. Google flights already built the system by using AI to predict the delays. In my capstone project, what I tried to build is, I would like to explore a certain aircraft model or its manufacturer can play any role in forecasting delays, unlike to the many other studies. If it is discovered that there is a positive relationship between the variables with the prediction, I would like to expand my research to comparing with each airline's fleet possession. This may go further to one of the considering factor to airline company's strategic decision whether to have diverse aircrafts models or minimize their inventory.

Due to the limited time and resources, I am not yet to be reached or finalized verifying my initial inference: aircrafts can be a predictor of the flight delays. I will gear up with more features by adding cleaned aircraft information and try different modeling. This executive summary and my entire project will be updated as I will be exploring further. Until then, here is what I've been made far in my research.

I got my 29-millions-data-points-sized-file of the on-time performance for the domestic passenger flights between 2013 to 2017. After the glimpse on the dataset and decided to subset it as local market observation with holidays time period. It ended up with the 520 thousands of records for the computational purpose. I ran for the Logistic Regression and Random Forest modeling to try out.

Since the dataset itself already contains what's the cause of its delays in five different categories, I used my target as binary classification on the delay time over 15 mins in either departure or arrival scene. Unlikely to the common conception as extreme weather will be the primary cause, late-arriving aircraft is the biggest reason of the flight delays. Therefore, I would like to gear my model with aircrafts model, manufacturer and its age, as I mentioned above. Hence I set my features as sin/cos time, distance, dummified all categorical variables, such as: day of week, carrier, airports, aircraft type, manufacturer, etc.

*The baseline accuracy were 0.7728 for not delayed, 0.2271 for delayed.* In my first model with *Logistic regression*, it slightly defeat the baseline as `train set: 0.7734`, `test set: 0.7731 `. It will be improved with some more feature engineering on my dataset. The next model is *Random Forest*, it turned out `train set: 0.9843`, `test set: 0.8498`. With GridSearchCV on RandomForest, as max-depth = 15 and n-estimator = 10, it got `train set: 0.7916`, `test set: 0.7901` beat the baseline.

In the confusion matrix, it showed as: precision `0.8578`, sensitivity `0.1036`, accuracy `0.7925` and specificity `0.9949`.


##### Disclaimer: All of the large data files ignored by `.gitignore`, therefore notebook might not reproduce same results without the datasets. Also, flightradar24 log-in credential muted for the security purpose.

--------------------------------------
## Data Science Tools and Methods Applied
### ML (Machine Learning)
 - Tried several models to predict.
   - RandomForest
   - LogisticRegression

### Webscrapping
 - To create automatic webscrapping for detailed information on the aircrafts
   - Selenium   

## Data Acquisition
### (1) On-Time Performance data from the Bureau of Transportation Statistics
 - Pulled monthly data on domestic passenger flights from the agency's website between 2013 January to 2017 December and aggregate them into one dataset.
 - Total volume of the combined dataset: 29 millions records.
   - Link: https://www.transtats.bts.gov/DL_SelectFields.asp?DB_Short_Name=On-Time&Table_ID=236


### (2) Aircraft information from flightradar24.com
 - The OTP dataset above contains aircraft tail number. Use this up-to-six-digits unique identifier of the aircraft as variable to my model.
 - Method of web-scraping: Selenium
   - Link: https://www.flightradar24.com/data/aircraft/ + {each tail no}


### Acknowledgements and references
##### (1) Ben Shaver
 - General Assembly's local instructor, Ben, helped a lot on the code challenges I had. Also, he showed his interests in this project and put a lot of his time working on the progress. I would like to acknowledge his help and dedication.

##### (2) kaggle Tutorial
 - https://www.kaggle.com/fabiendaniel/predicting-flight-delays-tutorial
 - This state of the art tutorial on predicting delays with strong visualization and codes guided me to unlock all the possibilities on this project. Many codes and plots, I commented in the notebook, were captured from this work. I would like to extend my appreciation to Mr. Fabien Daniel

##### (3) Cyclical time with sin and cos Time
 - https://ianlondon.github.io/blog/encoding-cyclical-features-24hour-time/
 - To use time vector as a variable to the model, I converted it to sin and cos time. The blog above and Ben Shaver, the GA local instructor, enable me to do this work.


##### (4) blog post from Ph.D Student in UC San Diego
 - https://srcole.github.io/2017/04/02/flight_delay/
 - Mr. Scott Cole's work also made me a lot of inspiration on this capstone project.


### Limitations and next steps

- Find more accurate dataset in aircraft information
- Bring time series analysis
- Build up Neural Networks
- Apply to the bigger dataset and play with in different angles. Such as, hub airports by airline, top 20 busiest airport, top 20 most frequent route between the two cities, etc.


## Directory of this repository

- README.md
   - Executive Summary and guide for the repository

- 00.Final_notebook.ipynb
   - contains final modelings and confusion matrix with the scores
   - Final notebook with all the other notebooks below.

- 01.Data Processing.ipynb
   - Import "on-time performance" from Bureau of Transportation Statistics

- 02.Selenium.ipynb
   - Web scrap the aircrafts information from Fllightradar24.common
   - This notebook will not work without login credential

- 03.EDA.ipynb
   - Basic EDAs on the datasets and plots
