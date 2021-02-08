# wallet_signPSBT

Sign the given input for a PSBT

## Parameters

1. `psbt`: `String` - The PSBT in base64 format
2. `inputs [Input]`

**Input**

- `input`: `Number` - The index of the input to sign
- `derivationPath`: `String` - The derivation path requied to sign the input

```js
params: [
  'cHNidP8BAFICAAAAAQHXVg9bz8W7xt+5+yOc/NM6xrk+N4tb1L2CdVLigKzgAAAAAAAAAAAAAXEDAAAAAAAAFgAUsbcyrOY/QlKFQFEN8ZkvPLly9uZ0U7pfAAEBK+gDAAAAAAAAIgAgYMATVrZ9ycDwP+12tinUlLpL35Y0O3884Zm8MXPfZAIBBSAEdFO6X7F1dqkUsbcyrOY/QlKFQFEN8ZkvPLly9uaIrAAA',
  [
    { index: 0, derivationPath: "84'/1'/0'/0/0" }
  ]
]
```

## Returns

- `String (Base64)` - The signed PSBT

## Example

```js
> await bitcoin.request({ method: 'wallet_signPSBT', params: [
  'cHNidP8BAFICAAAAAQHXVg9bz8W7xt+5+yOc/NM6xrk+N4tb1L2CdVLigKzgAAAAAAAAAAAAAXEDAAAAAAAAFgAUsbcyrOY/QlKFQFEN8ZkvPLly9uZ0U7pfAAEBK+gDAAAAAAAAIgAgYMATVrZ9ycDwP+12tinUlLpL35Y0O3884Zm8MXPfZAIBBSAEdFO6X7F1dqkUsbcyrOY/QlKFQFEN8ZkvPLly9uaIrAAA',
  [{ index: 0, derivationPath: "84'/1'/0'/0/0" }]
] })

"cHNidP8BAFICAAAAAQHXVg9bz8W7xt+5+yOc/NM6xrk+N4tb1L2CdVLigKzgAAAAAAAAAAAAAXEDAAAAAAAAFgAUsbcyrOY/QlKFQFEN8ZkvPLly9uZ0U7pfAAEBK+gDAAAAAAAAIgAgYMATVrZ9ycDwP+12tinUlLpL35Y0O3884Zm8MXPfZAIiAgMGAYYJKB28IUuObA8FWOz926cinKnxp95AG/inKfwLpEcwRAIgXOptwNaK5jpms5Nmz4Z6B4FcF6nq5/gXVJapnGm2Aw8CIHNDHbBKZYJmeu0k8a+hYZ2OmcJElcal9FkvUpsfnzHAAQEFIAR0U7pfsXV2qRSxtzKs5j9CUoVAUQ3xmS88uXL25oisAAA="
```