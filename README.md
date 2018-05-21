# Masternode-Setup-Script
# Cap Coin
Shell script to install a [CAP Masternode](https://capcoin.net/) on a Linux server running Ubuntu 16.04. Use it on your own risk.
***
## Installation on vps:
* login as root (if you are not root):
```
sudo -s
```
* install wget if its not installed:
```
apt-get install wget
```
* download and run script:
```
wget -q https://raw.githubusercontent.com/Cap-Project/Masternode-Setup-Script/master/cap_install.sh
bash cap_install.sh 
```
***
* during installation it will ask you to add private key that you will generate on local wallet
## Desktop wallet setup
After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps for Windows Wallet
1. Open the CAP Coin Desktop Wallet.
2. Go to RECEIVE and create a New Address: **MN1**
3. Send **10000** **CAP** to **MN1**.
4. Wait for 15 confirmations.
5. Go to **Tools -> "Debug console - Console"**
6. Type the following command: **masternode outputs**
7. Type **masternode genkey** to generate Privkey and paste it on vps during its installation 
8. Go to  ** Tools -> "Open Masternode Configuration File"
9. Add the following entry:
```
Alias Address Privkey TxHash Output_index
```
* Alias: **MN1**
* Address: **VPS_IP:PORT**
* Privkey: **Masternode Private Key**
* TxHash: **First value from Step 6**
* Output index:  **Second value from Step 6**
9. Save and close the file.
10. Go to **Masternode Tab**. If you tab is not shown, please enable it from: **Settings - Options - Wallet - Show Masternodes Tab**
11. Click **Update status** to see your node. If it is not shown, close the wallet and start it again.
10. Click **Start All**
11. If you are not able to see your **Masternode**, try to close and open your desktop wallet.
***
## Usage:
```
cap-cli mnsync status
cap-cli getinfo
cap-cli masternode status
or: 
cap-cli masternode debug
```
Also, if you want to check/start/stop **cap** , run one of the following commands as **root**:
```
systemctl status cap #To check the service is running.
systemctl start cap #To start cap service.
systemctl stop cap #To stop cap service.
systemctl is-enabled cap #To check whether or not the cap service is enabled on boot or not.
```
***
