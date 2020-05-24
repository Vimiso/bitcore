## Setting up GitHub
```
ssh-keygen -t rsa -C "email@gmail.com"
ssh-add ~/.ssh/github
# add public key to github account
git config --global user.name "Vimiso"
git config --global user.email "email@gmail.com"
ssh -T git@github.com
```

## Prerequisites
```
# install nvm
nvm install v8.16.2
apt install npm
npm install npm -g
apt install libzmq3-dev
apt install build-essential
apt install -y mongodb
systemctl status mongodb
npm install forever -g
```

## Installing Bitcore
```
cd /var
git clone https://github.com/Vimiso/bitcore.git
cd /var/bitcore
git checkout master
npm install --unsafe-perm
# add bitcore.config.json
npm run node
```

## Bitcoin Node:
```
mkdir ~/.bitcoin
cd ~/.bitcoin
wget https://bitcoin.org/bin/bitcoin-core-0.19.1/bitcoin-0.19.1-x86_64-linux-gnu.tar.gz
tar -xf bitcoin-0.19.1-x86_64-linux-gnu.tar.gz
```

```
vi ~/.bitcoin-cash/bitcoin.conf
```

```
whitelist=127.0.0.1
txindex=1
listen=1
server=1
irc=1
upnp=1
# listen on different ports than default testnet
port=20008
rpcport=20009
rpcallowip=127.0.0.1
rpcuser=vimiso
rpcpassword=<password>
datadir=/mnt/bitcoin
```

```
~/.bitcoin/bitcoin-0.19.1/bin/bitcoind -daemon
cd /var/bitcore
npm run node
# or
forever start -c "npm run node" ./
```

## Bitcoin Cash Node:
```
mkdir ~/.bitcoin-cash
cd ~/.bitcoin-cash
wget https://download.bitcoinabc.org/latest/linux/bitcoin-abc-0.21.7-x86_64-linux-gnu.tar.gz
tar -xf bitcoin-abc-0.21.7-x86_64-linux-gnu.tar.gz
```

```
vi ~/.bitcoin-cash/bitcoin.conf
```

```
whitelist=127.0.0.1
txindex=1
listen=1
server=1
irc=1
upnp=1
port=30008
rpcport=30009
rpcallowip=127.0.0.1
rpcuser=vimiso
rpcpassword=<password>
datadir=/mnt/bitcoin_cash
```

```
~/.bitcoin-cash/bitcoin-abc-0.21.7/bin/bitcoind -conf=/root/.bitcoin-cash/bitcoin.conf -daemon
```

## Monitor Storage:
```
du -sh /var/lib/mongodb
du -sh /mnt/bitcoin
du -sh /mnt/bitcoin_cash
```

## TODO
* crontab `~/.bitcoin/bitcoin-0.19.1/bin/bitcoind -daemon`
