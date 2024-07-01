![image](https://github.com/Mozgiii9/SideNode/assets/74683169/4344c896-230f-40a9-9028-1c3e2c99e897)

# SideNode

### Guide creation date: 03.04.2024

### Update date: 04/19/2024

### Project Description:

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
- *OS : Ubuntu 20.04 / Ubuntu 22.04.

**Before installing the node, you must complete the [Galxe quests](https://galxe.com/sideprotocol/campaign/GCraxUn3Fj). This is done in order to gain access to the faucet that gives out test tokens. Test tokens are necessary for correct startup and operation of the node.**

**Go to [link](https://galxe.com/sideprotocol/campaign/GCraxUn3Fj), do quests. Bind your Discord, Twitter, Telegram if you have not done it before. After successfully completing the quests you will be able to access the "#testnet-faucet" branch in Discord Side Protocol.**

**Further connect to the server. Do a packet update with the command:**

```
sudo apt update && sudo apt upgrade -y
```

**Install the node using the script:**

```
source <(curl -s https://itrocket.net/api/testnet/side/autoinstall/)
```

**Specify wallet name, node name and leave port 26. The node was installed when the logs went. Exit the logs display mode by CTRL+C.**

**Check node synchronization:**

```
sided status 2>&1 | jq .SyncInfo
```

**Unless the value of "catching_up" changes to "false" do not proceed to the next step!**

**When the node has synchronized, you can move on to creating the wallet. Run the commands in sequence, replace "$WALLET" with the name of your wallet that you specified when running the script:**

```
sided keys add $WALLET
```
**Save the wallet address as well as the seed phrase (mnemonic phrase) to a safe place. Proceed to the next steps (Don't forget to replace "$WALLET" with your wallet name:)**

```
WALLET_ADDRESS=$(sided keys show $WALLET -a)
```

```
VALOPER_ADDRESS=$(sided keys show $WALLET --bech val -a)
```

```
echo "export WALLET_ADDRESS="$WALLET_ADDRESS >> $HOME/.bash_profile
```

```
echo "export VALOPER_ADDRESS="$VALOPER_ADDRESS >> $HOME/.bash_profile
```

```
source $HOME/.bash_profile
```

**Check the node synchronization status again and make sure that catching_up is "false":**

```
sided status 2>&1 | jq .SyncInfo
```

**Go to the faucet branch in Discord (#testnet-faucet) and request tokens by sending a message:**


```
$request side-testnet-3 <ADDRESS_COACHEL>
```


**Replace WALLET_ADDRESS with your wallet address:**

**Use the "Create validator" command to start the validator:**


```
sided tx staking create-validator.
--amount 10000000000uside
--from $WALLET
--commission-rate 0.1.
--commission-max-rate 0.2.
--commission-max-change-rate 0.01.
--min-self-delegation 1.
--pubkey $(sided tendermint show-validator) \-
--moniker "test" \
--identity "" \
--details "I love blockchain." \
--chain-id side-testnet-3 --
--gas auto ---fees 1000uside.
-y
```

**Substitute values:**

*- moniker : Specify the name you gave your node when you ran the Bash script.*

*- details : You can specify your own value or leave the original value.*

After sending the command, enter your wallet password. The server should return the transaction hash (txhash) to you. Go to [explorer](https://testnet.itrocket.net/side/staking) and paste the transaction hash into the search. You will see the address of your validator, as well as the status of its operation. Note that the validator will start after a short time.

### Useful commands

**Check synchronization:**

```
sided status 2>&1 | jq .SyncInfo
```

**Check the logs:**

```
journalctl -fu sided -o cat
```

**View node information:**

```
sided status 2>&1 | jq .NodeInfo
```

**Reboot the service:**
```
sudo systemctl restart sided
```

**Add a new wallet:**

```
sided keys add $WALLET
```

**Restore wallet:**

```
sided keys add $WALLET --recover
```

**View wallet list:**

```
sided keys list
```

**Check wallet balance:**

```
sided q bank balances $(sided keys show $WALLET -a)
```

**Delegate tokens to yourself:**

```
sided tx staking delegate $(sided keys show $WALLET --bech val -a) 1000000uside --from $WALLET --chain-id side-testnet-3 --gas auto --fees 1000uside -y
```

**Delegate tokens to another validator. Replace <TO_VALOPER_ADDRESS> with the address of the validator to whom you want to delegate tokens:**

```
sided tx staking delegate <TO_VALOPER_ADDRESS> 1000000uside --from $WALLET --chain-id side-testnet-3 --gas auto --fees 1000uside -y
```
**Jail information:**

```
sided q slashing signing-info $(sided tendermint show-validator)
```

**Release the validator from jail:**
```
sided tx slashing unjail --from $WALLET --chain-id side-testnet-3 --gas auto --fees 1000uside -y
```

## Be sure to do your own reserch of projects before putting in node. Remember, by doing your own reserch, you learn and grow.
