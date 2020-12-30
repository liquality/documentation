# wallet_getConnectedNetwork

Returns the current connected network

## Parameters

None

## Returns

- `Object` - The current bitcoin network object
  - `bech32`: `String`
  - `bip32`: `Object { public, private }`
  - `coinType`: `String`
  - `isTestnet`: `Boolean`
  - `messagePrefix`: `String`
  - `name`: `String`
  - `pubKeyHash`: `Number`
  - `scriptHash`: `Number`
  - `wif`: `Number`

## Example

```js
> await bitcoin.request({ method: 'wallet_getConnectedNetwork', params: [] })

{
  "name": "bitcoin_testnet",
  "messagePrefix": "\u0018Bitcoin Signed Message:\n",
  "bech32": "tb",
  "bip32": {
    "public": 70617039,
    "private": 70615956
  },
  "pubKeyHash": 111,
  "scriptHash": 196,
  "wif": 239,
  "coinType": "1",
  "isTestnet": true
}
```