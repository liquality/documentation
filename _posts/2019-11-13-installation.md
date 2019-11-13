# Liquality installation guide

## Introduction

Liquality has developed a set of compatibility standards, libraries and reference implementations which allow for a trust minimized swaps between compatible blockchains. 

These include, a set of standards for cross-chain atomic swaps, an [chain abstraction layer](https://medium.com/liquality/the-missing-tool-to-cross-chain-development-2ebfe898efa1) which simplifies the development of communications between the supported chains as well as a [user interface or front-end](https://github.com/liquality/liquality-swap) and [launcher](https://github.com/liquality/liquality-launcher) and [automated agent or optional back-end](https://github.com/liquality/agent) which utilizes the library. Although each user interface and agent can be executed independently, we have also added integration between the two should you wish to run such a configuration.

## Architecture

The approach taken by the contributors have focussed on developing interoperability as a common language and standards over further intermediation of an additional component or third-party blockchain and/or middleware. 

The standards currently developed for interoperability include a slightly revised version of [Bitcoin Improvement Proposal 199](https://github.com/bitcoin/bips/blob/master/bip-0199.mediawiki) and a compatibility standards for Etheream called the [Ethereum Improvement Proposal 1630](https://github.com/ethereum/EIPs/issues/1631). 

These standards implement a common language for executing cross-chain atomic swaps between bitcoin, ether, and ERC20 tokens, and form the foundation for extending support for additional digital assets which support [sha256 hashlocks](https://en.bitcoin.it/wiki/Hashlock) and [timelocks](https://en.bitcoin.it/wiki/Timelock). 

The below figure shows a high-level view of the liquality stack architecture. 

![Architecture](../assets/architecture.png)

The liquality stack is licensed under the [MIT License](https://github.com/liquality/chainabstractionlayer/blob/dev/LICENSE.md), and is a completely free and open source community project. Each component in the stack aims to ensure that you can run and customize your own instance without any dependency on a third-party. 

## Prerequisites

Before we can invoke an operational instance of the agent and user interface, it is recommended that you execute this against your own environment. This is not a requirement, but suggested to avoid having to delegate trust to any third party. In this tutorial we will guide you through setting up a working stance of the liquality user interface and agent against a local testing configuration.  You can however configure the stack against testnet or mainnet nodes once you feel more comfortable with the setup.

Components which fall out of the scope for the liquality stack and which are required include:

* [Bitcoin Node](https://bitcoin.org/en/full-node)
* [Ethereum Node](https://github.com/trufflesuite/ganache-cli) - We will be using ganache considering this is for testing purposes.
* [Esplora Block Explorer APIs](https://github.com/Blockstream/esplora)
* [NodeJS](https://nodejs.org/)
* [CORS Proxy](https://www.npmjs.com/package/local-cors-proxy) - Required to enable CORS for your bitcoin node
* [MongoDB](https://www.mongodb.com/) - Required for the agent
* [JQ](https://stedolan.github.io/jq/) - Optional json command line parser, only used for legibility. 



## Installing the liquality swap interface

In this section we will be going through the steps required to invoke a local liquality swap interface from your local system. 

1. Clone the liquality swap interface. 

    `$ git clone https://github.com/liquality/liquality-swap`

    NOTE: We attempt to maintain all work in progress on the `dev` branch, with stable changes being merged to the `master` branch. For the purpose of this tutorial, we will suggest using the development branch as it contains the latest changes required.

2. Confirm that you are using the `dev` branch

    `$ cd liquality-swap && git branch`

3. Install the required node package manager dependencies.

    `$ npm install`

4. Update the configuration to match your environment.

    `$ vi ./src/config/config.js`

    The configuration script allows you to set your own list of supported assets, together with a list of your preferred trusted nodes. 

    For now, we will comment out the configuration for the `hostAgent`. This allows for integration with the liquality agent that is optional for market making, and which we will cover in the next section.

    `//  hostAgent: 'http://localhost:3030',`

    Important options to update here include the urls to your nodes, as well as any contract addresses.

    Considering that the front-end application requires access to the RPC end-points for your nodes, we will need to also startup a cors proxy for bitcoin as it does not support cors out of the box.

    To do so you can run 

    ```
    lcp --proxyUrl http://127.0.0.1:18443

    Proxy Active

    Proxy Url: http://127.0.0.1:18443
    Proxy Partial: proxy
    PORT: 8010

    To start using the proxy simply replace the proxied part of your url with: http://localhost:8010/proxy
    ```

5. Starting the liquality swap interface. 

    `$ npm start`

    This should invoke an https server on port 3000 and automatically [attempt to open it with your default browser](https://localhost:3000). For the purposes of this tutorial, we will be using chrome as most of the tests have been done using chrome, but should also work in firefox and edge. 

    NOTE: As this process provides a convenient way for bootstrapping the server, it uses a self signed certificate which might be prompted by the browser. To overcome this, you will might need to enable allowing insecure certificates for localhost by visiting the following url in chrome.

    ```chrome://flags/#allow-insecure-localhost```

Following the above, you should now have your very own instance of the liquality swap interface up and running on your system. We have also provided a packaged solution which can be downloaded from [the liquality launcher repository](https://github.com/liquality/liquality-launcher/releases).

## Automated Agent

In this section we will guide you through the steps to invoke a liquality automated agent which allows for hosting a market making agent that generate quotes, and processes swap requests without any manual intervention.

### Pre-requisite

Before we can run an agent, you will need to confirm that you have a version of mongo db running.

`$ mongo
MongoDB shell version v4.2.1
connecting to: mongodb://127.0.0.1:27017/?compressors=disabled&gssapiServiceName=mongodb
Implicit session: session { "id" : UUID("7f50e6fc-8129-43e3-83b0-1e3a29fb4638") }
MongoDB server version: 4.2.1
`


1. Clone a copy of the liquality agent.

    `$ git clone https://github.com/liquality/agent`

2. Confirm that you are using the `dev` branch

    `$ cd ./agent/ && git branch`

3. Install the required node package manager dependencies.

    `$ npm install`

4. Make a copy of the example environment configuration files.

    `$ cp ./.env.example ./.env`
    `$ cp ./sample-config.toml ./config.toml`

5. Update the `.env` file to reference the `config.toml` file
  
    `CONFIG_PATH=./config.toml`

6. Update the `config.toml` file to reflect your local environment.

    The most important parameters to update include your mongo db, as well as the bitcoin and ethereum node url's, credentials together with contract addresses for supported assets you wish to host.

7. Initiate our market data. 

    `$ npm run migrate`

    This will create a database in mongo db which includes the necessary list of supported assets, rates and other meta data which is configurable by the agent operator. 

    You can confirm that the market data has been created using the `mongo` cli.

    ```
    $ mongo mongodb://127.0.0.1/liquality
    MongoDB shell version v4.2.1
    connecting to: mongodb://127.0.0.1:27017/?compressors=disabled&gssapiServiceName=mongodb
    Implicit session: session { "id" : UUID("8eae6b2e-9be7-4bcc-ab17-5cd198a68063") }
    MongoDB server version: 4.2.1 
    db.markets.find({}).pretty()
    {
        "_id" : ObjectId("5dcbec1e21f1c02f07b0818e"),
        "from" : "BTC",
        "to" : "ETH",
        "min" : 100000,
        "max" : 5000000,
        "minConf" : 1,
        "rate" : 48.26,
        "spread" : 0.05,
        "orderExpiresIn" : 3600000,
        "status" : "ACTIVE",
        "__v" : 0
    }
    {
        "_id" : ObjectId("5dcbec1e21f1c02f07b0818f"),
        "from" : "ETH",
        "to" : "BTC",
        "min" : 250000000000000000,
        "max" : 2500000000000000000,
        "minConf" : 1,
        "rate" : 0.028,
        "spread" : 0.05,
        "orderExpiresIn" : 3600000,
        "status" : "ACTIVE",
        "__v" : 0
    }
    {
        "_id" : ObjectId("5dcbec1e21f1c02f07b08190"),
        "from" : "DAI",
        "to" : "BTC",
        "min" : 1000000000000000000,
        "max" : 100000000000000000000,
        "minConf" : 1,
        "rate" : 0.000135,
        "spread" : 0.05,
        "orderExpiresIn" : 3600000,
        "status" : "ACTIVE",
        "__v" : 0
    }
    ```

8. Start the agent API service.

    The API service provides an http interface for create quotes and managing order information in mongo. Support for this API has been integrated into the UI, but can be used for integration by any other application.  

    `$ npm run api`

    We can confirm that the api is up and running by issuing a GET query against the marketinfo endpoint.

    ```
    $ curl -s  http://localhost:3030/api/swap/marketinfo | jq .
    [
    {
        "from": "BTC",
        "to": "ETH",
        "min": 100000,
        "max": 5000000,
        "minConf": 1,
        "rate": 48.26,
        "spread": 0.05,
        "orderExpiresIn": 3600000,
        "status": "ACTIVE"
    },
    {
        "from": "ETH",
        "to": "BTC",
        "min": 2.5e+17,
        "max": 2.5e+18,
        "minConf": 1,
        "rate": 0.028,
        "spread": 0.05,
        "orderExpiresIn": 3600000,
        "status": "ACTIVE"
    },
    {
        "from": "DAI",
        "to": "BTC",
        "min": 1e+18,
        "max": 1e+20,
        "minConf": 1,
        "rate": 0.000135,
        "spread": 0.05,
        "orderExpiresIn": 3600000,
        "status": "ACTIVE"
    }
    ]
    ```

9. Start the worker processes.

    To avoid adding overhead to the APIs, we have isolated all the administrative overhead and back-office processing into a service worker architecture. This provides a separation of concerns which allows for more streamlined operation as well as debugging and future scaling. 

    `$ npm run worker`

You should now have a operation version of the agent running on your local system. 

You can now enable integration between the user interface and agent by uncommenting the `hostAgent` configuration parameter we had added during the previous steps.

`$ vi ./src/config/config.js`
`hostAgent: 'http://localhost:3030',`

Once enabled, your local user interface should present you with a list of available assets for swapping. 

## Conclusion

In this tutorial we guided you through setting up a local instance of the liquality swap user interface and complimentary automated agent. 

We encourage developers wishing to develop applications using the liquality libraries or to extend the functionality to submit Pull Requests get in touch via any of your support channels. 