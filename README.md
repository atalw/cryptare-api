# Cryptare API

## Overview

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

### Zebpay (INR)

URL: [https://atalwcryptare.firebaseio.com/zebpay.json](https://atalwcryptare.firebaseio.com/zebpay.json)


```json
"-L-SPfZ4ioSx2LLNxlIX":
	{
		"buy_price": 841715.0,
		"sell_price": 824881.0,
		"timestamp": 1512322021.542984,
		"vol_24hrs": 781.32573379
	}
```

Zebpay URL: [https://api.zebpay.com/api/v1/ticker?currencyCode=INR](https://api.zebpay.com/api/v1/ticker?currencyCode=INR)


	
### Coinsecure (INR)

URL: [https://atalwcryptare.firebaseio.com/coinsecure.json](https://atalwcryptare.firebaseio.com/coinsecure.json)


```json
"-L-R_7BcPPxe8I9tmz-p": {
	 "buy_price": 849998.0,
	 "coin_volume_24hrs": 21.211,
	 "fiat_volume_24hrs": 17799313.56,
	 "max_24hrs": 850000.0,
	 "min_24hrs": 830000.0,
	 "sell_price": 841599.0,
	 "timestamp": 1512307980.52585
   }
```

Coinsecure URL: [https://api.coinsecure.in/v1/exchange/ticker](https://api.coinsecure.in/v1/exchange/ticker)

### Koinex (INR)

URL: [https://atalwcryptare.firebaseio.com/koinex\_BTC\_INR.json](https://atalwcryptare.firebaseio.com/koinex_BTC_INR.json)

Koinex supports several altcoins. In the URL, replace `COIN` in koinex_`COIN`\_INR with any one of these `["BTC", "BCH", "ETH", "LTC", "XRP"]`. For Example, [https://atalwcryptare.firebaseio.com/koinex\_LTC\_INR.json](https://atalwcryptare.firebaseio.com/koinex_LTC_INR.json)

```json
"-L-SQr7i_0b-0GLPjMO_": {
	 "buy_price": 855000.0,
	 "max_24hrs": 862500.0,
	 "min_24hrs": 770000.0,
	 "sell_price": 853500.0,
	 "timestamp": 1512322331.009709,
	 "vol_24hrs": 124.644
   }
```

Koinex URL: [https://koinex.in/api/ticker](https://koinex.in/api/ticker)

### Throughbit (INR)

### Pocketbits (INR)

URL: [https://atalwcryptare.firebaseio.com/pocketbits.json](https://atalwcryptare.firebaseio.com/pocketbits.json)


```json
"-L-SPoFniEpq0B3yTGgT": {
    "buy_price": 849742,
    "sell_price": 825349,
    "timestamp": 1512322057.19493
  }
```

Pocketbits URL: [https://www.pocketbits.in/Index/getBalanceRates](https://www.pocketbits.in/Index/getBalanceRates)


### LocalBitcoins ("INR", "USD", "GBP", "CNY", "SGD", "EUR", "ZAR")

URL: [https://atalwcryptare.firebaseio.com/localbitcoins\_BTC\_INR.json](https://atalwcryptare.firebaseio.com/localbitcoins_BTC_INR.json)

LocalBitcoins supports different currencies. In the URL, replace `CURRENCY` in localbitcoins_BTC\_`CURRENCY` with any one of these `["INR", "USD", "GBP", "CNY", "SGD", "EUR", "ZAR"]`. For Example, [https://atalwcryptare.firebaseio.com/localbitcoins_BTC\_SGD.json](https://atalwcryptare.firebaseio.com/localbitcoins_BTC_SGD.json)

```json
 "-L-SPh4qGi1b8_10t3Uc": {
    "buy_price": 852800,
    "sell_price": 810500,
    "timestamp": 1512322027.783203,
    "vol_24hrs": 14.60155067
  }
```

Localbitcoins URLs: 

* Buy: [https://localbitcoins.com/buy-bitcoins-online/{}/.json](https://localbitcoins.com/buy-bitcoins-online/{}/.json)
* Sell: [https://localbitcoins.com/sell-bitcoins-online/{}/c/bank-transfers/.json](https://localbitcoins.com/sell-bitcoins-online/{}/c/bank-transfers/.json)
* Volume: [https://localbitcoins.com/bitcoinaverage/ticker-all-currencies/](https://localbitcoins.com/bitcoinaverage/ticker-all-currencies/)


### Coinbase

### Kraken

### Bitfinex

### Bittrex

### Gemini

### Bitstamp

