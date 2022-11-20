# Deploy to Testnet

### Explorer

{% embed url="https://testnet-explorer.publicawesome.dev/stargaze" %}
[https://testnet-explorer.publicawesome.dev/stargaze](https://testnet-explorer.publicawesome.dev/stargaze)
{% endembed %}

### Faucet

Join our [Discord](https://discord.gg/stargaze) and request tokens in the `#faucet` channel. You will need the developer role from `#pick-a-role`.

### Endpoints

RPC: [https://rpc.elgafar-1.stargaze-apis.com](https://rpc.elgafar-1.stargaze-apis.com)

LCD: [https://rest.elgafar-1.stargaze-apis.com](https://rest.elgafar-1.stargaze-apis.com)

GRPC: [http://grpc-1.elgafar-1.stargaze-apis.com:26660](http://grpc-1.elgafar-1.stargaze-apis.com:26660)

GRPC2 : [http://grpc-2.elgafar-1.stargaze-apis.com:26660](http://grpc-1.elgafar-1.stargaze-apis.com:26660)

### Building starsd binary

```shell
git clone git@github.com:public-awesome/stargaze.git
cd stargaze
make install
```

### Deploying a contract&#x20;

Stargaze testnets are open and do not require a governance proposal to deploy new contracts. Follow the next steps to upload a contract.



1\. Create a stars address

```shell
starsd keys add testnet-key
- name: testnet-key
  type: local
  address: stars1e9rf2y807g32jv88j9ydpe7082rk9ck8w79xtz
  pubkey: '{"@type":"/cosmos.crypto.secp256k1.PubKey","key":"Aidseu5Pl9DYHGZpCE2CkqLckQ6KSgC5IJvLL1yc+lpo"}'
  mnemonic: ""
```

2\. Request funds through the `#faucet` channel

3\. Configure RPC endpoint and Chain ID

```shell
starsd config node https://rpc.elgafar-1.stargaze-apis.com:443
starsd config chain-id elgafar-1
```

4\. Check your account has balance

```shell
starsd query bank balances [address]
```

5\. Deploy a contract

After executing this transaction you will have a code id that you can use to instantiate the contract.

```shell
starsd tx wasm store contract.wasm --from testnet-key \
    --gas-prices 0.025ustars --gas-adjustment 1.7 --gas auto
```

6\. Instantiating a contract

```shell
INSTANTIATE_MSG=$(cat <<EOF
{
  "contract_param": "something"
}
EOF
)

starsd tx wasm instantiate [code_id] "$INSTANTIATE_MSG" --label "StargazeContract" \
 --admin [my-address] \
 --gas-prices 0.025ustars --gas auto --gas-adjustment 1.9 --from testnet-key 
 

```

