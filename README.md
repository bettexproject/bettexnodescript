# Bettex coin
Shell script to install an [Bettex coin masternode](http://bettex.bet/) on a Linux server running Ubuntu 16.04. Use it on your own risk.  
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
6. Type the following command: **masternode outputs**  
7. Go to  **Tools -> "Open Masternode Configuration File"**
8. Add the following entry:
```
Alias Address Privkey TxHash TxIndex
```
* Alias: **MN1**
* Address: **VPS_IP:PORT**
* Privkey: **Masternode Private Key**
* TxHash: **First value from Step 6**
* TxIndex:  **Second value from Step 6**
9. Save and close the file.
10. Go to **Masternode Tab**. If you tab is not shown, please enable it from: **Settings - Options - Wallet - Show Masternodes Tab**
11. Click **Update status** to see your node. If it is not shown, close the wallet and start it again. Make sure the wallet is unlocked.
12. Select your MN and click **Start Alias** to start it.
13. Alternatively, open **Debug Console** and type:
```
masternode start-alias false MN1
```
14. Login to your VPS and check your masternode status by running the following command. If you get **status 4**, it means your masternode is active.
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
