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
