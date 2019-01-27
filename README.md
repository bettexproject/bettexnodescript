# Bettex coin version 3.1.1.1

## Bettex coin masternode setup  

You need to configure the desktop wallet and VPS server. Here are the steps:  
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
* Address: **VPS_IP:31470**
* Privkey: **Value from Step 6**
* TxHash: **First value from Step 7**
* TxIndex:  **Second value from Step 7**
10. Save file and close Desktop Wallet.
11. Prepare your VPS server follow the [instruction](https://github.com/bettexproject/bettexnodescript/blob/master/VPS-Setup-Guide.md)
12. Start shell script to install a Bettex coin masternode on a Linux server running Ubuntu 16.04.
```
wget -N https://raw.githubusercontent.com/bettexproject/bettexnodescript/master/bettexcoin_install.sh
bash bettexcoin_install.sh
```
**USE a privkey value, from step 6 for insert during installation Bettex coin masternode, when you see "Enter your bettex Masternode Private Key.**

13. Type the following command: **watch bettex-cli getinfo** to check and wait till it's synced (look for blocks number and compare with block [explorer](http://explorer.bettex.bet/))
14. Open the Bettex coin Desktop Wallet and wait till it's synced.
15. Go to **Masternode Tab**. If you tab is not shown, please enable it from: **Settings - Options - Wallet - Show Masternodes Tab**
16. Select your MN and click **Start Alias** to start it.
17. Alternatively, open **Debug Console** and type:
```
masternode start-alias false MN1
```
18. Check your masternode status by running the following command, type it into the PUTTY terminal. If you get **status 4**, it means your masternode is active.
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

## Masternode update:
In order to update your Bettex coin Masternode from 3.0.1.1 to 3.1.1.1, please run the following commands:
```
cd /tmp
wget -N https://github.com/bettexproject/bettexnodescript/releases/download/3.1.1.1/bettex_coin-3.1.1.1-linux-daemon.tar.gz
tar xvzf bettex_coin-3.0.1.1-linux-daemon.tar.gz
systemctl stop bettex
mv bettexd bettex-cli /usr/local/bin
systemctl start bettex
rm -r bettex*
```
