# Predict crypto using deep learning

### Description

This app uses the historical data of different crypto currencies to train deep learning models for each currency and predict
the currency direction price.

The app is mainly based on the Trader class which inheritates from the backtrader.client.Client adding more functionalities to make much easier the
training, prediction, buy and sell of the currencies.

### Getting Started

To start, we need to create the docker image
```console
git clone https://github.com/JonathanElejalde/playing_with_btc.git
cd playing_with_btc
docker build -f Dockerfile -t ml_strategy .
```

### Usage

Before we run the container, make sure to add your own keys for the binance API.
You can do this by adding keys.py as follows:

```python
api_key = "your api key"
secret_key = "your secret key"
```

or you can just add them directly in the app.py file when calling:

```python
trader = Trader('your api key', 'your secret key')
```

After this, we can run the app using the container
```console
docker run -v %cd%:/strategy -ti ml_strategy /bin/bash -c "cd strategy && python -W ignore app.py"
```
Change the %cd% with the absolute path where the playing_with_btc folder is.

#### Note

It will run in test mode, if you want to make real trading you will need to change TEST in the config.py file to True and 
use the trader.create_order function instead of trader.create_test_order. - For this, you just need to comment and uncomment the lines
in the app.py file-

### License

This project is licensed under the [MIT License](https://github.com/this/project/blob/master/LICENSE)

### Motivation

I've been learning trading and AI in parallel, so I wanted to create something that will involve both concepts just as a way to practice and not
thinking too much in making money.

### IMPORTANT

The app.py is an example and not a reliable way of making money. Thus, I recommend not to use it as a real trading strategy. However, 
you can use the concepts in this file to build your own reliable strategy.
