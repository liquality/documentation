# wallet_signMessage

Sign a message with the public key of a given address

## Parameters

1. `message`: `String` - The message to sign
2. `address`: `String` - The address to sign with

```js
params: [
  'Better with code than with words',
  'tb1qqwn2dp8mundc6mf3xt4c8puqakk0vrcgzdayq2'
]
```

## Returns

- `String (Hex)` - The signature

## Example

```js
> await bitcoin.request({ method: 'wallet_signMessage', params: [
  'Better with code than with words',
  'tb1qqwn2dp8mundc6mf3xt4c8puqakk0vrcgzdayq2'
] })

"2047ab7b010687146ef9d69648cbdc4610b7ebaf6f21d7255f2113fe87b24d4b4264eef980d21f29d3ba81b369e41bf532b1292021af16c6773187c34d090b7efb"
```