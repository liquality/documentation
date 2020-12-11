## Prerequisites

Before we can invoke an operational instance of the agent and user interface, it is recommended that you install the following prerequisites. This is not a requirement, but suggested to avoid having to delegate trust to any third party. In this tutorial we will guide you through setting up a working stance of the liquality user interface and agent against a local **testing configuration**.  You can however also follow these same steps against testnet or mainnet nodes depending on your requirement and once you feel more comfortable with the setup.

Components which fall out of the scope for the liquality stack and which are required include:

### Required for the User Interface and Agent
* [Bitcoin Node](https://bitcoin.org/en/full-node)
* [Ethereum Node](https://github.com/trufflesuite/ganache-cli) - We will be using ganache considering this is for testing purposes.
* [NodeJS](https://nodejs.org/)

### Required for the Agent

* [MongoDB >= 4.x](https://www.mongodb.com/) - Required for the agent

### Optional depending on your preferences

* [Esplora Block Explorer APIs](https://github.com/Blockstream/esplora) - optional if you do not wish to use the blockstream hosted instance. 
* [CORS Proxy](https://www.npmjs.com/package/local-cors-proxy) - Required to enable CORS for your bitcoin node. You can also use nginx or any other reverse proxy which enables CORS separately.
* [JQ](https://stedolan.github.io/jq/) - Optional json command line parser, only used for legibility. 

For convenience, we've also added a `docker-compose` script which will setup a local bitcoin and ethereum environment which you can use for testing. 

```
$ git clone --branch master https://github.com/liquality/liquality-swap/
$ cd ./liquality-swap/src/test/integration/environment/
$ docker-compose up
```

The above will start a bitcoin node in `regtest` mode with a cors proxy exposed over port 18443, as well as a ethereum ganache instance over port 8545. You will have to install mongo separately. 

You can test this as follows.

For Bitcoin
```
$ curl -s --user bitcoin:local321 --data-binary '{"jsonrpc":"1.0","id":"curltext","method":"getblockchaininfo","params":[]}' -H 'content-type:text/plain;' http://127.0.0.1:18443 | jq .
{
  "result": {
    "chain": "regtest",
    "blocks": 2405,
    "headers": 2405,
    "bestblockhash": "3f468ba75ec193e2f61ada2d05316f2d64b4ada559ace068912168d23ba07090",
    "difficulty": 4.656542373906925e-10,
    "mediantime": 1573650754,
    "verificationprogress": 1,
    "initialblockdownload": false,
    "chainwork": "00000000000000000000000000000000000000000000000000000000000012cc",
    "size_on_disk": 753976,
    "pruned": false,
    "softforks": [
      {
        "id": "bip34",
        "version": 2,
        "reject": {
          "status": true
        }
      },
      {
        "id": "bip66",
        "version": 3,
        "reject": {
          "status": true
        }
      },
      {
        "id": "bip65",
        "version": 4,
        "reject": {
          "status": true
        }
      }
    ],
    "bip9_softforks": {
      "csv": {
        "status": "active",
        "startTime": 0,
        "timeout": 9223372036854776000,
        "since": 432
      },
      "segwit": {
        "status": "active",
        "startTime": -1,
        "timeout": 9223372036854776000,
        "since": 0
      }
    },
    "warnings": ""
  },
  "error": null,
  "id": "curltext"
}
```

For Ethereum

```
$ curl -s --data-binary '{"jsonrpc":"1.0","id":"curltext","method":"net_version","params":[]}' -H 'content-type:text/plain;' http://127.0.0.1:8545 | jq .
{
  "id": "curltext",
  "jsonrpc": "1.0",
  "result": "1573649903688"
}
```

For Mongo, we can use docker 

```
$ docker run -p27017:27017 -d mongo
```