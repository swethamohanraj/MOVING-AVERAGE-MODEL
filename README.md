# EXP - 6 MOVING-AVERAGE-MODEL

## AIM:

Implementation of Moving Average Model Using Python.

## ALGROTHM:

1) Import necessary libraries
2) Read the electricity time series data from a CSV file,Display the shape and the first 20 rows of the dataset
3) Set the figure size for plots
4) Suppress warnings
5) Plot the first 50 values of the 'Value' column
6) Perform rolling average transformation with a window size of 5
7) Display the first 10 values of the rolling mean
8) Perform rolling average transformation with a window size of 10
9) Create a new figure for plotting,Plot the original data and fitted value
10) Show the plot

## PROGRAM:

python

import os
os.chdir("C:\\users\\monit\\TIME SERIES LAB\\")
import pandas as pd
import numpy as np
from matplotlib import pyplot
from statsmodels.tsa.ar_model import ExponentialSmoothing,SimpleExpSmoothing,Holt
import rcParams
rcParams['figure.figsize']= 20,5
import warnings
warnings.filterwarnings('ignore')
electricitytimeseries = pd.read_csv('Electric_Production.csv',header=0,index_col=0)
electricitytimeseries.shape
electricitytimeseries.head(20)

# MOVING AVERAGE METHOD
plt.plot(electricitytimeseries[1:50]['Value'])
plt.xticks(rotation=30)
plt.show()

# rolling average transfrom
rollingseries = electricitytimeseries[1:50].rolling(window=5)
rollingmean = rollingseries.mean()

#finding rolling mean MA(5)
print(rollingmean.head(10))

# plot transfrom dataset
rollingmean.plot(color='purple')
pyplot.show()

# rolling average transfrom
rollingseries = electricitytimeseries[1:50].rolling(window=10)
rollingmean = rollingseries.mean()
#finding rolling mean MA()
print(rollingmean.head(10))

# Exponential smoothing - single
data = electricitytimeseries[1:50]
fit1 = SimpleExpSmoothing(data).fit(smoothing_level=0.2,optimized=False)
fit2 = SimpleExpSmoothing(data).fit(smoothing_level=0.8,optimized=False)
plt.figure(figsize=(18,8))
plt.plot(electricitytimeseries[1:50],marker='o',color='black')
plt.xticks(rotation=30)
plt.plot(fit1.fittedvalues,marker='o',color='blue')
plt.plot(fit2.fittedvalues,marker='o',color='red')

## OUTPUT:

### Moving Average
<img width="506" alt="image" src="https://github.com/Monisha-11/MOVING-AVERAGE-MODEL/assets/93427240/e6423bc0-9dd1-4529-937d-fb17bffd2033">

### Plot Transform Dataset
<img width="506" alt="image" src="https://github.com/Monisha-11/MOVING-AVERAGE-MODEL/assets/93427240/100aa6e6-24f6-4831-b645-b10b9c668914">

### Exponential Smoothing

<img width="512" alt="image" src="https://github.com/Monisha-11/MOVING-AVERAGE-MODEL/assets/93427240/6ee4216f-21a7-4c63-a13f-b9e2257cf321">

## RESULT:
Thus we have successfully implemented the Moving Average Model using above mentioned program.
