![V8_DKG_Testnet](https://github.com/user-attachments/assets/e6bd420a-d2d7-4772-94ab-a029e76ab2d6)

# OriginTrail V8 Incentivized Testnet - Guides
OriginTrail - Decentralized Knowledge Graph (DKG), Run an Node V8 Incentivized Testnet - Buidl to Measure, Manage, and Master
## Here We Go...Guys!!!
**`OriginTrail community, driven by an incentivized testnet system. The goal of the V8 incentivized testnet is to ensure security, scalability and usability for all ecosystem participants in a joint test environment, before releasing the new version to the DKG mainnet. An incentivising all eligible contributors with a total incentive pool of 1,000,000 TRAC tokens.`**

*There following four categories of contributions and their incentive pools are indicated below.*
| Incentivized Activity               | Required Technical Level | Reward Budget  |
|-------------------------------------|--------------------------|---------------|
| Staking & UI testing                | Low                      | 50 000 TRAC   |
| Running core nodes                  | Medium                   | 100 000 TRAC  |
| Bug submissions & Code contributions| Medium                   | 100 000 TRAC  |
| Building Paranets (inception program for Builders) | High | 750 000 TRAC  |

*The V8 incentivized testnet will go through a "3 layer launch", each layer introducing new functionality*
- **Core Infrastructure Layer: Run V8 core nodes**
- **Security Layer: V8 staking**
- **AI Layer: V8 edge nodes**

## 1. Preparation for V8 DKG Core Node
**1. Hardware requirements** 

`In order to deploy your V8 DKG node, you will need a Linux server with the minimum recommended hardware`
| Requirement                      | Details                                          |
|-----------------------------------|--------------------------------------------------|
| RAM                               | 4GB                                              |
| CPUs                              | 2 CPUs                                           |
| HDD Space                         | 50GB                                             |
| Supported OS                      | Ubuntu 20.04 LTS, Ubuntu 22.04 LTS               |
| Node Installation Script Purpose  | Install OriginTrail node                         |

**2. Configuration OriginTrail node**

`Setting up node for Base Sepolia Testnet`

- Acquire Base Sepolia ETH (native)
- Acquire Base Sepolia TRAC (token)

`Important note prepare minimum 2 different wallet (address & key)`

- EVM **operational** wallet public key no. 1 (address)
- EVM **operational** wallet private key no. 1 (private key)
- EVM **management** wallet address no. 2 (address)
- EVM **management** wallet private key no. 2 (private key)

`Provide/choose Base Sepolia RPC endpoints`

- Get RPC public https://chainlist.org/chain/84532
- Get RPC own the best like Infura, Alchemy, Thirdweb, Ankr, Publicnode, blastapi, blokpi, dRpc etc....

`Port firewall on the server`

- PORT 8900 (default node API endpoint)
- PORT 9000 (networking port for communication with other nodes)

**In order to acquire TRAC token on Base Sepolia, you should use the Faucet bot on [Discord](https://discord.gg/zuCaVtXFpD) channels** 
```sh
!fundme_v8_base_sepolia_trac (your_operational_wallet_address)
```

## 2. Running V8 DKG Core Node installation
**1. Installer bind (port) firewall configured**
```sh
sudo ufw allow 9999 && sudo ufw allow 8900 && sudo ufw allow 9000 && sudo ufw reload
sudo iptables -A INPUT -p tcp --dport 9999 -j ACCEPT && sudo iptables -A INPUT -p tcp --dport 8900 -j ACCEPT && sudo iptables -A INPUT -p tcp --dport 9000 -j ACCEPT
```

**2. Run OriginTrail V8 DKG Core node installer** 
```sh
cd /root/ && curl -k -o v8_installer.sh https://raw.githubusercontent.com/OriginTrail/ot-node/v8/develop/installer/v8_installer.sh && chmod +x v8_installer.sh
```

**3. Execute the installer by running**
```sh
./v8_installer.sh
```

**4. Verify V8 DKG Core node installation**

- During node installation process stay cool and read on ssh logs, maybe your menu like image below. this OK status

![V8-DKG-Core-Node-installation-OriginTrail-10-24-2024_09_53_AM](https://github.com/user-attachments/assets/a96a3e52-9d8d-45ad-90ae-7163893c3ea2)

- If your installation has been successful, your node will show the `Node is up and running!` log as shown in the example image. **Congratulations, your V8 DKG Core node is up and running!**

![Captureorigin](https://github.com/user-attachments/assets/0b7070f4-6809-43a4-97c2-ca11b19ebf90)

## 3. Checking, Leaderboard and Usefull Commands
**1. Super cmd logs its need**

- Starting your node: `otnode-start` or `systemctl start otnode`
- Stopping the node: `otnode-stop` or `systemctl stop otnode`
- Restarting the node: `otnode-restart`  or `systemctl restart otnode`
- Showing node logs: `otnode-logs`  or `journalctl -u otnode --output cat -fn 100`
- Opening the node config: `otnode-config` or `nano /root/ot-node/.origintrail_noderc`
- Save and backup: `cat /root/ot-node/.origintrail_noderc`

**2. To check leaderboard the Incentivised testnet website**

- The leaderboards are periodically updated based on community contributions, used to determine the amount of TRAC incentives.
- Checking show up **[COMMUNITY LEADERBOARDS](https://dkg-v8-incentivised-testnet.origintrail.io/)**

**3. Important Note** 

During the V8 DKG Core node installation process, installer will deploy otnode-logger.service which will automatically stream the V8 DKG Core node logs to OriginTrail team for support/debug purposes **This service is a hard requirement for the incentivised testnet rewards.**

To disable this service, execute the following commands on the server once the installation is finalized:
```sh
systemctl disable otnode-logger.service
systemctl stop otnode-logger.service
```
