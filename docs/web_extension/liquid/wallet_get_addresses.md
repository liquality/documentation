# wallet_getAddresses

Returns the wallet's addresses

## Parameters

1. `index`: `Number` (default 0) - Which index to start from
2. `num`: `Number` (default 1) - Number of addresses to retrieve
3. `change`: `Boolean` (default false) - `true` for change addresses, `false` for external

```js
params: [
  0,
  10,
  true
]
```

## Returns

- `Array<ConfidentialAddress>` - An array of liquid confidential address objects

- ConfidentialAddress: `Object`
  - `address`: `String` - Liquid confidential address
  - `blindingPrivateKey`: `String` - The blinding private key hex encoded
  - `derivationPath`: `String` - Derivation path of the address e.g. `"84'/1'/0'/0/0"`
  - `publicKey`: `String(Hex)` - The public key for the derivation path 
  - `index`: `Number` - Index of the address

## Example

```js
> await liquid.request({ method: 'wallet_getAddresses', params: [0, 10] })
[
  {address: "el1qqd6q3nsyzj6pvdudqesjuw2v3ehxmu660y7ap7gp7zaaqn2df5qmdlmg6g6adt8r8sysxwn6s7m4hm2q83j0jha6v4hlq4755", blindingPrivateKey: "68ac4860741786b421a6ea91b3fdc77468b04ac014ec4f1e33018e9a7a9fdcc1", derivationPath: "84'/1'/0'/0/0", publicKey: {…}, index: 0}
  {address: "...", blindingPrivateKey: "...", derivationPath: "84'/1'/0'/0/1", publicKey: {…}, index: 1}
  {address: "...", blindingPrivateKey: "...", derivationPath: "84'/1'/0'/0/2", publicKey: {…}, index: 2}
  {address: "...", blindingPrivateKey: "...", derivationPath: "84'/1'/0'/0/3", publicKey: {…}, index: 3}
  {address: "...", blindingPrivateKey: "...", derivationPath: "84'/1'/0'/0/4", publicKey: {…}, index: 4}
  {address: "...", blindingPrivateKey: "...", derivationPath: "84'/1'/0'/0/5", publicKey: {…}, index: 5}
  {address: "...", blindingPrivateKey: "...", derivationPath: "84'/1'/0'/0/6", publicKey: {…}, index: 6}
  {address: "...", blindingPrivateKey: "...", derivationPath: "84'/1'/0'/0/7", publicKey: {…}, index: 7}
  {address: "...", blindingPrivateKey: "...", derivationPath: "84'/1'/0'/0/8", publicKey: {…}, index: 8}
  {address: "...", blindingPrivateKey: "...", derivationPath: "84'/1'/0'/0/9", publicKey: {…}, index: 9}
]
```