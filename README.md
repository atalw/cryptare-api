# Cryptare API

## Overview

The Cryptare API gives access to the data used by the [Cryptare iOS App](). The initial versions of the app used a lot of the same data provided by this API, however each user requested data individually. At the time it made sense because the app was essentially a side project for myself. There was also no need for storage of the data. As the app grew, and the number of users started increasing, new features required access to the history of exchange market prices. There were several reasons why I felt the need for this API:

* Majority of exchanges do not provide access to their history of market statistics. This API stores this data which is publicly available anyway.
* Each exchange has their own API with different rules. This API standardizes it and removes the learning curve for developers.
* Having each user of the app make a new request to the Exchange API naturally increases the load on the Exchange server. Instead, a scalable solution would be to make a single request to the Exchange API and serve the response data to all the users. This API fulfills this need.
* Because the database is a [Firebase Real-time database](), observers can be set up to listen for changes in the database in real-time. This is ideal for the cryptocurrency environment, which changes practically every second.


## Design

The result of the API calls will return some or all of the following fields. This depends on the data provided by the exchange.

| Field        	| Description	
| :------------- |:-------------
| `buy_price` | Current buy (ask) price of the exchange 
| `sell_price`| Current sell (bid) price price of the exchange
| `max_24hrs` | Highest price in the past 24 hours  
| `min_24hrs` | Lowest price in the past 24 hours
| `vol_24hrs` or `coin_volume_24hrs` | Volume of coins transferred in the past 24 hours
| `vol_30days` | Volume of coins transferred in the past 30 days
| `fiat_volume_24hrs` | Amount of fiat money transferred in the past 24 hours
| `timestamp` | UNIX format timestamp of data entry   

### Coindesk ("INR", "USD", "GBP", "JPY", "CNY", "SGD", "EUR", "ZAR")

Coindesk is used to get the current price

* Supported coins = `["BTC"]`
* Supported currencies = `["INR", "USD", "GBP", "JPY", "CNY", "SGD", "EUR", "ZAR"]`

### Zebpay

