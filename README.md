# Predicting Airline On-Time Performance

---
## Content
 * [Problem Statement](##Problem-Statement)
 * [Dataset](##Dateset)
 * [Methodology](##Methadology)
 * [Model-Score](##Model-Score)
 * [Conclusion](##Conclusion)
 * [Opportunity For Improvement](##Opportunity For Improvement)
 

## Problem Statement
As a traveler, flying can be a frustrating and long endeavor especially during peak period. We often need to face unforeseen circumstances such as long immigration line and flight delays, or worse, lost baggage. In order to save guard ourselves, we are taught to get a travel insurance in case any of these circumstances were to happen. However, on the other side of the fence, insurance companies face the difficult task of predicting the likelihood of these outcomes to happen. Take for example, if the insurance company able to predict if a flight will delay before it departs, they are able to set a competitive pricing for their insurance products. 

---

## Dataset
In the project, I will be using dataset from Bureau Transportation of Statistics (USA) to predict if a flight will delay or on-time. There are two datasets that I will be using which are airline_list.csv and Delay_table.csv. The data in airline_list.csv shows the airline code and the corresponding airline name while the Delay_table.csv shows the flight information such as the date, airline code, origin and destination airport, scheduled departure and arrival time  and many more. Since there are no airline name information in Delay_table.csv, I will merge these two datasets so that I can get the airline name.


### Data Glossary
After cleaning and doing some EDA, I came up with this set of features that I will use for the modeling. In order to avoid data leakage, these features are carefully selected based on my domain knowledge so as there will be no future data provided to the model. 

|Feature|Description|
|----|----|
|year|Year|
|quarter|Quarter|
|month|Month|
|dayofmonth| Day of Month|
|dayofweek|Day of Week (Numeric)|
|flightdate|Date of Flight|
|flight_number_reporting_airline|Airline Unique Carrier Code|
|originairportid|Origin Airport ID|
|destairportid|Destination Airport ID|
|destcitymarketid|Destination City Market ID|
|destwac|Destination Airport World Area Code|
|crsdeptime|Computer Reservation System (Scheduled) Departure Time|
|crsarrtime|Computer Reservation System (Scheduled Arrival Time|
|airtime|Flight Time (Minutes)|
|flights|Number of Flights|
|distance| Distance Between Airport (miles)|
|distancegroup|250 Mile Distance Interval Group|
|airline|Airline Name|
|destcity|Destination City Name|

---

## Methodology
As a rule of thumb in the aviation industry, a flight is considered delay when it arrived at the destination airport more than 15 minutes than the scheduled arrival time. My target variable (y-axis) will be 'arrdel15'. I will be running all data from 2018 to 2020 from the final_table.csv to 2 models which are Logistic Regression and Random Forest. After which, I will extract the 10 best features combined from the 2 models first run to rerun again for the second time in hope to get better score. 


### Metric
The metrics used for this project is ROC-AUC score since there is an signifant imbalance in the data. Secondary to that I will also observe and rank the siginifant of each feature. 


### Data Imbalance
The data imbalance will be treated with class weight - balance in the model. 

---

## Model Score

First Run
|Model|Train Score|Test Score|Recall|Roc-AUC|
|----|----|----|----|----|
|Logistic Regression|65.65|65%|61%|65.1%|
|Random Forest|64.4%|62.6%|69%|62.9%|

Second Run
|Model|Train Score|Test Score|Recall|Roc-AUC|
|----|----|----|----|----|
|Logistic Regression|64.5|63.8%|59%|64.2%|
|Random Forest|63.8%|63.3%|67%|63.1%|

---

---

## Opportunity For Improvement
- Run other classification model such as Gradient Boost or a much simpler one such as Decision Tree
- Project has the potential to go beyond by predicting the minutes delay
- Further study on the dataset from Covid Impact. 

