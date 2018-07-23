# Bettex coin

- **Instruction for prepare [VPS server](https://github.com/bettexproject/bettexnodescript/blob/master/VPS-Setup-Guide.md)**

- **Shell script to install a [Bettex coin masternode](http://bettex.bet/) on a Linux server running Ubuntu 16.04.**
***


## Installation for version 2.0.0.3
```
wget -N https://raw.githubusercontent.com/bettexproject/bettexnodescript/master/bettexcoin_install.sh
bash bettexcoin_install.sh
```
***

## Desktop wallet setup  

After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps:  
1. Open the Bettex coin Desktop Wallet.  
2. Go to RECEIVE and create a New Address: **MN1**  
3. Send **5000** BTXC to **MN1**.  
4. Wait for 15 confirmations.  
5. Go to **Tools -> "Debug Console"**  
6. Type the following command: **masternode genkey**
7. Type the following command: **masternode outputs**
8. Go to  **Tools -> "Open Masternode Configuration File"**
9. Add the following entry:
```
Alias Address Privkey TxHash TxIndex
```
* Alias: **MN1**
* Address: **VPS_IP:PORT**
* Privkey: **Value from Step 6**
* TxHash: **First value from Step 7**
* TxIndex:  **Second value from Step 7**
10. Save and close the file.
11. Go to **Masternode Tab**. If you tab is not shown, please enable it from: **Settings - Options - Wallet - Show Masternodes Tab**
12. Click **Update status** to see your node. If it is not shown, close the wallet and start it again. Make sure the wallet is unlocked.
13. Select your MN and click **Start Alias** to start it.
14. Alternatively, open **Debug Console** and type:
```
masternode start-alias false MN1
```
15. Login to your VPS and check your masternode status by running the following command. If you get **status 4**, it means your masternode is active.
```
bettex-cli masternode status
```
***

## Usage:
```
bettex-cli mnsync status
bettex-cli masternode status  
bettex-cli getinfo
```
Also, if you want to check/start/stop **Bettex**, run one of the following commands as **root**:
```
systemctl status bettex.service #To check if bettex service is running  
systemctl start bettex.service #To start bettex service  
systemctl stop bettex.service #To stop bettex service  
systemctl is-enabled bettex.service #To check if bettex service is enabled on boot  
```  
***
