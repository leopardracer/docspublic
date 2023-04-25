---
cover: ../../../.gitbook/assets/Stargaze_new_logo_black_bg_padding.png
coverY: 0
---

# 1. Setup a basic project

## Initialize a new project

Setting up your project for minting is done via a set of command-line tools. Start by cloning a sample repository, and replace it with your project contents.

Replace `[my-project-name]` with the name of your project.

```
git clone https://github.com/public-awesome/stargaze-tools [my-project-name]
cd [my-project-name]
yarn install
```

## Create a testnet account

In order to deploy a smart contract on Stargaze, you'll need an account with some STARS in it. For this tutorial, we will be instantiating our smart contract on a Stargaze testnet.

```
yarn account
```

You should see mnemonic and address printed out like:

```
>> mnemonic: sure adapt throw vocal sibling mom already light dinner sail survey sphere
pubkey: {
  type: 'tendermint/PubKeySecp256k1',
  value: 'AwqXZKoqAJl+9R3qWgseVYomxFN2akDGQ2rzS6P/Oyfo'
}
address: stars1us0r08kr3jtr0h74skk46hl6cmtsrptlqyfstl
✨  Done in 1.03s.
```

Now edit `config.js` and fill in the above mnemonic and address in their corresponding fields.

{% hint style="info" %}
Do not use a mainnet mnemonic / seed phrase for testing. Please use the above method to generate a test account. For mainnet, see [Launching on mainnet with Keplr](../9.-launching-on-mainnet/9a.-launching-on-mainnet-with-keplr-optional.md).
{% endhint %}

## Fund account from testnet faucet

Get testnet tokens from the [Stargaze Discord](https://discord.gg/stargaze) channel `#🚰faucet`. Type your address from the above step to receive some coins.

Example:

```
$request [stars1...]
```
