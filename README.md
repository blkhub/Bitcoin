# Bitcoin
Bitcoin node management by BLKHUB

An install manual for Linux system. The provided commands are for a terminal. Binaries are checked against the developer signature.

A fully synced Bitcoin node requires around 300 GB. Make sure your current user directory has this free disk space.

## Install

As a user :
```
VERSION=0.18.0
wget https://bitcoincore.org/bin/bitcoin-core-$VERSION/bitcoin-$VERSION-x86_64-linux-gnu.tar.gz
wget https://bitcoincore.org/bin/bitcoin-core-$VERSION/SHA256SUMS.asc
gpg --recv-keys 01EA5486DE18A882D4C2684590C8019E36C2E964
sha256sum --check SHA256SUMS.asc --ignore-missing
gpg --verify SHA256SUMS.asc && tar -xf bitcoin-$VERSION-x86_64-linux-gnu.tar.gz
```

As root or administrator user :  
```
install -t /usr/local/bin bitcoin-$VERSION/bin/*
```

Test :  
```bitcoind --version```

Configure :  
```
mkdir ~/btcdata
mkdir ~/.bitcoin
```  
Copy the *bitcoin.conf* file provided in the *.bitcoin* directory.
Change in this *bitcoin.conf* file :
* the rpcpassword CHANGEME to a customized password
* the USERNAME to your current user name

```nano ~/.bitcoin/bitcoin.conf```

## Running the bitcoin node

```bitcoind```

Monitor :  
```bitcoin-cli getblockchaininfo```  
or monitor through live logs :  
```tail -f ~/btcdata/debug.log```

Get the latest block height at https://blkhub.net/api/blocks/tip/height

To stop it  
```bitcoin-cli stop```

## For more information

Bitcoin command line arguments  
```bitcoind -?```

Configuration parameters  
https://github.com/bitcoin/bitcoin/blob/master/share/examples/bitcoin.conf

CLI API call list  
https://en.bitcoin.it/wiki/Original_Bitcoin_client/API_calls_list  
https://bitcoin.org/en/developer-reference#rpc-quick-reference

RPC documentation  
https://bitcoincore.org/en/doc/0.18.0/

