# wallet_signPSET

Sign the given input for a PSET

## Parameters

- `pset`: `String` - The PSET in base64 format
- `inputs`: `Array<Input>` - The array on inputs to be signed

- Input: `Object`
  - `index`: `Number` - The input index to be signed
  - `address`:  `String` - The address associated with the input that requires signing

```js
params: [
  'cHNidP8BAFICAAAAAQHXVg9bz8W7xt+5+yOc/NM6xrk+N4tb1L2CdVLigKzgAAAAAAAAAAAAAXEDAAAAAAAAFgAUsbcyrOY/QlKFQFEN8ZkvPLly9uZ0U7pfAAEBK+gDAAAAAAAAIgAgYMATVrZ9ycDwP+12tinUlLpL35Y0O3884Zm8MXPfZAIBBSAEdFO6X7F1dqkUsbcyrOY/QlKFQFEN8ZkvPLly9uaIrAAA',
  [
    {
      index: 0,
      address: 'el1qqdzl6568hpe6ztz0mc47jcc3vsf8xzcnfsrxt6qmqu6zs8la7l659ex7fj6hk6r62cry4rvmpa2srjnc4dc7x566wwyu6kqn2'
    }
  ]
]
```

## Returns

- `String (Base64)` - The signed confidential PSET

## Example

```js
> await liquid.request({ method: 'wallet_signPSET', params: [
  'cHNidP8BAFICAAAAAQHXVg9bz8W7xt+5+yOc/NM6xrk+N4tb1L2CdVLigKzgAAAAAAAAAAAAAXEDAAAAAAAAFgAUsbcyrOY/QlKFQFEN8ZkvPLly9uZ0U7pfAAEBK+gDAAAAAAAAIgAgYMATVrZ9ycDwP+12tinUlLpL35Y0O3884Zm8MXPfZAIBBSAEdFO6X7F1dqkUsbcyrOY/QlKFQFEN8ZkvPLly9uaIrAAA',
  [
    {
      index: 0,
      address: 'el1qqdzl6568hpe6ztz0mc47jcc3vsf8xzcnfsrxt6qmqu6zs8la7l659ex7fj6hk6r62cry4rvmpa2srjnc4dc7x566wwyu6kqn2'
    }
  ]
] })

"cHNidP8BAFICAAAAAQHXVg9bz8W7xt+5+yOc/NM6xrk+N4tb1L2CdVLigKzgAAAAAAAAAAAAAXEDAAAAAAAAFgAUsbcyrOY/QlKFQFEN8ZkvPLly9uZ0U7pfAAEBK+gDAAAAAAAAIgAgYMATVrZ9ycDwP+12tinUlLpL35Y0O3884Zm8MXPfZAIiAgMGAYYJKB28IUuObA8FWOz926cinKnxp95AG/inKfwLpEcwRAIgXOptwNaK5jpms5Nmz4Z6B4FcF6nq5/gXVJapnGm2Aw8CIHNDHbBKZYJmeu0k8a+hYZ2OmcJElcal9FkvUpsfnzHAAQEFIAR0U7pfsXV2qRSxtzKs5j9CUoVAUQ3xmS88uXL25oisAAA="
```