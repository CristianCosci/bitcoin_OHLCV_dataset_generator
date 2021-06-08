# bitcoin_OHLCV_dataset_generator
Jupyter Notebook  which allows you to create your own dataset with bitcoin "OPEN, HIGH, LOW, CLOSE" data, through the trades of different exchanges.

The data is taken from: 
  -Coinbase
  -Bitfinex
  -Kraken
  -Bitstamp
  -Itbit
  -Okcoin
  
To do this, I used the trade data provided in csv format by the https://bitcoincharts.com website.
The data starts from 01-01-2012

To create the candlestick dataset, the data was aggregated as follows:
- maximum of the interval for the HIGH data
- first of the interval for the OPEN data
- minimum of the interval for the LOW data
- last of the interval for the CLOSE data

The data aggregated is then averaged with the various exchanges
The volume data of the aggregated dataset is instead the sum of the trades of the corresponding interval but to have a better evaluation of the data only the most complete bitstamp exchange is used).
  
You can change the interval in which to aggregate the data by changing the "compression" parameter in the script. Now is set to 60min interval.
  
There may be some holes in the data where values are missing. I therefore decided to interpolate the data of a single exchange, that is the one with the most complete "Bitstamp" data. The type of interpolation used is a "slinear" interpolation which in the case of time series like this makes the data as clean as possible if the dataset were to be used for machine learning models.

To see the related study on interpolation look at this repo: https://github.com/CristianCosci/interpolationStudy_toHandleMissingData_BTCdataset

The data are for educational purposes only, it is not recommended to use this dataset for financial purposes
There are also some functions able to summarize some characteristics of the obtained datasets.

![image](https://user-images.githubusercontent.com/44636000/121206380-b39d6700-c878-11eb-98c3-585295fddabe.png)

![image](https://user-images.githubusercontent.com/44636000/121206459-c57f0a00-c878-11eb-835a-ad7673ad3ff6.png)

