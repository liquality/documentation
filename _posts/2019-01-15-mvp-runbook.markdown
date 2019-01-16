---
layout: post
title:  "Liquality Run Book"
date:   2019-01-15 15:21:28 +0400
categories: liquality knowledge base
---

# Swap run through steps

Here we cover the steps required execute a swap using the liquality swap interface. These steps should be executed before committing changes to the master branch of the [liquality-swap](https://github.com/liquality/liquality-swap) repository.

# Prerequisite

Before executing a swap you will need access to the following

1. Access to an instance of the swap interface
> For convenience, we have an example swap interface up and running at [https://liquality.io/swap/](https://liquality.io/swap/). You are also welcome to spin up your own instance by visiting our github repo at [https://github/liquality/liquality-swap/](https://github/liquality/liquality-swap/)
2. Access to a [Ledger Nano S](https://www.ledger.com/products/ledger-nano-s) with a sufficient balance of *bitcoin* required for the swap
3. Access to [Metamask](https://metamask.io/) with a sufficient balance of *ether* required for the swap
4. A counter party (person you are looking to swap with) that also meets the requirements set out here. Your counter party will need to provide you with their preferred addresses, and terms for the assets you are looking to swap.


## Initiating a swap (Party A) - Swap Initiation



1. Access the swap user interface
> Visit [our demonstration swap interface](https://liquality.io)
![Swap Initiation](/assets/initiate_1.png)
2. Select the preferred **Have** and **Want** assets
> E.g. I want BTC in exchange for ETH
![Swap Initiation](/assets/initiate_2.png)
3. Connect you wallets
> We currently only include support for two assets, nl. bitcoin and ether. Each asset is limited to a set of wallets including ledger (for bitcoin) and metamask (ether)
![Swap Initiation](/assets/initiate_3.png)
![Swap Initiation](/assets/initiate_4.png)
4. Enter the preferred amount of the asset you have
> The amount for the asset you have should be entered under the "Have" column to the left. This includes an entry where you can provide the largest denimination of the asset you have selected for the "Have" criteria
![Swap Initiation](/assets/initiate_6.png)

5. Enter the preferred amount of the asset you want
> The amount for the asset you have should be entered under the "Want" column to the right. This includes an entry where you can provide the largest denimination of the asset you have selected for the "Want" criteria
![Swap Initiation](/assets/initiate_5.png)
6. Enter the address of the counter party asset for the "Have" column
![Swap Initiation](/assets/initiate_7.png)
7. Enter the address of the counter party asset for the "Want" column
![Swap Initiation](/assets/initiate_8.png)
8. Select the *Next* option
9. Follow the prompts of the wallet from your "Have" selection
> A screen indicating that a swap has been initiated is shown. In this step, you would have locked up the amount of funds from the "Have" asset into a contract which is to be claimed by the counter party once they have confirmed the terms of the swap.
![Swap Initiation](/assets/initiate_9.png)
9. Send the swap counter party link to the person you have agreed to swap with
> This is the person that you have established the terms of the swap with and whos addresses have been entered into the terms of this agreement.
![Swap Initiation](/assets/initiate_10.png)
10. Select the "Link sent" option
> A screen "Awaiting Counterparty" is shown. On this screen, you are presented with information pertaining the to status of the swap. This includes, wether or not the counter party has accepted the terms of the trade, the terms of the swap Get x (Want) for y (have) active for the hh:mm:hr dd/mm/yyyy hh:mm. There is also a time indicator showing you the visual duration of the swap, together with the transaction ID of the "Have" asset you have locked up. You can also recover the swap link from the "Swap Link" option.
![Swap Initiation](/assets/initiate_11.png)
11. Review terms of claim
> On confirmation of the terms of the swap, a screen prompting to claim the "Want" portion of the swap is presented
![Swap Initiation](/assets/initiate_12.png)
12. Select "Claim your funds"
![Swap Initiation](/assets/initiate_13.png)
13. Follow the prompts of the wallet from your "Want" selection
> A screen indicating that a swap has been completed is shown
![Swap Initiation](/assets/initiate_14.png)

## Confirming the terms for a swap (Party B) - Counter parties agree
1. Access the Swap interface using a link provided by the swap initiator
> This link is generated during the "Swap Initiation"
![Swap Initiation](/assets/confirm_1.png)
2. Review the terms of the Swap
> Confirm that you are in agreement with the terms set out by the initiator of the swap. These terms include the "Want" and "Have" assets, their respective values and the rate at which they are to be swapped. There is also information regarding the duration for which the swap is still valid.
3. Connect you wallets
> We currently only include support for two assets, nl. bitcoin and ether. Each asset is limited to a set of wallets including ledger (for bitcoin) and metamask (ether)
![Swap Initiation](/assets/confirm_2.png)
4. Select the *Confirm Terms* option
> Select this option if you are happy with the terms of this swap. Alternatively, initiate a swap with the revised terms and send the link to the counter party, or ask them to re-configured these terms based on the preferred values.
> Note: It might be undesirable to renogitiate these terms considering that the initiator has already locked up the funds for the initial terms of the contract.
![Swap Initiation](/assets/confirm_3.png)
5. Follow the prompts of the wallet from your "Have" selection
> A screen indicating that a swap has been confirmed is shown. In this step, you would have locked up the amount of funds from the "Have" asset into a contract which is to be claimed by the counter party once they are satisfied that you have  confirmed the terms of the swap.
> A screen "Counterparty hasn't claimed" is shown. On this screen, you are presented with information pertaining the to status of the swap. This includes, wether or not the counter party has claimed the funds based on the terms of the trade, the terms of the swap Get x (Want) for y (have) active for the hh:mm:hr dd/mm/yyyy hh:mm (usually half the duration of the initial terms). There is also a time indicator showing you the visual duration of the swap, together with the transaction ID of the "Have" asset you have locked up. You can also recover the swap link from the "Swap Link" option.
![Swap Initiation](/assets/confirm_4.png)
6. Review terms of claim
> On confirmation of the terms of the claim, a screen prompting to claim the "Want" portion of the swap is presented
![Swap Initiation](/assets/confirm_5.png)
7. Select "Claim your funds"
![Swap Initiation](/assets/confirm_6.png)
8. Follow the prompts of the wallet from your "Want" selection
> A screen indicating that a swap has been completed is shown
![Swap Initiation](/assets/confirm_7.png)
