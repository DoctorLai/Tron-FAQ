# Tron Blockchain FAQs

Tron is based on BIP44  // m/44'/195'/0'/0/0 - You can refer to https://github.com/TronLink/Tronlink-core-android/tree/master/app/src/main/java/com/tronlink/core/common/common/bip39

1. What will be the consumption token when users don't have enough bandwidth to make transfer transaction?
> It will burn TRX to pay the fee,  one bandwidth = 420 SUN (previously was 140 SUN before [Proposal 51](https://tronscan.org/#/proposal/51)),   you can calculate based on this. 1TRX = 1000000SUN. You can check this doc for more tech detail https://developers.tron.network/docs/resource-model

2. Is there a config in tron full node which can allow only certain ip's or ip range to query http api?
> This needs to be restricted in the nginx service.

3. We are trying to set up a multisignature with 7 participants, but it isn't allowing us more than 5 users. The documentation says that the maximum is 8 active accesses.
> 8 Active Accesses meaning that you can set up to 8 permission groups. In each group, max num of participants is 5 i.e. so the maximum number of participants in a multisignature is 5.

4. How to verify Tron Wallet Addresses offline?
```
import base58
base58.b58decode_check("TSSMHYeV2uE9qYH95DqyoCuNCzEL1NvU3S").hex()
```

5. How to get the Fee by Transaction Hash?
> You can use the TronGrid API GetTransactionInfoById to Query the transaction fee, block height by transaction id see: https://developers.tron.network/reference#walletgettransactionbyid

6. How to transfer trc20 token to smart contact?
> See https://developers.tron.network/docs/trc20-contract-interaction 
> Be careful on transfer TRC20 to a contract address. In most case, transfer TRC20 token to a contract means you will lose those tokens becase no one can withdraw it.

7. Spam/unknown Tokens
> Just receiving a token into your wallet does not have any harm to your wallet, but using that token on any platform is solely your responsibility, don't do anything with an unknown token.
> Tron network is a decentralised system anyone in the world can create a token with any name and distribute it over tron network to any wallets, there is no permission is needed for incoming transfer, also tronlink is a decentralised wallet no permission is needed for incoming transfer, if someone sends this token to your wallet most probably it will visible.
> Verified or legitimate token has a blue tick ✔️ mark.
> You can hide the visibility of the token by using the "+" option on the right side of the tronlink home page.
> Also, you can see more information for that token by clicking the information button on the top right corner of that token's transfer history page.
> If by mistake you have tried to swap fake tokens on any scam website then please don't use that wallet again immediately transfer your wallet funds to a new wallet.

8. How do I retrieve transaction note from the get_tranaction() function?
> Please refer to https://developers.tron.network/docs/make-transaction-locally and after you get the transaction by id, please parse the data field to get the note.

9. If I want to become an SR(c), would I have to deploy a fullnode?
> Yes, because if your node goes up the list, it must be able to create blocks and confirm transactions.

10. I have created a token on your blockchain network but it's price is not yet determined. What should I do for the price to appear in my wallet?
> It needs to be listed on PoloniDex or another exchange & tracked by CoinGecko. If you need the price to show, then exchange listing is needed, again if not on PoloniDEX, then the exchange you list it on must be tracked by CoinGecko and you must apply for your token to be tracked by CoinGecko.

11. Can I use  Ethereum private key to generate a Tron address?
> Yes.

12. How to figure out gas costs when deploying smart contracts on my tronbox setup? I can then use that account to query "http://127.0.0.1:9090/wallet/getcontract?value=xxx" and get JSON that describes the methods available in the contract, but I see not cost for the creation or running of the contract when I interact with it.
> You need the transaction hash to query it and see how much it has used. Besides the more functions and internal transactions a contract has the more processing power it uses on the node hence the fee going up.

13. Can I use Tron from my Shasta testnet to invest into something?
> TRX on shasta can only work on shasta, mainly for Developers, no other value.

14. What is the cost to deploy a new contract?
> Deploy a new contract is not free, for a simple TRC20 Token contract, it will cost around 80 TRX to complete it.  it will cost more if your contract is more complex.

15. I want to deploy a contract in tron blockchain. Can I use the tron energy for it instead of paying TRX?
> Trx are burned only if you don't have enough energy or bandwidth.

16. What is the justswap contract address on shasta?
> Justswap does not have a testnet version.

17. Is there a way to accept a particular token as payment in a contract?  Ethereum has a ERC-1363 Payable Token - is there something comparable for TRON?
> I would suggest you try on Tron testnet, it should be supported from TVM level.

18. When a token is made Do users always have to pay a fee for the transfer? Is there a solution for transferring tokens free of charge?
> You can freeze TRX to get ressources for free transfer.

19. How do we use TRON-PRO-API-KEY in the website?
> when you send API make sure you include the key in the headers for example 
```
    headers: {
        Accept: 'application/json', 
        'Content-Type': 'application/json',
        'TRON-PRO-API-KEY': AppKey,
    },
```

20. How can i use api to create wallet address for my app users？
> It is suggested that you generate address offline instead of using any API.

21. Is it possible to get jst token on Shasta test net? I wanted to test the justlink vrf but I using shasta instead of nile?
> users cannot join shasta, but you can join Nile and get JST token at: https://nileex.io/join/getJoinPage

22. When i create an adress, next how i make it to online chain？
> Activate that account, for example transfer 1 TRX to that account.

23. Will it be any case, energy of an wallet can be negative value?
> energy = obtain-consumed, and let's say now you have 200k obtianed by freezing from two different account, one 150k, one 50k, and you consumed 100k, but the one freezing 150k do a unfreez, and this time, the consumed is more than obtained, so an energy can be negative.
> I would say it is normal if your energy is negative after unfreeze, and all your consumed energy will be recovered to 0 in 24 hours.

24. Even you are not producing block, you still need to keep running the server and all the txn consume storage, right ?
> Yes it consumes storage because you are keeping a copy of the blockchain, also if your node is voted up and activates as a top SR it has to be in sync or may be kicked back down or even voted out of the SRs.

25. Although TRON is burning on a daily basis, why is the supply increasing?
> TRON burns and produces at the same time. If the production rate is high compared to burning, of course, the percentage of currencies will rise and vice versa.

26. What is the formula for energy regeneration?
> regeneration is 24 hours, it may be per second. I do not have the exact formula but is something like ((ENERGY_Assigned / 86400 seconds) * (timestamp - last_consume_timestamp) + ENERGY_left_calculation_formula_at_last_consume_timestamp[This is a separate formula]) and maybe a couple more things in it to calculate it precisely.
> So the formula is: total assigned energy/86400 (1 day in seconds) per second. Using the entire energy takes 24 hours to come back, if you have 10,000 energy, and use 5,000 energy, it will come back in 12 hours, but if you have 20,000 energy and use up 5,000 energy, it'll be back in 6 hours.

27. Fullnode sync is very slow.
> https://developers.tron.network/docs/faq#8-how-to-solve-the-problem-of-slow-node-block-synchronization-or-stop-synchronization

28. How to make a Stablecoin on tron network?
> Stablecoin can be issued on any public chain. This is the USDT coin on tron network. https://tronscan.org/#/token20/TR7NHqjeKQxGTCi8q8ZY4pL8otSzgjLj6t

29. How to Integrate TRC20 token in backend for Deposit and Withdraw Operations?
> Check this guide: https://developers.tron.network/docs/trc20-contract-interaction

30. How to Test JustSwap in TestNet?
> Currently, there is no testnet for JustSwap, if you are familiar with smart contract realted development,  it is very easy to integrate with justswap if you follow the developer document on justswap homepage.

31. How can I make withdrawal from my Tron Wallet?
> try tronlink.  https://www.tronlink.org/

32. I get "Out of Energy" error with 7656 Energy on Tronlink wallet.
> That amount of energy is very low for a TRC20 contract operation. A simple transaction is about 20000 energy. You need to have some TRX to burn or stake.

33. Are there any guides how to make TRC20 transfers via full node api?
> check this guide: https://developers.tron.network/docs/trc20-contract-interaction you can also see the example with curl or you can find more examples here https://developers.tron.network/reference#trigger-smart-contract
> Using this https://developers.tron.network/docs/parameter-and-return-value-encoding-and-decoding to decode and uncode.

34. How to fetch list of transaction list by wallet address?
> https://developers.tron.network/reference#transaction-information-by-account-address

35. How can i watch transactions of tron blockchain by socket?
> You can do this by http api or gRPC api.

36. The Energy consumption of Nile and Shasta TestNet?
> The Nile is 3 times as the mainnet and the Shasta is the same as the mainnet.

37. When will be possible to count estimated energy before execute transaction?
- https://developers.tron.network/docs/greatvoyage-430bacon#1-add-a-new-field-energy_used-in-transactionextention.
- https://developers.tron.network/docs/faq#5-how-to-calculate-the-bandwidth-and-energy-consumed-when-calling-the-contract

38. Can I override unconfirmed transations in tron?
> No

39. I have successfully launched my token on mainnet. How would i get it listed on tronlink?
> It will sycn to tronlink around 2 hours after you finished token record on tronscan.

40. why need to build own fullnode?
> Trongrid has Ratio limit, If you have a large business volume and frequent API visits, it will exceed the maximum visits of Trongrid. At this time, the best choice is to build your own FullNode.

41. How can i start private network on local in my system?
> https://developers.tron.network/docs/tron-private-chain

42. How to run a event server?
> Try Tron’s Developer hub, you can find answer there, https://developers.tron.network/docs/event-plugin-deployment-mongodb

43. Do we have to use a black hole to burn tokens in Tron network? If yes, what is the official black hole address of TRC20? What is the fee and on what basis is it calculated?
> https://developers.tron.network/docs/faq#3-what-is-the-destruction-address-of-tron and https://developers.tron.network/docs/resource-model

44. Startup will still be stuck after the upgrade (v4.3).
> change the maxTimeRatio to above 20.0 e.g. 30.0 and restart the node.

45. how to define the fee_limit for TRC20 token?
> You can set the feelimit when you create a contract transaction, refer to the documentation https://developers.tron.network/reference#trigger-smart-contract

46. Let’s said I’m going to trigger smart contract for transfer. Does it mean it wil out of energy if it exceed the fee limit that I set? 
> There are more detailed instructions here, you can read the following document https://developers.tron.network/docs/resource-model#2-how-to-set-fee-limit-caller-must-read

47. the API URL of the tron test browser
> check this.   https://shastapi.tronscan.org/api/vote/witness  https://nileapi.tronscan.org/api/vote/witness

48. How much is the Fee to activate account on Main net?
> 1 TRX

49. If i want to grab the latest tron/usdt price how would i go about doing so? I cannot find anywhere the API offers 😕
> You can use my API (Fair use policy)  
> $ curl -s --data "TRON USDT" https://price.justyy.workers.dev/query
> {"query":["TRON USDT"],"time":"2021-09-21T01:11:16.186Z","result":["1 tron = 0.08916068705152887 usdt"]}
> You can also try the following:
> 1. https://winklink.org/
> 2. https://coinmarketcap.com/
> 3. https://www.coingecko.com/en

50. I created a private Tron chain. It comes with TronGrid. Do I have to pay for Trongrid if my calls exceed 100K daily?
> no, you dont need to pay on your own private chain.

51. Is there a way to get information about user's balance using only the address of wallet?
> you can do this via tronweb or trongrid api

52. Is there any IDE like Remix to develop contract?
> You can try http://www.tronide.io/

53. I am looking for someone to help me develop a TRC-20 stablecoin.
> You can refer to the USDT on TRC-20 https://tronscan.org/#/token20/TR7NHqjeKQxGTCi8q8ZY4pL8otSzgjLj6t/code

54. How can i valid one address is valid?
> the account is a public key created from private key, you can verify it according to this: https://developers.tron.network/docs/account

55. I already set up fullnode and solidity node, so my question is how can i listen to new transaction received by given address ?
> Loop through the blocks or use event-plugin：https://developers.tron.network/docs/event-subscribe

56. Is there a way to pool energy or bandwith across multiple wallets? As in sharing the resources between multiple wallets.
> No

57. How to find out if a Tron Address is active or not?
> It will return account detai via getaccount API if account is activated.

58. What is the minimum sending amount of TRX to activate the address? 
> Transfer >0.1 TRX to activate the address.
> At least 1 TRX must be burned to activate the account. If there is not enough frozen bandwidth, an additional 0.1 TRX will be burned. In this case, it will cost 1.1 TRX to complete the creation of a new account; if there is enough frozen bandwidth, 1 TRX must be burned to complete creating the new account.

59. Where  we can find the token icon file? (manual search via google ... or there is some better way? )
> All token icon can be found on tronscan.

60. is there any email list subscription to be notified about important update on full nodes? ( when we need to update our full nodes If happening any critical update)
> You will see Update notification in this channel if there is a new version. or you can subscribe the release from here: https://github.com/tronprotocol/java-tron/releases

61. Is it more profitable to freeze balance than pay fees in TRX?
> Depends on your balance and daily transaction count. very much transactions, 100+. If you have more balance then freeze, your freezing resource gets filled every day. If you got 100k bandwidth, and used all of it, it will be filled to 100k the next day. You'll get about 1.5 bandwidth for each TRX stacked

62. Does any one know an efficient method to listen for triggered smart contract event on the tron network. Tried using tronweb's watch method but it doesn't pick all transactions.
> one option is to pull all events from trongrid API:  https://developers.tron.network/reference#events-by-transaction-id

63. Sample JS code to transfer TRC20 token?
```javascript
export const triggerSmartContract = async (req, res) => {

    const trc20ContractAddress   = "TQxmdUhvJt59GJ7m9VWQe99gZ26HJikSug";//contract address
    var address         = "TZ7C72E4AZPjEiswtWfb35PVhm28VmWnJC";

    try {

        let contract = await tronWeb.contract().at(trc20ContractAddress);
        //Use send to execute a non-pure or modify smart contract method on a given smart contract that modify or change values on the blockchain.
        // These methods consume resources(bandwidth and energy) to perform as the changes need to be broadcasted out to the network.
        let result = await contract.transfer(address, 100).send({
            feeLimit: 1000000
        }).then(output => {console.log('- Output:', output, '\n')});
        
        console.log('result: ', result);

    } catch(error) {

        console.error("trigger smart contract error", error)
    }
}
```

64. I create a transaction for TRX in Tron network successfully. How can I send USDT or any other token in Tron with the Trongrid API?
> https://developers.tron.network/docs/trc20-contract-interaction#transfer

65. How to fix this "contract validate error : account does not exist"?
> Probably the account is not activated, transfer >0.1 TRX to that account will activate the new accout.
> At least 1 TRX must be burned to activate the account. If there is not enough frozen bandwidth, an additional 0.1 TRX will be burned. In this case, it will cost 1.1 TRX to complete the creation of a new account; if there is enough frozen bandwidth, 1 TRX must be burned to complete creating the new account.

66. How to transfer TRC10/TRC20 token and I want to see the fee when transfering?
> - sendToken is for TRC10 transfer: https://developers.tron.network/reference#sendtoken
> - TRC20 token transfer is done via triggersmartcontract: https://developers.tron.network/docs/trc20-contract-interaction#transfer
> - see the fee: https://developers.tron.network/docs/faq#5-how-to-calculate-the-bandwidth-and-energy-consumed-when-calling-the-contract 

67. Is it possible the wallet account and account being approved both need activated?
> the account must be activated if you want to start transction with that account.

68. How to improve the sync speed or solve the sync stop problems of java-tron?
> 1. a better machine such as 16 CORES + 32GB RAM, 500 GB SSD
> 2. make sure single physical CPU has 16 cores or above: the following needs to be bigger or equal to 16.
```
$cat /proc/cpuinfo | grep -e "cpu cores"  -e "siblings" | sort | uniq
cpu cores   : 8
siblings    : 16
```
> 3. Change the max time toerlance to 20.0 or above:
```
vm = {
  supportConstant = false
  minTimeRatio = 0.0
  maxTimeRatio = 20.0
  saveInternalTx = false
}
```
> 4. Improve the start-up by adding XX:+UseConcMarkSweepGC
> $java -XX:+UseConcMarkSweepGC -jar Fullnode.jar -c config.conf

69. Is it harmful or advantageous to use a public node instead of setting up my own node?
> depends on your own requirement, public nodes are mainly for seed nodes, it cannot support very limited requests, too many requests may cause the node stop working. If you have a large number of requests, it is best to use your own Node, because your own Node only serves you and is more secure.

70. How to make a TRC20 coin?
> 1. first you have to write the smart contract for your coin.
> 2. deploy your token's smart contract.
> 3. from this link you can record your trx20 token: https://tronscan.org/#/tokens/create/Type

71. I got this number from api. amount_str = "2535672" how can i understand how much is this? how can i convert it to exact amount?🤔
> 2.5 TRX

72. What are internal transactions?
> please refer to this doc: https://developers.tron.network/docs/vm-introduction#internal-transactions

73. Can I generate TRC20 address in Mainnet? I need generate TRC20 adrress while become a member for all user.
> You can use local nodes to generate addresses or generate addresses offline，pls check this document https://github.com/tronprotocol/java-tron/blob/develop/framework/src/main/java/org/tron/core/services/http/GenerateAddressServlet.java#L23

74. Is there a method to get the current chain id on TronWeb instance?
> https://developers.tron.network/reference#eth_chainid

75. Can anyone help me learn to add liquidity to my TRC 20 token?
> https://justswap.zendesk.com/hc/en-us/articles/360047260732-How-to-add-liquidity-

76. We are developing an exchange software that use TronGrid to manage transactions, Is this the best way? Or run the Full node?
> depends on the request volume, if the trongrid free volume cannot meet your requirement , you need to set up your own node.

77. How to get "REST API endpoint providing circulating supply value" for certain token using http? Token: https://tronscan.org/#/token20/TThrzAzRj2Pw4CQjqo1dk2zGyifPhuNHRu/ I need to get something like this: http://explorer.litecoin.net/chain/Litecoin/q/totalbc (only pure number "9,964,245,481.605456077196663259" using http)
> You can use this: https://apilist.tronscan.org/api/token_trc20?contract=TThrzAzRj2Pw4CQjqo1dk2zGyifPhuNHRu&showAll=1 This is closest you’ll get probably.

78. How much energy can I get by staking 1000 TRX?
> With 1000 TRX, you can get estimated gain 1000 TRON Power and 25970.664 Energy. You can see this at tronscan.io when you staking the TRX.
> 
> ![image](https://user-images.githubusercontent.com/1764434/138568650-4164a06c-bb39-43f6-84b0-51604de1f920.png)

79. Is there an API to get the unit price of energy?
> https://developers.tron.network/reference#getchainparameters-1 you can get the "getEnergyFee" from this api.

80. Where can i find documentation for setting up event server in vps? Right now, i am trying to "deploy tron event subscription plugin" but i am not sure if i am doing something wrong or documentation is broken. I need this to fetch user's NFT balance and some other events. 
> doc to deploy event plugin : https://developers.tron.network/docs/event-subscribe

81. I cannot get any information of a tron wallet on tronscan.org or using trongrid API
> only activated account can return data. non-activated account will return empty. Transfer > 0.1 TRX to that account will activate that account.

82. Getting 503 Errors: Failed to load resource: the server responded with a status of 503 (). This happen 100% of the times on the main net, on Nile everything works as expected.
> IP or API-KEY access exceeds frequency limit, max 15 times/s

83. Is possible to send  energy to address in tron network?
> You cannot send energy to other address, however you can set the receive address when you freezing TRX for energy.

84. Energy unit price doubles?
> https://tronscan.org/#/proposal/71

85. How can I get a api of Energy By Burning TRX?
> https://developers.tron.network/docs/greatvoyage-430bacon#1-add-a-new-field-energy_used-in-transactionextention

86. How can we forecast  how much SUN  = 1 Energy?
> https://api.trongrid.io/wallet/getaccountresource?address=TEi9FxmwRAGncvMLEdgKpFsQrGBgAZywC7&visible=true  you can see the total energy and total freezing TRX for energy , Based on this, you can roughly estimate how much energy the new freezing TRX can obtain: 
```
TotalEnergyLimit /(totalEnergyWeight + newFreezeTRX) * newFreezeTRX. 
Burn TRX = Energy * Energy Unit price / 10^6
```

87. TRX and SUN relationship?
> 1 TRX = 1000000 sun, e.g. 280 sun means 0.00028 TRX.

88. I got  this error {"result":{"code":"OTHER_ERROR","message":"636c617373206f72672e74726f6e2e636f72652e73657276696365732e687474702e4a736f6e466f726d6174245061727365457863657074696f6e203a20343a32363a20494e56414c49442068657820537472696e67"}} - How can I decode the message?
> It is hex, you can do this:
```
"".join(list(map(chr, list(bytes.fromhex(message)))))
```
> It is also at tronide.io
> 
> ![image](https://user-images.githubusercontent.com/1764434/140302028-ed2b4dda-cb8c-4425-888a-6ceb9be5ff66.png)

88. What are the Tron Python SDK?
> https://pypi.org/project/tron/ and https://pypi.org/project/tronapi/
> You can use one of these SDK
```
pip3 install tron
pip3 install tronapi
```

89. How to generate address offline?
> Some Demo code of Generate address offline(means generate address locally): 
- java： https://github.com/tronprotocol/java-tron/blob/develop/framework/src/main/java/org/tron/core/services/http/GenerateAddressServlet.java#L23
- Python: https://github.com/andelf/tronpy/blob/8beacd905ecd8cb151498748e2d446004c0b53ff/tronpy/tron.py#L458
- Java-script: https://github.com/tronprotocol/tronweb/blob/34cb9c5ac0f5167b0660e663583d973949868e04/src/index.js#L393
- C sharp: https://github.com/farukterzioglu/TronSharp/blob/master/TronSharp.Tests/Singature/SignWithPrivateKey.cs
> Offline sign: 
- Java: https://cn.developers.tron.network/docs/%E6%9C%AC%E5%9C%B0%E6%9E%84%E5%BB%BA%E4%BA%A4%E6%98%93
- Python: https://github.com/andelf/tronpy/blob/8beacd905ecd8cb151498748e2d446004c0b53ff/tronpy/tron.py#L130
- Java-script: https://github.com/tronprotocol/tronweb/blob/34cb9c5ac0f5167b0660e663583d973949868e04/src/lib/trx.js#L650

90. How do I calculate contract call bandwidth and energy values? Are there any relevant code samples?
> https://developers.tron.network/docs/faq#5-how-to-calculate-the-bandwidth-and-energy-consumed-when-calling-the-contract

91. How can I check balance of USDT trc20 token?
```js
const trc20ContractAddress = "TR7NHqjeKQxGTCi8q8ZY4pL8otSzgjLj6t"； //mainnet USDT contract
let contract = await tronWeb.contract().at(trc20ContractAddress);

//contract.[eventname].watch(callback) enventname is the name of the event of the contract
await contract && contract.Transfer().watch((err, event) => {
  if(err)
    return console.error('Error with "Message" event:', err);
 
  console.group('New event received');
  console.log('- Contract Address:', event.contract);
  console.log('- Event Name:', event.name);
  console.log('- Transaction:', event.transaction);
  console.log('- Block number:', event.block);
  console.log('- Result:', event.result, '\n');
  console.groupEnd();
});
```

92. How can ı create seed phrase from keystore?
> Tron is based on BIP44, // m/44'/195'/0'/0/0

93. What is an offline mode? And can I create a account with PHP?
> offline mode  ≈  create it via SDK. We can create address with library instead of communicating with the node.

94. Does metamask support TRON?
> No - use tronlink instead.

95. Does any one know about ByteString convert to readable string in trident-java get transaction by id, and the return value such like below:
```
value: "\n\025A\210$S\221\364\304\224lU7\026\344\207)\377\304\3132\375\313\022\025A\246\024\370\003\266\375x\t\206\244,x\354\234\177w\346\336\321<\"D\251\005\234\273\000\000\000\000\000\000\000\000\000\000\000\000\204i\336\236,y\231(^\234I\004\241\300\210\220\273\232\334b\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000\017B@"
```
> Check: https://github.com/tronprotocol/wallet-cli/blob/f8c542f1c0fa45e882640ffadf988118cea7cd7a/src/main/java/org/tron/common/utils/Utils.java#L350 

96. Validate signature error: xxxx is signed by xxxx but it is not contained of permission
> You are using wrong private key. The private key must the priavate key of the owner_address.

97. Does tronweb have the function of identifying and observing the wallet?
> This feature is not currently available on tronweb.

98. Converting Hex to ASCII:
```bash
curl -s -X POST --data "524556455254206f70636f6465206578656375746564" "https://str.justyy.workers.dev/hex"
```
or
```bash
echo "524556455254206f70636f6465206578656375746564" | xxd -ps -r
```

99. Decimals of TRX
> 6

100. How to get address using trident-java?
```java
KeyPair keyPair = new KeyPair("your private key");
keyPair.toBase58CheckAddress();
```

101. How to Transfer TRC-20 using Python?
> https://github.com/andelf/tronpy

102. How can I get Free Shasta?
> https://twitter.com/TronTest2

103. when running a litenode that was started from a database snapshot, is there a way to compress the current database when it gets to big for the litenode to store?
> No

104. If i want to listen trc20 transaction for certain address, should i develop a full node?
> https://developers.tron.network/v3.7/docs/tronweb-trx-functions  
> Get all transaction detail by block with `tronWeb.trx.getBlock(12345);` thus no need for a full node.

105. How should I monitor real-time transfer events on the chain?
> two options: 
- one is using event plugin:   https://developers.tron.network/docs/event-subscribe
- one is scanning the block: please refer to the doc: https://developers.tron.network/docs/how-to-determine-address-recharge

106. owner_address Why is this parameter mandatory? We can activate the newly created account later.
> activate account has cost, you have the specify the owner account to pay the cost.

107. How to get user's authority so that can check his balance with wallet address?
> you don't need user authority to check balance. Just call the BalanceOf(address) funtion of the token contract, or use the Tronlink api for TRX balance

108. How to check confirmation of the transaction?
> https://developers.tron.network/docs/tron-protocol-transaction#transaction-confirmation

109. How much fee for issuing a TRC10 token?
> https://developers.tron.network/docs/trc10

110. Is there a way to predict block hash values?
> No way

111. I have a tron address but lost the private key, is there anyway to regain (recover) this?
> No

112. Does TRON have any documentation that encapsulates the API? Interfaces can be called directly, like API
> https://developers.tron.network/reference/select-network

113. How to listen to wallet address deposit?
You can use:
- event plugin： https://developers.tron.network/docs/event-subscribe 
- scanning blocks： https://developers.tron.network/docs/faq#14how-to-judge-the-recharge-and-withdraw-funds-by-scanning-the-block

114. How to transfer TRX to another account using Javascript (tronweb)?
> https://developers.tron.network/docs/trx-transfer

115. Can i pay fees in tron and not freeze my tron?
> Yes

116. I want to create a raw transaction (without signing it) and get its hash in hex format. The official TRON API normally returns a JSON for creating transactions. Does anybody here know how to do this?
> https://developers.tron.network/docs/make-transaction-locally.

117. How to send TRC20 using PHP?
> https://github.com/iexbase/tron-api

118. What is SUN?
> 1 SUN = 0.000001 TRX

119. How to Convert TRX to SUN using tronWeb?
> https://developers.tron.network/reference/tosun

120. is it possible to hide transaction for any particular wallet?
> No way, block chain is a fully transparent platform. all transactions are public.

121. can we block any particular wallet, if someone steal crypto & is it possible to block those users so they can not able to access to those funds?
> No. Blockchain is decentralised. As long as you have private keys, you have accessed to the funds in your wallet. However, there are several work arounds from centralized org.
> - USDT contract do support account block if user report it is a scam.
> - Exchanges usually also support account block if the money goes to the exchange.
> - CEX can block because they internally use Wallet Mechanism

122. curl -X GET  http://127.0.0.1:8090/wallet/getnowblock curl: (7) Failed connect to 127.0.0.1:8090; Connection refused
> - check whether your node is still running.
> - Check your server configuration and see whether 8090 is enabled.

123. How to deploy my full node?
> https://developers.tron.network/docs/fullnode

124. I by mistake deposited USDT on my tronlink wallet usdt contract address. Is there a way to retreive/recover the coins?
> https://cs.tether.to/

125. How do I get the current USDT price？
> You can use the free API: https://price.justyy.workers.dev/

126. How to Query TRX balance?
> https://developers.tron.network/docs/query-trx-balance

127. Does tronscan have api to get chain id or net id like ethereum?
> TRON has no concept of chainid.

128. How long does it take for a successfully broadcasted transaction that did not appear on the blockchain to expire?
> https://developers.tron.network/docs/tron-protocol-transaction#transaction-confirmation 
> The mechanism of TRON's block validation is that a block is validated after this block is produced and 19 different SRs produce subsequent blocks based on this block.

129. Can the wallet address be customized?
> No

130. Is it possible to get a list all holder addresses from a defined trc20 token via API?
> https://developers.tron.network/reference/get-trc20-token-holder-balances

131. How can I add tron network on coinbase wallet? 
> https://help.coinbase.com/en/wallet/getting-started/what-types-of-crypto-does-wallet-support Please refer to the documentation, or contact Coinbase wallet customer service with your questions.

132. Which API of Trongrid queries the balance of USDT?
> https://developers.tron.network/reference/get-account-info-by-address

133. Does Tron have a json rpc api like Ethereum?
> https://developers.tron.network/reference/json-rpc-api-overview

134. How much bandwidth/energy for freezing the TRX?
> https://tronstation.io/

135. How to freeze trx for account that i created using tronweb?
> https://developers.tron.network/reference/freezebalance

136. Is there a way to upload a custom abi on Tronscan for a contract already deployed?
> No

137. How to transfer or send USDT from one wallet to another wallet using TronWeb?
> https://helloacm.com/how-to-send-transfer-usdt-on-tron-blockchain-using-tronweb/

138. How to transfer or send TRX from one wallet to another wallet using TronWeb?
> https://helloacm.com/javascript-function-to-send-trx-on-tron-blockchain-based-on-tronweb/

139. What are the USDT Contract Addresses (TRC-20)?
- Main Net: TR7NHqjeKQxGTCi8q8ZY4pL8otSzgjLj6t
- Shasta TestNet: TG3XXyExBkPp9nzdajDZsozEu4BkaSJozs
- Nile TestNet: TXYZopYRdj2D9XRtbG411XZZ3kM5VkAeBf

140. How can I validate a Tron Wallet Address  using Tronweb?
> You can use `TronWeb.isAddress` method to validate an address.

141. What is the difference between Energy and Bandwidth in Tron?
> https://tronscanorg.zendesk.com/hc/en-us/articles/360041445672-What-are-Bandwidth-and-Energy

142. Is there a beginner's guide to deploy a smart contract on tron?
> https://developers.tron.network/docs/smart-contracts-introduction

143. How to Verify a Signature of a Signed Hex Message?
> https://developers.tron.network/reference/verifymessage

144. How to Convert Base58 to Hex Tron TRC20?
> https://tronscan.io/#/tools/tron-convert-tool

145. What is the "visible" parameter? POST /wallet/createtransaction
> It is the address format, visible true for base58 and false for hex format.

146. How much storage space do I have to prepare to run a node?
> https://tronprotocol.github.io/documentation-en/architecture/network/

147. If I generate a HD address this way:

```js
const node = ethers.utils.HDNode.fromMnemonic(process.env.MNEMONIC)
const dp = `m/44'/195'/0'/0'`;
const i = 1;
const wallet = node.derivePath(`${dp}/${i}`)
console.log(wallet.address)
it'll start with 0x --> "0xfdsfds.........43
```

148. How to convert it into a valid Tron address now? The one that starts with "41" or "T".
> https://developers.tron.network/reference/frommnemonic

149. Is there any limitation on calling tron public node?
> https://developers.tron.network/reference/rate-limits#what-should-i-do-if-im-rate-limited

150. I am trying to sent all trx balance to another account using tronweb. First I get the current balance and then I pass this value to tronWeb.trx.sendTransaction. The problem is that I receive "insufficient balance"
It can happen for 2 things:
- you don't have enough bandwidth and the system is trying to burn some trx but it can't  because you are trying to send all.
- the account balance api call is cached the balance and it's not giving you the real number you have.

151. How do I find the increase factor and max factor of a contract?
> Call /wallet/getchainparameters to get the values of threshold, increase_factor, and max_factor on the Nile testnet.  check this document: https://coredevs.medium.com/dynamic-energy-model-deployed-and-opened-on-nile-testnet-59b81cb748f5

152. Could the 'TRANSACTION_EXPIRATION_ERROR' error be caused by not being synchronized? This is an error that occurs when using 'sendcoin' in wallet-cli.
> The error TRANSACTION_EXPIRATION_ERROR is caused by the expiration of the transaction. Currently, the transaction validity period created by the node is 1 minute, and the transaction needs to be broadcast within 1 minute. If it expires, the transaction needs to be recreated

153. I want to create an account and transfer tokens after setting up a full node, but block synchronization takes too long. I wonder if it's normal.
> You can use the latest backup database and the synchronization time will be greatly reduced:https://developers.tron.network/docs/main-net-database-snapshots
