# wallet_getConnectedNetwork

Returns the current connected network

## Parameters

None

## Returns

- `Object` - The current liquid network object
  - `bech32`: `String`
  - `blech32`: `String`
  - `bip32`: `Object { public, private }`
  - `coinType`: `String`
  - `isTestnet`: `Boolean`
  - `messagePrefix`: `String`
  - `name`: `String`
  - `pubKeyHash`: `Number`
  - `scriptHash`: `Number`
  - `wif`: `Number`
  - `confidentialPrefix`: `Number`
  - `assetHash`: `String`


## Example

```js
> await liquid.request({ method: 'wallet_getConnectedNetwork', params: [] })

{
  "name": "liquid_regtest",
  "messagePrefix": "\x18Liquid Signed Message:\n",
  "bech32": "ert",
  "blech32": "el",
  "bip32": {
    "public": 0x043587cf,
    "private": 0x04358394
  },
  "pubKeyHash": 235,
  "scriptHash": 75,
  "wif": 0xef,
  "coinType": "1",
  "isTestnet": true,
  "confidentialPrefix": 4,
  "assetHash": "5ac9f65c0efcc4775e0baec4ec03abdde22473cd3cf33c0419ca290e0751b225",
}
```