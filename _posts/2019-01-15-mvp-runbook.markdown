---
layout: post
title:  "Liquality Run Book"
date:   2019-01-15 15:21:28 +0400
categories: liquality knowledge base
---

# Swap run through steps

Here we cover the steps required to be run before merging your changes with the master branch.

# Prerequisite

Before executing a swap you will need access to the following

1. An instance of the swap interface deployed
> We already have an example swap interface up and running at [https://liquality.io/swap/](https://liquality.io/swap/). You are also welcome to spin up your own instance by visiting our github repo at [https://github/liquality/liquality-swap/](https://github/liquality/liquality-swap/)
2. Access to a [Ledger Nano S](https://www.ledger.com/products/ledger-nano-s) with a sufficient balance of ether required for the swap
3. Access to [Metamask](https://metamask.io/) with a sufficient balance of ether required for the swap
4. A counter party (person you are looking to swap with) that also meets the requirements set out here. Your counter party will need to provide you with their preferred addresses for the assets you are looking to swap. In this case, their bitcoin and ethereum addresses.


## Initiating a swap (Party A)



1. Access the swap user interface
>   Visit [our demonstration swap interface](https://liquality.io)
2. Select the preferred have and want assets
> E.g. I want BTC in exchange for ETH
3. Connect you wallets
> We currently only include support for two assets, nl. bitcoin and ether. Each asset is limited to a set of wallets including ledger (for bitcoin) and metamask (ether)
4. Enter the preferred amount of the asset you have
> The amount for the asset you have should be entered under the "Have" column to the left. This includes an entry where you can provide the largest denimination of the asset you have selected for the "Have" criteria
5. Enter the preferred amount of the asset you want
> The amount for the asset you have should be entered under the "Want" column to the right. This includes an entry where you can provide the largest denimination of the asset you have selected for the "Want" criteria
6. Enter the address of the counter party asset for the "Have" column
7. Enter the address of the counter party asset for the "Want" column
8. Select the *Next* option
9. Follow the prompts of the wallet from your "Have" wallet
> A screen indicating that a swap has been initiated should be shown. In this step, you would have locked up the amount of funds from the "Have" asset into a contract which is to be claimed by the counter party once they have confirmed the terms of the swap.
9. Send the swap counter party link to the person you have agreed to swap with
> This is the person that you have established the terms of the swap with and whos addresses have been entered into the terms of this agreement.
10. Select the "Link sent" option
> A screen "Awaiting Counterparty" is shown. On this screen, you are presented with information pertaining the to status of the swap. This includes, wether or not the counter party has accepted the terms of the trade, the terms of the swap Get x (Want) for y (have) active for the hh:mm:hr dd/mm/yyyy hh:mm. There is also a time indicator showing you the visual duration of the swap, together with the transaction ID of the "Have" asset you have locked up. You can also recover the swap link from the "Swap Link" option.


## Confirming the terms for a swap (Party B)
