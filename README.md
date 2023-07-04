### Hi there 👋

<!--
**amberlisez1/amberlisez1** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->git clone https://github.com/AleoHQ/snarkOS.git --depth 1
cd snarkOS
source <(curl -s https://raw.githubusercontent.com/nodejumper-org/cosmos-scripts/master/lava/lava-testnet-1/install.sh)

——————
#create wallet :
———————-


lavad keys add wallet


———————————-
 #SAVE SEED PHRASE 
——————————
#SAVE PRIVATE VALIDATOR KEY :
—————————————-

cat $HOME/.lava/config/priv_validator_key.json

——————————
#wait util the node is synced, should return FALSE
———————————-

#For check synce :
————————————

lavad status 2>&1 | jq .SyncInfo.catching_up

faucet : 
ask in discord, 

——————————
#Check balance :
———————————-

lavad keys show wallet -a

lavad q bank balances $<lavad keys show wallet -a>

______________________
 #create validator :
__________________________


lavad tx staking create-validator \
--amount=90000ulava \
--pubkey=$(lavad tendermint show-validator) \
--moniker="YOUR_VALIDATOR_MONIKER" \
--chain-id=lava-testnet-1 \
--commission-rate=0.1 \
--commission-max-rate=0.2 \
--commission-max-change-rate=0.05 \
--min-self-delegation=1 \
--fees=10000ulava \
--from=wallet \
-y

—————————-
#you can see the validator detail
