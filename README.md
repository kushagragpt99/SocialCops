# Challenge 1: Agriculture Commodities, Prices & Seasons

Aim: Your team is working on building a variety of insight packs to measure key trends in the Agriculture sector in India. You are presented with a data set around Agriculture and your aim is to understand trends in APMC (Agricultural produce market committee)/mandi price & quantity arrival data for different commodities in Maharashtra.

## Objective:
  
1: Test and filter outliers.  
 Understand price fluctuations accounting the seasonal effect.  
 Detect seasonality type (multiplicative or additive) for each cluster of APMC and commodities.  
   De-seasonalise prices for each commodity and APMC according to the detected seasonality type.  
   Compare prices in APMC/Mandi with MSP(Minimum Support Price)- raw and deseasonalised.  
 Flag set of APMC/mandis and commodities with highest price fluctuation across different commodities in each relevant season, and year.  

 
## Description of frequently used variables
1:**data1**  Pandas dataframe with values in  CMO_MSP_Mandi.csv.   
  
**data2** - Pandas dataframe with values from _'Monthly_data_cmo.csv'_.  

**matrix2** - Numpy representation of data2.   

**matrix1** - Numpy representation of data1.   

**commodity_dict** - Dictionary with the commodities from data2 as keys and information about the commodities as values. Information is stored as numpy arrays in the same structure as given in data2.   


**APMC_dict** - Dictionary with the APMCs from data2 as keys and information about the APMCs as values. Information is stored as numpy arrays in the same structure as given in data2.   


**com_price** - dict with keys as commodities and values as their minimum support price.  

**exceeding_msp** - list with entries exceeding MSP given in CMO_MSP_Mandi.csv.  

**data3** - storing fluctuation (max_price - min_price) in a column of data3, sorted in descending order of fluctuation.   

**max_fluctuation_list** - list with entries corresponding to maximum fluctuation among a group whose membership is decided by APMC, commodity and year i.e 3 degrees of freedom for membership.  

## Methodology

### Preprocessing
NaN values are removed from the min_price, max_price, modal_price, and arrival_qty. Values with min_price>max_price are also removed to give positive fluctuation in each case.  

### Removing Outliers
An outlier is a piece of data that is an abnormal distance from other points. In other words, it’s data that lies outside the other values in the set.
 The most effective way to find all of your outliers is by using the interquartile range (IQR).
 The IQR contains the middle bulk of your data, so outliers can be easily found once you know the IQR. An outlier is defined as being any point of data that lies over 1.5 IQRs below the first quartile (Q1) or above the third quartile (Q3)in a data set.  
High = (Q3) + 1.5 IQR  
Low = (Q1) – 1.5 IQR  
In the case of quartiles, the Interquartile Range (IQR) may be used to characterize the data when there may be extremities that skew the data; the interquartile range is a relatively robust statistic (also sometimes called "resistance") compared to the range and standard deviation.  

### Understand price fluctuations accounting the seasonal effect  
Multiple approaches to detecting seasonality are used for the task.  datetime indexed
1. The first approach uses the seasonal decompose function of statsmodels library. Given dataframe is converted to a time series with
respect to an interval of months across the span of time range (2014 September to 2016) i.e 28 months. This datetime indexed pandas
time-series is broken to trend, seasonal and residual components according to the additive and multiplicative  seasonal model. Regression models are used to fit linear models on trend vs observed data
for additive decomposition and log of trend and observed data for multiplicative model.  

2. The second approach uses moving mean over 4 points to calculate the trend. Seasonality is detected by removing trend from the observed data (direct subtraction in the case of additive
model and subtraction after taking log in the case of multiplicatiev model).  

### Comparing with MSP
A loop is run over all values in data2, where the MSP of the commodity of the entry in the loop is compared with the min_price
of the entry in the loop. If value of min_price is less than MSP of that commodity ( detected from the com_price dict with keys as commodity
name and key as MSP of the ommodity) then that loop entry is adde to the list exceeding_msp.

### Highest Price Fluctuation   
data3 has entries of data2 sorted by fluctuation in descending order. An array of all zeros of size _no of commodities*no of APMC*no of years_ 
is created to keep a check on reoccurence of values identified by the above 3 metrics. passing through data3, the first occurence of commodity in an APMC in a year in data3 will have the maximum fluctuation as data3 is sorted in descending order of fluctuation.
 First occurence marks check_arr as 1 and no other values of the APMC*commodity*year is added to the max_fluctuation_list. 



[Link](url) and ![Image](https://github.com/kushagragpt99/SocialCops/tree/master/pictures/regression_mult.png)
```
