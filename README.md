# Masternode-Setup-Script
# DMTC coin
Shell script to install a [DMTC Masternode](https://dominantchain.com) on a Linux server running Ubuntu 16.04. Use it on your own risk.
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
wget -q https://github.com/dominantcoin/Masternode-Setup-Script/blob/master/dmtcs_install.sh
bash dmtcs_install.sh 
```
***
* during installation it will ask you to add private key that you will generate on local wallet
## Desktop wallet setup
After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps for Windows Wallet
1. Open the DMTC Desktop Wallet.
2. Go to debug console.
3. Call rpc method allocatefunds masternode <alias> <tier>.(<alias> - masternodes name, can be anything you want; <tier> - The tier you want to run: bronze, silver, gold). Ex. allocatefunds masternode mnName silver.
The output of this command will be the collateral_hash. 
4. Wait for 15 confirmations.
5. Call fundmasternode  <alias> <tier> <result_of_allocate_funds> <masternode_ip>. Ex. fundmasternode "mnName" silver "l3047ad8e934c66d00a6121b32b261764cf5e668e417c4be682835c90c212a11" "1.1.1.1"
The output is: <alias ip:port> <private_key> <collateral_hash> <output_index>
6. Save <private_key> and paste it on vps during its installation.
7. Go to Masternode fonfiguration file masternode.conf. (C:\Users\username\AppData\Roaming\DMTC)
8. Add the following entry(result from step 5):
```
<alias ip:port> <private_key> <collateral_hash> <output_index>
Example: config line": "mnName 1.1.1.1:51472 YR3PbWUjNguD2juUrJj1BDFd24PKyAhUfVtbtCb9LAwodCczG2nB l3047ad8e934c66d00a6121b32b261764cf5e668e417c4be682835c90c212a11 1
```
9. Save and close the file.
10. Go to the masternodes in yo wallet and click **Start masternode**.
11. If you are not able to see your **Masternode**, try to close and open your desktop wallet.
***
## Usage:
```
dmtc-cli mnsync status
dmtc-cli getinfo
dmtc-cli getmasternodestatus (on vps)

