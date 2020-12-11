## Installing the liquality swap interface

In this section we will be going through the steps required to installing and running a local liquality swap interface from your local system. 

1. Clone the liquality swap interface. 

    `$ git clone --branch master https://github.com/liquality/liquality-swap`

    NOTE: We attempt to maintain all work in progress on the `dev` branch, with stable changes being merged to the `master` branch. For the purpose of this tutorial, we will suggest using the development branch as it contains the latest changes required.

2. Confirm that you are using the `master` branch

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