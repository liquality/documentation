## Installing the liquality automated agent

In this section we will guide you through the steps to install and run a liquality automated agent. The agent allows for market making, generation and management of orders, and processes swap requests without the need for manual processing.

### Pre-requisite

Before we can run an agent, you will need to confirm that you have a version of mongo db running.

`$ mongo
MongoDB shell version v4.2.1
connecting to: mongodb://127.0.0.1:27017/?compressors=disabled&gssapiServiceName=mongodb
Implicit session: session { "id" : UUID("7f50e6fc-8129-43e3-83b0-1e3a29fb4638") }
MongoDB server version: 4.2.1
`


1. Clone a copy of the liquality agent.

    `$ git clone --branch master https://github.com/liquality/agent`

2. Confirm that you are using the `master` branch.

    `$ cd ./agent/ && git branch`

3. Install the required node package manager dependencies.

    `$ npm install`

4. Make a copy of the example environment configuration files.

    `$ cp ./.env.example ./.env`
    `$ cp ./sample-config.toml ./config.toml`

5. Update the `.env` file to reference the `config.toml` file.
  
    `CONFIG_PATH=./config.toml`

6. Update the `config.toml` file to reflect your local environment.

    The most important parameters to update include your mongo db, as well as the bitcoin and ethereum node url's, credentials together with contract addresses for supported assets you wish to host.

7. Initiate our market data. 

    `$ npm run migrate`

    This will create a database in mongo db which includes the necessary list of supported assets, rates and other meta data which is configurable by the agent operator. 

    You can confirm that the market data has been created using the `mongo` cli.

    ```shell
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
    }```
    

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

```
$ vi ./src/config/config.js
...
hostAgent: 'http://localhost:3030',
...
```

Once enabled, your local user interface should present you with a list of available assets for swapping. 

## Conclusion

In this tutorial we guided you through setting up a local instance of the liquality swap user interface and complimentary automated agent. 

We encourage developers wishing to develop applications using the liquality libraries or to extend the functionality to submit Pull Requests get in touch via any of your support channels. 

Developers wishing to learn more about the standards and libraries are encouraged to checkout our [Chain Abstraction Layer](http://chainstackjs.org/).