# PowoCoin
Shell script to install a [PowoCoin Masternode](https://powocoin.xyz/) on a Linux server running Ubuntu 14.04 or 16.04. Use it on your own risk.

***
## Installation:
```
wget https://raw.githubusercontent.com/powocoin/masternodeguide/master/powo.sh
sudo chmod +x powo.sh && sudo bash powo.sh
```
***

## Desktop wallet setup

After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps for Windows Wallet
1. Open the PowoCoin Desktop Wallet.
2. Go to RECEIVE and create a New Address: **MN1**
3. Send **1000** **POWO** to **MN1**.
4. Wait for 15 confirmations.
5. Go to **Tools -> "Debug console - Console"**
6. Type the following command: **masternode outputs**
7. Go to  ** Tools -> "Open Masternode Configuration File"
8. Add the following entry:

```
Alias Address Privkey TxHash Output_index
```

Your entry should look something similar to this --

```
MN1 0.0.0.0:18882 88ET491cBrrZaKoCKyTdjvZStvM97iB102HS82AJDwFEE1jgP AZ30b9a06a54030315ea8110ab2670808946bc3a3640e1010292909343f876 0

```


* Alias: **MN1**
* Address: **VPS_IP:PORT**
* Privkey: **Masternode Private Key**
* TxHash: **First value from Step 6**
* Output index:  **Second value from Step 6**
9. Save and close the file.
10. Go to **Masternode Tab**. If you tab is not shown, please enable it from: **Settings - Options - Wallet - Show Masternodes Tab**
11. Click **Update status** to see your node. If it is not shown, close the wallet and start it again. Make sure the wallet is unlocked.
12. Open **Debug Console** and type:
```
startmasternode alias false MN1
```
***

## Usage:
```
powocoin-cli getinfo
powocoin-cli mnsync status
powocoin-cli masternode status
```

***
