horuscoin (Rx)
=========

[![Horuscoin](http://i.imgur.com/DWraPO4.png)](http://horuscoin.info)

## What is Horuscoin?
Horuscoin is a cryptocurrency like Bitcoin, although it does not use SHA256 as its proof of work (POW). Taken development cues from Tenebrix, Litecoin, Dogecoin and Megcoin.

### License
Horuscoin is released under the terms of the MIT license. See [COPYING](COPYING)
for more information or see http://opensource.org/licenses/MIT.

### Development and contributions 
Development is ongoing and the development team as well as other volunteers can freely work in their own trees and submit pull requests when features or bug fixes are ready.

## Proof Of Work
Horuscoin uses scrypt as it's proof of work. However, unlike most scrypt variants, horuscoin uses an R value that is not a value of 1. I call this variant scrypt-8-4 or scrypt-n-r. To mine it, you must ensure that your miner is capable of mining scrypt where the `n` is 8 and the `r` parameter is 4. This value was chosen for uniqueness. In this way, even if scrypt-n ASICs came out, they'd be unlikely to support values of R that aren't 1, so this provides ASIC resistance without using experimental or unfamiliar algorithms.

The low values of R and N also means that GPUs should be easier to mine with and it should be practical to build FPGAs for this algorithm. Approximate memory usage can be calculated as `128*R*N`, so the overall memory usage of this algorithm should just be a bit more than 4Kbytes. 

## Wallet
Unlike most altcoin wallets forked from litecoin etc, this has been built by forking from dogecoin-1.7. dogecoin-1.7 is basically a rebase on top of bitcoin 0.9. So, all of the nifty features in bitcoin 0.9 are also in this wallet, including the "core" and cli functionality changes.

### Difficulty
Difficulty is adjusted each block by the digishield algorithm. This algorithm has been proven to be stable by dogecoin and digitalcoin and allows for extremely fast difficulty adjustments, at the cost of slightly more block time fluctuation

### Ports
RPC 10026
P2P 10027

## Build Notes

###Building horuscoind daemon on Linux
dependencies

  sudo apt-get update
  sudo apt-get install build-essential libtool autotools-dev autoconf libssl-dev  libboost-all-dev libdb5.1++-dev git libminiupnpc-dev -y

building (make sure you are on the main directory, not in /src)

    ./autogen.sh
    ./configure --without-gui --without-tests
    make
    sudo make install

### Building horuscoin-qt on Linux (qt4)
dependencies

sudo apt-get update
sudo apt-get install build-essential libtool autotools-dev autoconf libssl-dev  libboost-all-dev libdb5.1++-dev libqt4-dev libprotobuf-dev protobuf-compiler git libqrencode-dev libminiupnpc-dev -y

building (make sure you are on the main directory, not in /src)

    ./autogen.sh
    ./configure --with-gui=qt4 --without-tests
    make USE_UPNP=1 USE_IPV6=1 USE_QRCODE=1
    sudo make install

### Building horuscoin-qt on Linux (qt5)
dependencies
  
  sudo apt-get update
  sudo apt-get install git build-essential libssl-dev libdb5.1++-dev  libboost-all-dev libqrencode-dev libminiupnpc-dev libqt5core5a  autotools-dev autoconf qttools5-dev-tools qttools5-dev  libqt5dbus5  libqt5gui5 libprotobuf-dev protobuf-compiler -y

building (make sure you are on the main directory, not in /src)

    ./autogen.sh
    ./configure --with-gui=qt5 --without-tests
    make USE_UPNP=1 USE_IPV6=1 USE_QRCODE=1
    sudo make install
