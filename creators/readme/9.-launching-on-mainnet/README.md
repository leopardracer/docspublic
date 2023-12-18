# 9. Launching on mainnet

You have thoroughly tested your contracts on testnet. The images and metadata reside on IPFS. You only need to change some values in `config.js` before launching on mainnet.

* Change the RPC endpoint to the mainnet endpoint `rpcEndpoint: 'https://rpc.stargaze-apis.com/'`.
* Change `startTime` of the launch. i.e: 3pm EST on Friday, March 25, 2022, and format it to UTC: `startTime: '2022-03-25T19:00:00.000Z'`.
* Change account to your mainnet account.
* Comment out (add `//` before all the contract codes)`CONTRACT CODE IDs: Castor Testnet`
* uncomment (remove `//` before the contract codes sg721CodeId, minterCodeId, whitelistCodeId) `CONTRACT CODE IDs: Mainnet`

Now you're ready to deploy.

{% hint style="info" %}
Whitelist `start_time` and `end_time` should come before Public Mint `start_time`. Airdrops can be done irrespective of any `start_time`.\
\
Ex: You launch your minter contract to mainnet on 12/24/2022 with Whitelist starting on Christmas (12/25/2022) and Public Mint the day after (12/26/2022). You can airdrop on Christmas Eve (12/24/2022) or Christmas (12/25/2022) or during Public Mint. **With great power comes great responsibility**.
{% endhint %}

At any time, before whitelist, during whitelist sale, or during public sale you are able to use `mint_to(address)` or `mint_for(token_id, address)` to do airdrops. If the special airdrop tokens are early token ids (i.e: 1, 2, 3, etc), then you want to deploy your contract early and give yourself enough time to run the airdrop and check the results.

Congratulations, you're officially a Stargaze Creator.
