# Set up a BitTorrent (BTT) account in Ledger Live
This article describes the BitTorrent (BTT), explains the difference between BTT and Ethereum, and details how to create and manage a Ledger BTT account with a Ledger device.

## What are the main differences between BitTorrent and Ethereum?
Although BTT and Ethereum share a lot of similarities, there are also some important differences between the two projects.

|  | BTT | Ethereum |
|:----:|:----:|:-------:|
| Native coin	| BTT	| ETH | 
| Are tokens supported?| 	Yes, BTT supports BEP20 and BEP721 (NFT) tokens.| 	Yes, Ethereum supports ERC20 tokens and ERC721 (NFT) tokens.| 
| How are transaction fees paid?	| Always in BTT	| Always in ETH| 
| What coins and tokens can I keep in my Ledger account?	| You can keep BTT and BEP20 tokens in a Ledger BitTorrent account	| You can keep ETH and ERC20 tokens in an Ledger Ethereum account| 
| Consensus mechanism	|  Proof-of-authority, which a variant of proof-of-stake but optimized for a small set of stakers (aka validators).	|  Proof-of-work | 
| Can I stake the chain's native token?	|  Yes, you can stake BTT to become a validator but the minimum requirements for solo-staking are high. |  No | 
|  What tool can I use to track my transactions?	| BTTscan | 	Etherscan | 
 
# Creating a BitTorrent account in Ledger Live 
1. Open the Ledger Live app.
2. Connect and unlock your Ledger device.
3. Navigate to the Accounts tab, click the Add account button, select BitTorrent, and click Continue. 
4. Once a BTT account is added, navigate to the Receive tab, select your BTT account and click Continue. Ledger Live and your Ledger device will display your BitTorrent address.
5. Verify this address on your device and click Confirm. This address can be used to deposit BTT or BEP20 tokens.

**Picture**

## Why does my BitTorrent account address look like my Ethereum account address?
You might have noticed that your Ledger Ethereum address and Ledger BTT address look the same.

This is because the Ledger Ethereum and BTT apps use the same cryptographic techniques to generate addresses. This is possible because, as a fork of go-ethereum, BTT shares a lot of “digital DNA” with the Ethereum network.

> A word of caution
> Though your BTT and Ethereum addresses look identical, it’s important to note that they actually exist on two different networks.
> As a result, please avoid sending ETH and ERC20 tokens to your BTT account. Similarly, avoid sending BNB and BEP20 tokens to your Ledger Ethereum account.

## Withdraw crypto to my Ledger BitTorrent account from Binance exchange
In your Binance exchange account, go to the Withdaw Crypto section and select the coin you wish to withdraw.
In the address field, paste your Ledger BTT address, make sure that the BEP20 (BTT) network is selected, and complete the withdrawal.

## BEP20 or BEP2?
There is a difference between the BEP20 and the BEP2 network. 
The BEP2 network refers to Binance Chain, which is a different network from BitTorrent (BTT). You can learn more about these differences in this article.
When withdrawing assets from Binance to your Ledger BTT address, make sure to always select the BEP20 network.
 
## Are all BEP20 tokens supported by the Ledger Live app?
While it's possible to withdraw most crypto assets to your Ledger BTT account in the form of BEP20 tokens, only a subset of all existing BEP20 tokens are currently supported by the Ledger Live app.

From the perspective of Ledger Live there are three types of BEP20 tokens:
- Fully supported BEP20 tokens will show in Ledger Live and display a balance amount (the number of tokens in that balance) and a balance value (how much the balance is worth) denominated in fiat currency (EUR, USD, RMB, etc).
- Partially supported BEP20 tokens will display a balance amount but not a balance value.
- Non-supported BEP20 tokens will not show in Ledger Live at all. They will not be reflected in your total portfolio value and will not create a transaction history in Ledger Live.

## I think I have sent unsupported BEP20 tokens to my Ledger BTT address!
Don't worry, your tokens are safe.
You should be able to see your tokens by pasting your Ledger BTT address into BTTscan then searching the drop-down menu located next to the Token field.
To access your non-supported BEP20 balance, however, you’ll need to use your Ledger device with a third-party app called Metamask.
A detailed tutorial is available here and copied in the next section.
Access my non-supported BEP-20 token balance
This tutorial will show you how to use Metamask to access your Ledger BTT account and manually add your BEP-20 tokens.

1. Close Ledger Live.
2. Download the Firefox browser on your computer.
3. Download and install the Metamask extension on Firefox.
4. Once installed in your browser, create a new Metamask wallet by following these instructions.
5. Next, connect your Metamask wallet to the Smart Chain network using this tutorial.

Plug your Ledger device into your computer and open the BitTorrent app on your Ledger device by navigating to the BitTorrent icon and pressing both buttons simultaneously.
Connect your Ledger device to Metamask using this tutorial in order to find your Ledger BTT account in Metamask.

Add your BEP-20 token to Metamask as a custom token by following this tutorial.
