![image](https://github.com/Mozgiii9/SideNode/assets/74683169/4344c896-230f-40a9-9028-1c3e2c99e897)

# SideNode

### Creation date: 03.04.2024

### Guide update date: 19.04.2024
#### Project Description:

*Side protocol* is a full-stack omnichannel exchange infrastructure offering specialized infrastructure, tools and applications for DeFi asset exchange. They focus on 4 principles. Scalability, interoperability, decentralization and exchange.

The solution they offer is designed to address CEX - centralization, DEX - problem with integrating new tokens, DEX - limited user experience compared to CEX. DEX is very demanding in terms of scalability and performance, in such cases gas fees are very high, which hits small traders. Here are the main problems Side Protocol wants to solve

**Investment:** 

I can single out Eric Chen, who is the CEO of Injective. After all, the product is very similar to Injective and will probably complement/combine it. As CEO Shane said, there will be a $30M closed tokensale and this amount will attract many people to the project.

**Official Resources:**

- *Website:* [go to](https://side.one/)

- *Link to Medium:* [go](https://medium.com/@SideProtocol)

- *Link to the project's Twitter:* [go to](http://x.com/sideprotocol)

- *Link to the project's Discord:* [go](https://discord.gg/sideprotocol)

### Recommended server specs: 

- *CPU : 4 CORES;*
- *RAM : 8 GB;*
- *Storage : 200GB SSD;*
- *OS : Ubuntu 20.04 / Ubuntu 22.04*

Translated with DeepL.com (free version)

**Before installing the node, you must complete [Galxe quests](https://galxe.com/sideprotocol/campaign/GCraxUn3Fj). This is done in order to get access to the faucet, which gives out test tokens. Test tokens are necessary for correct startup and operation of the node.

**Go to [link](https://galxe.com/sideprotocol/campaign/GCraxUn3Fj), do quests. Bind your Discord, Twitter, Telegram if you have not done it before. After successfully completing the quests you will be able to access the "#testnet-faucet" branch in Discord Side Protocol.**

**Further connect to the server. Do a packet update with the command:**

```
sudo apt update && sudo apt upgrade -y
```

** Install the node using the script:** ```

```
source <(curl -s https://itrocket.net/api/testnet/side/autoinstall/)
```

** Specify wallet name, node name and leave port 26. The node was installed when the logs went. Exit the logs display mode by CTRL+C.**

**Check node synchronization:**

```
sided status 2>&1 | jq .SyncInfo
```

**Unless the value of "catching_up" changes to "false" do not proceed to the next step! **

**When the node has synchronized, you can move on to creating the wallet. Run the commands in sequence, replace "$WALLET" with the name of your wallet that you specified when running the script:**

```
sided keys add $WALLET
```

**Save the wallet address as well as the seed phrase (mnemonic phrase) to a safe place. Proceed to the next steps (Don't forget to replace "$WALLET" with the name of your wallet).
