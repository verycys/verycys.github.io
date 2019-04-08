---
title: "Freqtrade Trading Bot"
date: 2019-04-07
last_modified_at: 2019-04-07
---

## Installing Ubuntu
[https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop#0](https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop#0)

## Environment Settings
Freqtrade git repo: [https://github.com/freqtrade/freqtrade](https://github.com/freqtrade/freqtrade)
Freqtrade: [https://www.freqtrade.io/en/latest/](https://www.freqtrade.io/en/latest/)  
CCXT git repo: [https://github.com/ccxt/ccxt](https://github.com/ccxt/ccxt)  
MTG git repo: [https://github.com/MontrealTradingGroup](https://github.com/MontrealTradingGroup)

```sh
# setup
$ git clone https://github.com/freqtrade/freqtrade.git
$ cd freqtrade
$ git checkout develop
$ ./setup.sh --install

# pending this command
$ sudo apt install python3-pip
$ pip3 install virtualenv --user
$ sudo apt-get install make build-essential python3-dev

# try
$ source .env/bin/activate
$ python3.6 ./freqtrade/main.py -c config.json

# for fix error
# importerror: libta_lib.so.0: cannot open shared object file: no such file or directory
$ wget http://prdownloads.sourceforge.net/ta-lib/ta-lib-0.4.0-src.tar.gz
$ tar -xzf ta-lib-0.4.0-src.tar.gz
$ cd ta-lib/
$ ./configure --prefix=/usr
$ make
$ sudo make install
```

## Configuration
