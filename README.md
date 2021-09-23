# Tron Blockchain FAQs

1. What will be the consumption token when users don't have enough bandwidth to make transfer transaction?
> It will burn TRX to pay the fee,  one bandwidth = 140 SUN,   you can calculate based on this. 1TRX = 1000000SUN. You can check this doc for more tech detail https://developers.tron.network/docs/resource-model

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
> https://developers.tron.network/docs/greatvoyage-430bacon#1-add-a-new-field-energy_used-in-transactionextention.

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
> change the maxTimeRatio to 30.0 and restart the node

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
