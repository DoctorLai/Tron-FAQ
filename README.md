# Tron Blockchain FAQs

1. What will be the consumption token when users don't have enough bandwidth to make transfer transaction?
> It will burn TRX to pay the fee,  one bandwidth = 140 SUN,   you can calculate based on this. 1TRX = 1000000SUN. You can check this doc for more tech detail https://developers.tron.network/docs/resource-model

2. Is there a config in tron full node which can allow only certain ip's or ip range to query http api?
> This needs to be restricted in the nginx service.

3. We are trying to set up a multisignature with 7 participants, but it isn't allowing us more than 5 users. The documentation says that the maximum is 8 active accesses.
> 8 Active Accesses meaning that you can set up to 8 permission groups. In each group, max num of participants is 5 i.e. so the maximum number of participants in a multisignature is 5.
