# Assignment-of-SMA-in-Python
#import the required libraries for SMA Technical Indicators value.

import pandas as pd

import quandl

import matplotlib.pyplot as plt

#API-Key Given From The Quandl.

auth_token = "YOUR API-KEY"

#define the Simple Moving Average such that it consider the Close price of the Given Stocks.

#and No. of days which can be defined further for Calculation of SMA.

def SMA(data,ndays):

    SMA = pd.Series(pd.rolling_mean(data['Close'],n),name = 'SMA')
    
    data = data.join(SMA)
    
    return data

#retrieve the data from qandl add your own simble i have just added gold symbol from MCX.

data = quandl.get('MCX/GCQ2017',start ='2016-08-12',end ='2017-07-24')

data = pd.DataFrame(data)


#define the Number of days you need to calcuate the Moving Average.

n = 20

SMG = SMA(data,n)

SMA = SMG['SMA']

#call the function to print the SMA.

print(SMG)

#Comment out Below if you need these Values in CSV Files.

SMG.plot()

#visualise the data 

plt.show()

#save the File into CSV

SMG.to_csv("FileName.csv")
