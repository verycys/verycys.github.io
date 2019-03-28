---
title:  "Python Binance 01"
date:   2019-03-28
last_modified_at: 2019-03-28
---
이 프로젝트는 암호화폐 자동매매 프로그램을 만들기 위해 시작하였습니다. Github에서 [Sammchardy/python-binance][1] 코드와 [Roibal/Cryptocurrency-Trading-Bots-Python-Beginner-Advance][2] 코드를 이해한 후 Roibal의 Trading Bot을 커스터마이징 할 계획입니다. Roibal의 코드에 대한 강의는 Youtube - [Blockchain Engineer][3] 채널에서 볼 수 있습니다. Sammchardy의 python-binance Docs는 다음의 [링크][4]에서 볼 수 있습니다.

## Structure
> 루트 디렉토리 구조입니다. 아직은 파일들의 필요유무가 파악이 되지 않아 다 기재하였으나 코드를 보면서 필요없는 파일들은 삭제할 것입니다.

Sammchardy의 python-binance v0.7.1을 다운받아 루트 디렉토리로 잡은 후 Roibal의 Cryptocurrency-Trading-Bots-Python-Beginner-Advance를 examples 디렉토리 안에 다운받았습니다.

```sh
├── binance
│   ├── __init__.py
│   ├── client.py
│   ├── depthcache.py
│   ├── enums.py
│   ├── exceptions.py
│   ├── helpers.py
│   └── websockets.py
├── examples
│   ├── BinanceKeys.py
│   ├── Cryptocurrency-Trading-Bots-Python-Beginner-Advance-master
│   │   ├── BinanceKeys.py
│   │   ├── BinanceTriArbTrader.py
│   │   ├── Binance_Triangular_Arbitrage_DataCollection.py
│   │   ├── Crypto-Trading-Bots
│   │   │   ├── Advanced_Cryptocurrency_Trading_Bot.py
│   │   │   ├── Crypto_Sentiment_Analysis_SocialMedia_Bot.py
│   │   │   ├── Roibal_BinanceBot.py
│   │   │   └── TradingView_SignalScraper.py
│   │   ├── CryptoTriArbBot_DataLog.txt
│   │   ├── Historic-Legacy
│   │   │   ├── CryptoTriangularArbitrageBinanceBot.py
│   │   │   ├── Private_TriArbBot.py
│   │   │   ├── Sentiment_Analysis_Crypto_Historic.py
│   │   │   ├── TriArbBot_Paper_and_Tweet.py
│   │   │   └── readme.md
│   │   ├── LICENSE
│   │   ├── Portfolio.txt
│   │   ├── Portfolio_fees.txt
│   │   ├── Portfolio_fees_Rates.txt
│   │   ├── README.md
│   │   ├── Stochastic_Crypto_Pandas_Stock.py
│   │   ├── list_fees_paid.txt
│   │   └── save_historical_data_Roibal.py
│   ├── RoibalBot.py
│   ├── readme.md
│   ├── save_historical_data.py
│   └── save_historical_data_Roibal.py
├── tests
│   ├── __init__.py
│   ├── test_api_request.py
│   ├── test_depth_cache.py
│   └── test_historical_klines.py
├── LICENSE
├── PYPIREADME.rst
├── README.rst
├── setup.cfg
├── setup.py
├── test-requirements.txt
├── tox.ini
├── requirements.txt
└── venv
```

## Helpers.py
> Helpers.py head

```python
import dateparser
import pytz

from datetime import datetime
```
***
> def date_to_milliseconds(date_str):

```python
def date_to_milliseconds(date_str):
    """Convert UTC date to milliseconds

    If using offset strings add "UTC" to date string e.g. "now UTC", "11 hours ago UTC"

    See dateparse docs for formats http://dateparser.readthedocs.io/en/latest/

    :param date_str: date in readable format, i.e. "January 01, 2018", "11 hours ago UTC", "now UTC"
    :type date_str: str
    """
    # get epoch value in UTC
    epoch = datetime.utcfromtimestamp(0).replace(tzinfo=pytz.utc)
    # parse our date string, UTC시간 출력함수
    d = dateparser.parse(date_str)
    # if the date is not timezone aware apply UTC timezone
    if d.tzinfo is None or d.tzinfo.utcoffset(d) is None:
        d = d.replace(tzinfo=pytz.utc)

    # return the difference in time
    return int((d - epoch).total_seconds() * 1000.0)
```
해당 함수는 epoch[^1]로부터 date_str까지의 경과시간을 milliseconds(천분의 일초)로 바꾸는 함수이다. date_str을 입력할 때는 ‘now UTC’ 또는 ’11 hours ago UTC’ 형식으로 입력해야 한다. 실험적으로 date_str에 1970년 2월 1일을 입력하니 2678400000이 출력되었다. 31일 * 24시간 * 60분 * 60초 * 1000초는 2678400000 이다.[^2]

## Footnote

[1]: https://github.com/sammchardy/python-binance
[2]: https://github.com/Roibal/Cryptocurrency-Trading-Bots-Python-Beginner-Advance
[3]: https://www.youtube.com/channel/UCVTnyT4fUxYkvawbggo8-AQ/featured
[4]: https://python-binance.readthedocs.io/en/latest/

[^1]: epoch는 1970년 1월 1일 00:00:00 협정 세계시를 의미한다.
[^2]: [파이썬 시간모듈 정리 링크](https://devanix.tistory.com/297)
