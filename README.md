# SELFMiner
[![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=A8YE92K9QM7NA)

Mining Litecoin(Open Source) on Ubuntu OS by using CPUMiner(Open Source) connect to litecoinpool.org (For miners who want to mine Litecoin by yourself).

note : all fee-free!!!

## Requirement

- [x] Server
- [x] Wallet 
- [x] Miner
- [x] Pool

## Wallet

##### Installation

I recommended `Litecoin` wallet. Install it into your server :

```
wget https://github.com/downloads/litecoin-project/litecoin/litecoin-0.6.3c-linux.tar.gz
tar xzvf litecoin-0.6.3c-linux.tar.gz
cd litecoin-0.6.3c-linux/bin/##
sudo apt-get install libqtgui4
```

some one need this option :

```
sudo apt-get install libqtgui4:amd64
```

note : `##` in `cd litecoin-0.6.3c-linux/bin/##` means 32 or 64, it's base on your OS

##### Config your wallet

To use litecoind, you must set a rpcpassword in the configuration file `/home/ubuntu/.litecoin/litecoin.conf`. It is recommended you use the following random password :

```
rpcuser=ANY_USERNAME
rpcpassword=ANY_PASSWORD
```

Create litecoin.conf :

```
sudo nano /home/ubuntu/.litecoin/litecoin.conf
```

And modify it look like this :

```
rpcuser=ANY_USERNAME
rpcpassword=ANY_PASSWORD
rpcallowip=127.0.0.1
rpcport=9332
daemon=1
server=1
gen=0
```

##### Start Litecoin wallet service

```
cd ~/litecoin-0.6.3c-linux/bin/##
./litecoind
```

##### Stop the service

```
./litecoind stop
```

##### Create new wallet address

```
./litecoind getnewaddress YOUR_RPC_USER
```

note : Litecoin will return wallet address to you, it used to regist in litecoinpool.org

## litecoinpool.org

You need to register to the [pool](www.litecoinpool.org) first.
Set your Litecoin wallet address in `My Account` page.
After setting your account. It will show mining command look like this :

```
./minerd --algo=scrypt --url=stratum+tcp://HOST:PORT --userpass=WORKERNAME:PASSWORD
```

The command used to connect between `cpuminer` and `litecoin.org`.
Or you can download `mine.sh` from the website.

## Stratum protocal

Stratum is a proposal for an open source client-server `overlay` protocol that enables thin clients. It is currently used by Electrum. While originally announced right before 2012, the protocol has not yet been completed and proposed as a BIP for standardisation.

##### Installation

```
sudo apt-get install python-dev
git clone https://github.com/slush0/stratum-mining-proxy
cd stratum-mining-proxy
sudo python setup.py install
```

## CPUMiner

It is a multi-threaded, highly optimized CPU miner for Litecoin, Bitcoin, and other cryptocurrencies. Currently supported algorithms are SHA-256d and scrypt(N, 1, 1). It supports the getblocktemplate mining protocol as well as the Stratum mining protocol, and can be used for both solo and pooled mining.

ref : https://github.com/pooler/cpuminer

##### Installation

```
sudo apt-get install build-essential autoconf automake libtool pkg-config libcurl3-dev libudev-dev
git clone https://github.com/pooler/cpuminer
cd cpuminer
sh autogen.sh
./configure CFLAGS="-O3"
make
```

Now, you can mine Litecoin by using `./minerd --algo=scrypt --url=stratum+tcp://HOST:PORT --userpass=WORKERNAME:PASSWORD`.

Enjoy!!!

## Option

Mining Litecoin by using CPU, it will take many many many cost from your resources. For miner who don't care about it. I found some tools to support you :

##### CPULimit

Set your limit of CPU usage : `https://github.com/patharanordev/cpulimit/wiki/CPU-Usage-Limiter-for-Linux`.

Usage :

```
sudo cpulimit --limit 80 sh mine.sh
```

##### Bank

You should backup your coin data, example `coinbase`, ...

## Alternative mining

In case you concern about your resources. I recommended `TopMine`. All of the services are free of charge and are available for everyone. It looks like an investment system. Your miner performance upon `TeraX`.

See more detail via link image below :

[![ScreenShot](https://topmine.io/baners/728x90-Rumoviee.gif)](https://topmine.io/?reg=102963)

## Donation
If this project help you reduce time to develop, you can give me a cup of coffee :) 

#### Money


[![paypal](https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=A8YE92K9QM7NA)


#### Coin

- Bitcoin  : `1DG2i89xDYFfAeU7Kv5m79361AAwBANSfX`
- Litecoin : `DS7uUZ5WYhvMLSDu3hXicSQzeAXpJKcZCs`
- Dogecoin : `DS7uUZ5WYhvMLSDu3hXicSQzeAXpJKcZCs`

