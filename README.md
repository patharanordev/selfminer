# SELFMiner

Mine Litecoin on Ubuntu OS by using CPUMiner connect to litecoinpool.org.
(For miners who want to mine Litecoin by yourself)

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

The command used connect between `cpuminer` and `litecoin.org`.

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
