---
title: "Algorithmic Trading: Backtest, Optimize & Automate in Python"
date: 2019-04-08
last_modified_at: 2019-04-08
---
이 강의노트는 Udemy에서 [Mohsen Hassan, Ilyass Tabiai - Algorithmic Trading: Backtest, Optimize & Automate in Python][1]를 보고 작성하였습니다.

## About Algorithmic Trading
> 시스템 트레이딩의 장단점과 오픈소스 소프트웨어 사용에 대해 설명합니다.

## Installations
> Installing Virtual Machine(Virtual Box, Linux), Ubuntu, Python Packages

MontrealTradingGroup git repo: [https://github.com/MontrealTradingGroup/deployPython3VM](https://github.com/MontrealTradingGroup/deployPython3VM)

## Virtual Machine: Linux Environment
> Linux 환경설정에 대해 설명합니다.

## Python Primer
> 파이썬의 기본문법에 대해 설명하며 Docs - Python Syntax에 정리하였습니다.

Caesar cipher: [http://practicalcryptography.com/ciphers/caesar-cipher/](http://practicalcryptography.com/ciphers/caesar-cipher/)

## Installing Freqtrade
> Freqtrade 오픈소스 소프트웨어 설치, git 설치에 대해 설명합니다.

Freqtrade git repo: [https://github.com/freqtrade/freqtrade](https://github.com/freqtrade/freqtrade)
Freqtrade: [https://www.freqtrade.io/en/latest/](https://www.freqtrade.io/en/latest/)  
CCXT git repo: [https://github.com/ccxt/ccxt](https://github.com/ccxt/ccxt)

## Configure And Run
> 텔레그램, 바이낸스 등과 연동 및 다른 요소들과의 설정을 마친 후 가상환경에서 트레이딩봇을 실행시킵니다. 그리고 실행된 전략인 `default_strategy.py`에 대한 설명을 합니다.

{% include figure image_path="/assets/images/posts/algo-01.png" alt="this is a placeholder image" caption="Ubuntu Terminal에서 트레이딩봇 실행화면" %}
{% include figure image_path="/assets/images/posts/algo-02.png" alt="this is a placeholder image" caption="Ubuntu Terminal에서 트레이딩봇 실행 시 텔레그램 메시지 수신화면" %}

```sh
# Run
# --dynamic-whitelist 200은 볼륨이 가장 높은 200개의 코인을 가지고 전략을 실행하라는 의미
$ python3.6 ./freqtrade/main.py -c config.json --dynamic-whitelist 200
```

## Strategy Implementation
> Strategy Development and Coding

- Bollinger Bands
- Relative Strength Index

위 2개의 indicator를 결합하여 전략구상 후 코딩하는 과정을 설명합니다. 코딩을 위해 `freqtrade/freqtrade/strategy` 디렉토리 안에 있는 파일들을 수정합니다.
> Backtesting Strategy

```sh
# 최초실행 or Dataset을 refresh하고 싶을 때
$ python3.6 ./freqtrade/main.py -c config.json -s BBRSI backtesting --refresh-pair

# 후속실행
$ python3.6 ./freqtrade/main.py -c config.json -s BBRSI backtesting

# timerange
$ python3.6 ./freqtrade/main.py -c config.json -s BBRSI backtesting --timerange=20190119-20190211

# 백테스팅 Data 저장 to >> freqtrade/user_data/backtest_data/backtest-result.json
# Plotting할 때 필요
$ python3.6 ./freqtrade/main.py -c config.json -s BBRSI backtesting --export trades
```
{% include figure image_path="/assets/images/posts/algo-03.png" alt="this is a placeholder image" caption="백테스팅 실행화면" %}
- 백테스팅 데이터는 `freqtrade/user_data/data/binance` 디렉토리에 저장됩니다.
- 위 전략에 대해 2019-03-05부터 2019-04-04까지 바이낸스 데이터를 가지고 백테스팅한 결과입니다.
- 가상으로 0.0116 BTC만큼 수익을 얻은 것을 확인할 수 있습니다.

> Plotting Results

```sh
# 백테스팅 결과 시각화
$ python3 ./scripts/plot_dataframe.py -s BBRSI -p ADA/BTC

# 사용한 indicator를 포함하여 시각화
$ python3 ./scripts/plot_dataframe.py -s BBRSI -p ADA/BTC --indicators1 bb_lowerband,bb_middleband,bb_upperband --indicators2 rsi
```
{% include figure image_path="/assets/images/posts/algo-04.png" alt="this is a placeholder image" caption="백테스팅 결과 시각화" %}
> Parameter to Optimize

- Sharpe Ratio
- Slippage

Parameter들을 optimize하기 위해 `freqtrade/freqtrade/optimize` 디렉토리 안에 있는 `default_hyperopt.py` 파일을 참고하여 `bbrsi_opt.py` 파일의 코드를 작성합니다.
```sh
# 최적지점을 찾기 위해 BBRSIOPT에 기재된 코드에 따라 100번, 5000번 계산합니다
python3 ./freqtrade/main.py -c config.json --customhyperopt BBRSIOPT hyperopt -e 100
python3 ./freqtrade/main.py -c config.json --customhyperopt BBRSIOPT hyperopt -e 5000

# timerange
python3 ./freqtrade/main.py -c config.json --customhyperopt BBRSIOPT hyperopt --timerange=20181208-20190118 -e 5000
```
{% include figure image_path="/assets/images/posts/algo-05.png" alt="this is a placeholder image" caption="100번 계산 후 최적화 결과" %}
실행된 결과값이 어떤 의미를 가지는지 설명한 후 현재의 strategy를 결과값에 따라 업데이트합니다.
> Optimize Strategy #39

1. Optimize 결과값을 현재의 strategy(bbrsi.py)에 업데이트 합니다.
  - ROI
  - Stoploss
  - Bollinger bands
  - Populate_buy_trend with rsi-value
  - Populate_sell_trend with rsi-value
2. Optimize된 strategy가 최적화 수익률과 동일한 결과값을 가지는지 백테스팅하여 확인합니다.

> Running the Strategy Live #41

1. dry_run을 false로 변경
2. aks가 아닌 bid에 있는 order_book의 가격으로 거래하기 위해 bid_strategy의 use_order_book를 true, ask_last_balance를 1로 변경

## Walkforward Analysis
```sh
# 데이터를 먼저 다운받은 후 실행해야 합니다
python3 ./freqtrade/main.py -c config.json --customhyperopt BBRSIOPT hyperopt --timerange=20181208-20190118 -e 100
```

## Freqtrade strategies repo
다음의 링크에서 다양한 전략들을 다운받아 활용할 수 있습니다.
[https://github.com/freqtrade/freqtrade-strategies](https://github.com/freqtrade/freqtrade-strategies)

[1]: https://www.udemy.com/algorithmic-trading-in-python/
