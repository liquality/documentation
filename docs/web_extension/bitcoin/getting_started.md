# Getting Started

Download the [Liquality Wallet](https://chrome.google.com/webstore/detail/liquality-wallet/kpfopkelmapcoipemfendmdcghnegimn?hl=en).

## Connecting with the extension

The extension injects the api into pages under `window.bitcoin`. 

To check that the extension is running and accessible on your web application, log the `window.bitcoin` object.

```js
> console.log(window.bitcoin)
{ enable: ƒ, request: ƒ }
```

As shown, the bitcoin interface exposes 2 very simple functions.

## Enable

Applications that need access to the wallet must first request that the extension is enabled. 

```js
> await window.bitcoin.enable()
```

This will prompt the user to allow access to the wallet for the application.

![Wallet](../assets/enable.png)

If the prompt is accepted, the first address of the user wallet will be returned. This can be used as a form of identity.

```js
[
  {
    "address": "tb1qqwn2dp8mundc6mf3xt4c8puqakk0vrcgzdayq2",
    "derivationPath": "84'/1'/0'/0/0",
    "publicKey": "02eff43612d911ec20d344d6eada4a9727be7a7da90c8451d26e182f8d25dc33b8",
    "index": 0
  }
]
```

The application can then make further requests to the wallet using `window.bitcoin.request()`

## Request

The `request` method is used to request information from the wallet (e.g. addresses, public keys) as well as prompt for signatures.

For example: We can retrieve 10 addresses using the `wallet_getAddresses` method:

```js
> await bitcoin.request({ method: 'wallet_getAddresses', params: [0, 10] })
[
  {address: "tb1qqwn2dp8mundc6mf3xt4c8puqakk0vrcgzdayq2", derivationPath: "84'/1'/0'/0/0", publicKey: {…}, index: 0}
  {address: "tb1qca6k2ke5jdrwmdqcku4eex4k9hzzzhzshhsgpn", derivationPath: "84'/1'/0'/0/1", publicKey: {…}, index: 1}
  {address: "tb1q6e36gyc8vhv97k9m2uldndsl8xg80yd49mhqpx", derivationPath: "84'/1'/0'/0/2", publicKey: {…}, index: 2}
  {address: "tb1qvphc32p0qxl2fm89r04epmtxvdt7l7dl5a955c", derivationPath: "84'/1'/0'/0/3", publicKey: {…}, index: 3}
  {address: "tb1qxm90ahvjnut9d7mw8d0r22czldnu3kqyef55nn", derivationPath: "84'/1'/0'/0/4", publicKey: {…}, index: 4}
  {address: "tb1q8wjjk4gu3am2tjg833qulqt69ny8e24vt8ccj6", derivationPath: "84'/1'/0'/0/5", publicKey: {…}, index: 5}
  {address: "tb1q7jkkn80maps9z068u22jrpv65t9epjlrl4zpzj", derivationPath: "84'/1'/0'/0/6", publicKey: {…}, index: 6}
  {address: "tb1qrzpw5rrm9w8qf3v3y43av3npeqhgp9lng5xtyk", derivationPath: "84'/1'/0'/0/7", publicKey: {…}, index: 7}
  {address: "tb1q9vu3j2m6u48sv53g7e24lfx2c9mavv0ee6wr02", derivationPath: "84'/1'/0'/0/8", publicKey: {…}, index: 8}
  {address: "tb1q0m2f0vjc4njy5d0vzmlwre8jdtar9x9w7nz9jg", derivationPath: "84'/1'/0'/0/9", publicKey: {…}, index: 9}
]
```

## Supported Requests

- [wallet_getConnectedNetwork](../wallet_get_connected_network)
- [wallet_getAddresses](../wallet_get_addresses)
- [wallet_signMessage](../wallet_sign_message)
- [wallet_sendTransaction](../wallet_send_transaction)
- [wallet_signPSBT](../wallet_sign_psbt)
