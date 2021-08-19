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