URL: [https://atalwcryptare.firebaseio.com/zebpay.json?print=pretty](https://atalwcryptare.firebaseio.com/zebpay.json?print=pretty)

* Supported coins = `["BTC"]`
* Supported currencies = `["INR"]`.


```json
"-L-SPfZ4ioSx2LLNxlIX" : {
    "buy_price" : 841715.0,
    "sell_price" : 824881.0,
    "timestamp" : 1.512322021542984E9,
    "vol_24hrs" : 781.32573379
  }
```

Zebpay URL: [https://api.zebpay.com/api/v1/ticker?currencyCode=INR](https://api.zebpay.com/api/v1/ticker?currencyCode=INR)

	
### Coinsecure

URL: [https://atalwcryptare.firebaseio.com/coinsecure.json?print=pretty](https://atalwcryptare.firebaseio.com/coinsecure.json?print=pretty)

* Supported coins = `["BTC"]`
* Supported currencies = `["INR"]`


```json
"-L-R_7BcPPxe8I9tmz-p" : {
    "buy_price" : 849998.0,
    "coin_volume_24hrs" : 21.211,
    "fiat_volume_24hrs" : 1.779931356E7,
    "max_24hrs" : 850000.0,
    "min_24hrs" : 830000.0,
    "sell_price" : 841599.0,
    "timestamp" : 1.51230798052585E9
  }
```

Coinsecure URL: [https://api.coinsecure.in/v1/exchange/ticker](https://api.coinsecure.in/v1/exchange/ticker)

### Koinex

URL: [https://atalwcryptare.firebaseio.com/koinex\_BTC\_INR.json?print=pretty](https://atalwcryptare.firebaseio.com/koinex_BTC_INR.json?print=pretty)

Koinex supports several altcoins. In the URL, replace `COIN` in koinex_`COIN`\_INR with any one of these `["BTC", "BCH", "ETH", "LTC", "XRP"]`. For Example, [https://atalwcryptare.firebaseio.com/koinex\_LTC\_INR.json](https://atalwcryptare.firebaseio.com/koinex_LTC_INR.json)

* Supported coins = `["BTC", "BCH", "ETH", "LTC", "XRP"]`
* Supported currencies = `["INR"]`.

```json
"-L-SQr7i_0b-0GLPjMO_" : {
    "buy_price" : 855000.0,
    "max_24hrs" : 862500.0,
    "min_24hrs" : 770000.0,
    "sell_price" : 853500.0,
    "timestamp" : 1.512322331009709E9,
    "vol_24hrs" : 124.644
  }
```

Koinex URL: [https://koinex.in/api/ticker](https://koinex.in/api/ticker)

### Throughbit

### Pocketbits

URL: [https://atalwcryptare.firebaseio.com/pocketbits.json?print=pretty](https://atalwcryptare.firebaseio.com/pocketbits.json?print=pretty)

* Supported coins = `["BTC"]`
* Supported currencies = `["INR"]`.


```json
"-L-SPoFniEpq0B3yTGgT" : {
    "buy_price" : 849742,
    "sell_price" : 825349,
    "timestamp" : 1.51232205719493E9
  }
```

Pocketbits URL: [https://www.pocketbits.in/Index/getBalanceRates](https://www.pocketbits.in/Index/getBalanceRates)


### LocalBitcoins

URL: [https://atalwcryptare.firebaseio.com/localbitcoins\_BTC\_INR.json?print=pretty](https://atalwcryptare.firebaseio.com/localbitcoins_BTC_INR.json?print=pretty)

LocalBitcoins supports different currencies. In the URL, replace `CURRENCY` in localbitcoins_BTC\_`CURRENCY` with any one of these `["INR", "USD", "GBP", "CNY", "SGD", "EUR", "ZAR"]`. For Example, [https://atalwcryptare.firebaseio.com/localbitcoins_BTC\_SGD.json](https://atalwcryptare.firebaseio.com/localbitcoins_BTC_SGD.json)

* Supported coins = `["BTC"]`
* Supported currencies = `["INR", "USD", "GBP", "CNY", "SGD", "EUR", "ZAR"]`.


```json
 "-L-SPh4qGi1b8_10t3Uc" : {
    "buy_price" : 852800.0,
    "sell_price" : 810500.0,
    "timestamp" : 1.512322027783203E9,
    "vol_24hrs" : 14.60155067
  }
```

Localbitcoins URLs: 

* Buy: [https://localbitcoins.com/buy-bitcoins-online/{0}/.json](https://localbitcoins.com/buy-bitcoins-online/{}/.json)
* Sell: [https://localbitcoins.com/sell-bitcoins-online/{0}/c/bank-transfers/.json](https://localbitcoins.com/sell-bitcoins-online/{}/c/bank-transfers/.json)
* Volume: [https://localbitcoins.com/bitcoinaverage/ticker-all-currencies/](https://localbitcoins.com/bitcoinaverage/ticker-all-currencies/)
* Replace `{0}` with the desired currency.


### Coinbase

Example URL: [https://atalwcryptare.firebaseio.com/coinbase\_BTC\_USD.json?print=pretty](https://atalwcryptare.firebaseio.com/coinbase_BTC_USD.json?print=pretty)

General URL: `https://atalwcryptare.firebaseio.com/coinbase_{0}_{1}.json` where `{0}`= coin and `{1}`= currency.

* Supported coins = `["BTC", "ETH", "LTC"]`
* Supported currencies = `["USD", "GBP", "EUR"]`
* Note: Coinbase does not yet support `GBP` currency for `ETH` and `LTC`. _(5 Dec, 2017)_

```json
 "-L-Rx3Uxaz7JiUBVVHOU" : {
    "buy_price" : "11913.25",
    "max_24hrs" : 11795.0,
    "min_24hrs" : 10762.0,
    "sell_price" : "11677.34",
    "timestamp" : 1.512314257803914E9,
    "vol_24hrs" : 17214.74378967,
    "vol_30days" : 770063.73086679
  }
```

Coinbase URLs:

* Buy: [https://api.coinbase.com/v2/prices/{0}-{1}/buy](https://api.coinbase.com/v2/prices/{0}-{1}/buy)
* Sell: [https://api.coinbase.com/v2/prices/{0}-{1}/sell](https://api.coinbase.com/v2/prices/{0}-{1}/sell)
* Stats: [https://api.gdax.com/products/{0}-{1}/stats](https://api.gdax.com/products/{0}-{1}/stats)
* Replace `{0}` and `{1}` with the desired coin and currency pair.

### Kraken

Example URL: [https://atalwcryptare.firebaseio.com/kraken_BTC_USD.json?print=pretty](https://atalwcryptare.firebaseio.com/kraken_BTC_USD.json?print=pretty)

General URL: `https://atalwcryptare.firebaseio.com/kraken_{0}_{1}.json` where `{0}`= coin and `{1}`= currency.

* Supported coins = `["BTC", "ETH", "LTC"]`
* Supported currencies = `["USD", "GBP", "JPY", "CAD", "EUR"]`
* Note: Kraken only supports `["USD", "EUR"]` for `LTC`. _(5 Dec, 2017)_

```json
 "-L-aTXeq2CBrqCf1Ep9W" : {
    "buy_price" : 11650.0,
    "max_24hrs" : 11849.9,
    "min_24hrs" : 11006.3,
    "sell_price" : 11650.0,
    "timestamp" : 1.512316383052561E9,
    "vol_24hrs" : 3781.39453706
  }
```
Kraken URL: `https://api.kraken.com/0/public/Ticker?pair={0}{1}` where `{0}`= coin and `{1}`= currency.

Note: Kraken uses `XBT` instead of `BTC` to denote Bitcoin.


### Bitfinex

Example URL: [https://atalwcryptare.firebaseio.com/bitfinex\_BTC\_USD.json?print=pretty](https://atalwcryptare.firebaseio.com/bitfinex_BTC_USD.json?print=pretty)

General URL: `https://atalwcryptare.firebaseio.com/bitfinex_{0}_{1}.json` where `{0}`= coin and `{1}`= currency.

* Supported coins = `["BTC", "ETH", "LTC", "BCH", "XRP"]`
* Supported currencies = `BTC` has `["USD", "EUR"]` values. All other coins only have `["USD"]`.

```json
"-L-aY-Y4z8mq87TzvB4g" : {
    "buy_price" : 11666.0,
    "max_24hrs" : 11842.0,
    "min_24hrs" : 10718.0,
    "sell_price" : 11664.0,
    "timestamp" : 1.512475199170982E9,
    "vol_24hrs" : 58576.69881667
  }
```

Bitfinex URL: `https://api.bitfinex.com/v1/pubticker/{0}{1}` where `{0}`= coin and `{1}`= currency.

### Poloniex
Currently unsupported because Poloniex API access requires captcha verification. 

Poloniex URL: [https://poloniex.com/public?command=returnTicker](https://poloniex.com/public?command=returnTicker)

### Gemini

Example URL: [https://atalwcryptare.firebaseio.com/gemini\_BTC\_USD.json?print=pretty](https://atalwcryptare.firebaseio.com/gemini_BTC_USD.json?print=pretty)

General URL: `https://atalwcryptare.firebaseio.com/gemini_{0}_{1}.json` where `{0}`= coin and `{1}`= currency.

* Supported coins = `["BTC", "ETH"]`
* Supported currencies = `["USD"]`

```json
 "-L-aX1UZrGklkB4UHSPG" : {
    "buy_price" : 11691.78,
    "coin_volume_24hrs" : 7668.6324647363,
    "fiat_volume_24hrs" : 8.793478945770213E7,
    "sell_price" : 11691.77,
    "timestamp" : 1.512474945323566E9
  }
```

Gemini URL: `https://api.gemini.com/v1/pubticker/{0}{1}` where `{0}`= coin and `{1}`= currency.

### Bitstamp

Example URL: [https://atalwcryptare.firebaseio.com/bitstamp\_BTC\_USD.json?print=pretty](https://atalwcryptare.firebaseio.com/bitstamp_BTC_USD.json?print=pretty)

General URL: `https://atalwcryptare.firebaseio.com/bitstamp_{0}_{1}.json` where `{0}`= coin and `{1}`= currency.

* Supported coins = `["BTC", "ETH", "LTC", "XRP"]`
* Supported currencies = `["USD", "EUR"]`

```json
 "-L-SMU3d4YWpIp3ib080" : {
    "buy_price" : 11671.99,
    "max_24hrs" : 11800.01,
    "min_24hrs" : 10770.32,
    "sell_price" : 11661.01,
    "timestamp" : 1.512321182378586E9,
    "vol_24hrs" : 8015.99202548
  }
```

Bitstamp URL: `https://www.bitstamp.net/api/v2/ticker/{0}{1}` where `{0}`= coin and `{1}`= currency.

### Bittrex


