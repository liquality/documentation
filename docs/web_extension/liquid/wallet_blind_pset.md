# wallet_blindPSET

Blind the given PSET

## Parameters

1. `pset`: `String` - The PSET in base64 format
2. `inputAddresses`: `Array<String>` - The addresses associated with the inputs that requires blinding
3. `outputAddresses`: `Array<String>` - The addresses associated with the outputs that requires blinding

```js
params: [
  'cHNidP8BAFICAAAAAQHXVg9bz8W7xt+5+yOc/NM6xrk+N4tb1L2CdVLigKzgAAAAAAAAAAAAAXEDAAAAAAAAFgAUsbcyrOY/QlKFQFEN8ZkvPLly9uZ0U7pfAAEBK+gDAAAAAAAAIgAgYMATVrZ9ycDwP+12tinUlLpL35Y0O3884Zm8MXPfZAIBBSAEdFO6X7F1dqkUsbcyrOY/QlKFQFEN8ZkvPLly9uaIrAAA',
  [
    'el1qqd6q3nsyzj6pvdudqesjuw2v3ehxmu660y7ap7gp7zaaqn2df5qmdlmg6g6adt8r8sysxwn6s7m4hm2q83j0jha6v4hlq4755'
  ],
  [
    'el1qqdzl6568hpe6ztz0mc47jcc3vsf8xzcnfsrxt6qmqu6zs8la7l659ex7fj6hk6r62cry4rvmpa2srjnc4dc7x566wwyu6kqn2',
    'el1qqtguh9nlm6wqvrkyjf3luk6q8337qm8rxttqguyzyyh4et5k5r0e9f4xq3f04840jyf0562x4z7pdhgxsatfu4qg5cd3nltvg'
  ]
]
```

## Returns

- `String (Base64)` - The blinded confidential PSET

## Example

```js
> await liquid.request({ method: 'wallet_blindPSET', params: [
  'cHNidP8BAFICAAAAAQHXVg9bz8W7xt+5+yOc/NM6xrk+N4tb1L2CdVLigKzgAAAAAAAAAAAAAXEDAAAAAAAAFgAUsbcyrOY/QlKFQFEN8ZkvPLly9uZ0U7pfAAEBK+gDAAAAAAAAIgAgYMATVrZ9ycDwP+12tinUlLpL35Y0O3884Zm8MXPfZAIBBSAEdFO6X7F1dqkUsbcyrOY/QlKFQFEN8ZkvPLly9uaIrAAA',
  [
    'el1qqd6q3nsyzj6pvdudqesjuw2v3ehxmu660y7ap7gp7zaaqn2df5qmdlmg6g6adt8r8sysxwn6s7m4hm2q83j0jha6v4hlq4755'
  ],
  [
    'el1qqdzl6568hpe6ztz0mc47jcc3vsf8xzcnfsrxt6qmqu6zs8la7l659ex7fj6hk6r62cry4rvmpa2srjnc4dc7x566wwyu6kqn2',
    'el1qqtguh9nlm6wqvrkyjf3luk6q8337qm8rxttqguyzyyh4et5k5r0e9f4xq3f04840jyf0562x4z7pdhgxsatfu4qg5cd3nltvg'
  ]
] })

"cHNidP8BAFICAAAAAQHXVg9bz8W7xt+5+yOc/NM6xrk+N4tb1L2CdVLigKzgAAAAAAAAAAAAAXEDAAAAAAAAFgAUsbcyrOY/QlKFQFEN8ZkvPLly9uZ0U7pfAAEBK+gDAAAAAAAAIgAgYMATVrZ9ycDwP+12tinUlLpL35Y0O3884Zm8MXPfZAIiAgMGAYYJKB28IUuObA8FWOz926cinKnxp95AG/inKfwLpEcwRAIgXOptwNaK5jpms5Nmz4Z6B4FcF6nq5/gXVJapnGm2Aw8CIHNDHbBKZYJmeu0k8a+hYZ2OmcJElcal9FkvUpsfnzHAAQEFIAR0U7pfsXV2qRSxtzKs5j9CUoVAUQ3xmS88uXL25oisAAA="
```