
# PowoCoin Windows MN Guide (Single Wallet)
***
## REQUIREMENTS:
 * 1,000 POWO
 * A single 24/7 running computer running Windows.
 * Optonal: A dynamic DNS program like NOIP 
***
IP needs to be the public IP address of your computer. If your IP changes, you might need to use a dynamic IP program like NOIP as stated above.

**(Tutorial will use Windows as main wallet and masternode)**

1) Open the debug console and type the following command:
```
masternode genkey
```
 (This will be the masternode's privkey. Save key in temporary text file , We'll use this later...)

2) Next, enter the following command :
```
getaccountaddress mn1
```
3) Send **1,000 POWO** to the address. (Make sure this is 100% only 1,000; No less, no more.)

4) Next, enter the command into the console:
```
masternode outputs
```
 (This gets the proof of transaction of sending 1,000)

5) Go into the powocoin data directory, by default in Windows it'll be **%Appdata%/powocoin**. 

Find **masternode.conf** Or click on wallet options and click on open masternode configuration file.
and add the following line to it:
```
 <Name of Masternode(Use the name you entered earlier for simplicity)> <IP address>:18882 <The result of Step 1> <Result of Step 4> <The number after the long line in Step 4>
```
Example: 
```
mn1 31.14.135.27:18882 892WPpkqbr7sr6Si4fdsfssjjapuFzAXwETCrpPJubnrmU6aKzh c8f4965ea57a68d0e6dd384324dfd28cfbe0c801015b973e7331db8ce018716999 0
```
Substitute it with your own values and without the "<>"s

6) Open the **powocoin.conf** file (Find it or use the edit the config file in the PowoCoin Core client under "Tools"). Make it look like this:
```
rpcuser=long random username 
rpcpassword=longer random password 
rpcallowip=127.0.0.1 
listen=1 
server=1 
daemon=1 
logtimestamps=1 
maxconnections=256 
masternode=1 
externalip=your unique public ip address 
bind=your unique public ip address 
masternodeaddr=your unique public ip address 
masternodeprivkey=Result of Step 1
```

Make sure to replace rpcuser & rpcpassword with your own.

8) Close and restart your wallet.

9) Open the Debug Console and enter the following command:
```
masternode start-alias <alias>
```
 (Make sure wallet is unlocked)

The output should look something like this:
```

                 {
                       "overall" : "Successfully started 1 masternodes,          failed to start 0, total 1",
                       "detail" : {
                          "status" : {
                             "alias" : "mn1",
                             "result" : "successful"
                         }
                 }

```
11) In the masternode wallet, enter the following command:
```
masternode status
```
You should see something like: 
```
{
    "txhash" : "jse9grj983j4f9j349fj34r",
    "outputidx" : 1,
    "netaddr" : "x.x.x.x:18882",
    "addr" : "P0w3j948f98ejb90ejf498j349fj394jf",
    "status" : 4,
    "message" : "Masternode successfully started"
}
```

**Congratulations! You have successfully created your masternode!**
