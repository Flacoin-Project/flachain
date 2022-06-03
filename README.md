# Flachain Private Blockchain

<p><img src="https://avatars.githubusercontent.com/u/57708417?s=96&v=4" alt="Flacoin logo" title="Minig Flachain" align="right" height="100" /></p>


**Configure and operate Geth (Go-Ethereum) an Flachain Private blockchain for mining tokens**


**Overview**
  - [1- Install Geth and depends](#setup)
    - [2- Create folders project](#build)
    - [Config](#config)
  - [3- initializing geth](#operations)
  - [Commands geth for mining](#examples)
  - [Add Metamask config](#metamask)

### Setup
--------------

**Install geth and depends**

To enable our launchpad repository run:

```bash
sudo add-apt-repository -y ppa:ethereum/ethereum
```
```bash
sudo apt-get update
sudo apt-get install ethereum
```

#### Build

**Create local folder project**

```bash
git clone https://github.com/Flacoin-Project/flachain.git
cd flachain
mkdir node
```
**Done**


**Attention!!!**

Configure geth to boot into the folder we just created.

#### Config

**let's configure and run geth**

step 1

```bash
  geth --datadir ~/flachain/node init ~/flachain/genesis.json
```

-------------------------------

Step 2

```bash
  geth --datadir ~/flachain/node --config ~/flachain/config.toml console
```

-------------------------------


Step 3 

in geth console run command

**create new account address and create a password for your new account**

```bash
  personal.newAccount()
```

**Unlock your account for mining tokens**

```bash
  personal.unlockAccount(eth.accounts[0])
```

**Start mining...**

```bash
  miner.start(1)
```

**Stop mining...**

```bash
  miner.stop()
```


#### Operations

**Create geth.service file**

```
[Unit]
Description=Ethereum go client

[Service]
Type=simple
ExecStart=/usr/bin/geth --datadir ~/flachain/node --config ~/flachain/config.toml --http  --mine --miner.threads 1

[Install]
WantedBy=default.target

```

**Create geth service file in system**

```bash
   sudo nano /etc/systemd/system/geth.service
```
Copy and past the previous code save Done

**Start geth**

```bash
   sudo systemctl start geth
```

**Enable geth**

```bash
   sudo systemctl enable geth
```

**Stop geth**

```bash
   sudo systemctl stop geth
```

-----------------------

#### examples

**Some example commands for geth console**

```bash
   miner.start(1)
   miner.stop()
   web3.fromWei(eth.getBalance(eth.accounts[0]))
   net.peerCount
   eth.blockNumber
   admin.nodeInfo.enode
   eth.coinbase
   eth.getCoinbase(function(err, value) { console.log(value); })
   eth.accounts

```

Metamask
-------

Config network Flachain in Metamask

```
Network name: Flachain 

RPC url: https://data-seed.flacoin.org:2096

Chain ID: 29032022

Symbol: FLA

Url Explorer: Soon

```

**Thanks team Flacoin!**
