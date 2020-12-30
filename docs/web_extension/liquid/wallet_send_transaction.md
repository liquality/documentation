# wallet_sendTransaction

Send an amount of an asset to confidential address

## Parameters

1. `address`: `String` - The recipient confidential address
2. `amount`: `Number` - Amount in satoshis to send
3. `asset`: `String` - Hash of the asset to send

```js
params: [
  'el1qqdzl6568hpe6ztz0mc47jcc3vsf8xzcnfsrxt6qmqu6zs8la7l659ex7fj6hk6r62cry4rvmpa2srjnc4dc7x566wwyu6kqn2',
  10000,
  `5ac9f65c0efcc4775e0baec4ec03abdde22473cd3cf33c0419ca290e0751b225`
]
```

## Returns

- `String (Hex)` - The transaction id

## Example

```js
> await liquid.request({ method: 'wallet_sendTransaction', params: ['el1qqdzl6568hpe6ztz0mc47jcc3vsf8xzcnfsrxt6qmqu6zs8la7l659ex7fj6hk6r62cry4rvmpa2srjnc4dc7x566wwyu6kqn2', 10000,'5ac9f65c0efcc4775e0baec4ec03abdde22473cd3cf33c0419ca290e0751b225'] })

"ba8d75e01ab32932d9ac899418a6bec95f2869e1b1c161b871f661c5a8789a0e"
```