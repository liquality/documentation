# wallet_sendTransaction

Send an amount to address

## Parameters

1. `address`: `String` - The message to sign
2. `amount`: `Number` - Amount in satoshis to send

```js
params: [
  'tb1qqwn2dp8mundc6mf3xt4c8puqakk0vrcgzdayq2',
  10000
]
```

## Returns

- `String (Hex)` - The transaction id

## Example

```js
> await bitcoin.request({ method: 'wallet_sendTransaction', params: ['tb1qqwn2dp8mundc6mf3xt4c8puqakk0vrcgzdayq2', 10000] })

"ba8d75e01ab32932d9ac899418a6bec95f2869e1b1c161b871f661c5a8789a0e"
```