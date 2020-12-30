# wallet_signMessage

Sign a message with the public key of a given confidential address

## Parameters

1. `message`: `String` - The message to sign
2. `address`: `String` - The address to sign with

```js
params: [
  'Better with code than with words',
  'el1qqdzl6568hpe6ztz0mc47jcc3vsf8xzcnfsrxt6qmqu6zs8la7l659ex7fj6hk6r62cry4rvmpa2srjnc4dc7x566wwyu6kqn2'
]
```

## Returns

- `String (Hex)` - The signature

## Example

```js
> await liquid.request({ method: 'wallet_signMessage', params: [
  'Better with code than with words',
  'el1qqdzl6568hpe6ztz0mc47jcc3vsf8xzcnfsrxt6qmqu6zs8la7l659ex7fj6hk6r62cry4rvmpa2srjnc4dc7x566wwyu6kqn2'
] })

"2047ab7b010687146ef9d69648cbdc4610b7ebaf6f21d7255f2113fe87b24d4b4264eef980d21f29d3ba81b369e41bf532b1292021af16c6773187c34d090b7efb"
```