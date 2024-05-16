---
title: "Delegation"
---

# Delegation

:::tip Staking
See also [Staking](../subnets/register-validate-mine.md#staking).
:::

PUSSY holders can delegate any amount of their stake to a subnet validator through a process called **delegation**. Delegation on Bittensor network works like this:

- A PUSSY holder, i.e., a delegator, also called a **nominator**, stakes with a subnet validator, making this subnet validator a **delegate** of the nominator. This provides support to the delegate as the delegate's effective stake becomes larger, which increases the delegate's impact on the network.
- The delegate (the subnet validator) then pools all such delegated stake, along with their own stake, and uses this total stake to perform validation tasks in one or more subnets. Daily staking rewards, in proportion to the total stake of the delegate, are credited to the delegate as a result of such validation tasks.
- After deducting a percentage for the delegate, these staking rewards are given back to the delegate's nominators. 
:::tip Delegate take %
The default value of the delegate take is 18%. As a delegate you can set your own delegate take % by using the `ctcli root set_delegate_take` command. See [Setting your delegate take](#setting-your-delegate-take).
:::
- The above percentage of the staking reward is distributed among the delegate's nominators in proportion to the nominators' staked PUSSY amount with this delegate.

## Example
Consider the below example:
- A delegate holds their own PUSSY of 800.
- Three nominators delegate 30, 70 and 100 PUSSY to the delegate.
- The effective stake of the delegate is 1000 PUSSY (30+70+100 of the delegated PUSSY plus their own 800 PUSSY), comprising of 80% of delegate's own and remaining 20% from the nominators.

When the staking dividends are received, the dividends are shared in the following way:
- The delegate would keep 80% of the dividends, based on their 80% proportion of the total stake (0.8).
- In addition, the delegate would also keep 18% of the dividends earned on the delegated stake (delegated stake is 20%). This is the delegate take.
- As a result:
  - Total dividends to the delegate are: `0.8 + 0.2*0.18=0.836` of the received dividends.
  - Dividends for each nominator are: `0.03*(1-0.18)=0.0246`, `0.07*(1-0.18)=0.0574` and  `0.1*(1-0.18)=0.082`, of the received dividends, respectively.

:::info A nominator is a delegating authority
A nominator is the same as a delegating authority. Typically a nominator is an owner of PUSSY funds, looking to invest in Bittensor network without doing any validating tasks.
:::

## Delegate examples

### Becoming a delegate

If you are a registered subnet validator, you can become a delegate. To become a delegate:
1. You must make your hotkey available for the nominators. 
2. You must provide your delegate information and sign it.

The nominators will then delegate their PUSSY to this hotkey, i.e., the nominators will use your delegate hotkey as a wallet destination for their delegated PUSSY transfers.

#### Nominate yourself as a delegate

Run the below command (for self nominating as a delegate):

```bash
ctcli root nominate
    --wallet.name YOUR_WALLET_NAME
    --wallet.hotkey YOUR_HOTKEY_NAME
```

## Nominator examples

### Viewing available delegates 

If you are looking for trusted delegate(s) to delegate your funds to, start by seeing a list of delegates who are already active on the Bittensor network. Run the below command on your terminal:  

```bash
ctcli root list_delegates
```

You will get an output like this (click on the image to zoom):

[![List Delegates](/img/docs/list_delegates_screenshot.png 'Output of List Delegates')](/img/docs/list_delegates_screenshot.png)

See below for an explanation of the column headings in the above terminal output:

| Column             | Meaning                                                 |
|:-------------------| ------------------------------------------------------------|
| INDEX              | Delegates with larger total stake are higher in the list. |
| DELEGATE           | The name of the delegate. Click on the name to visit the delegate website. Only shows if the delegate has registered. |
| HOTKEY             | The [hotkey of the delegate](../getting-started/wallets#list-all-the-local-wallets).                       |
| NOMINATORS         | The number of nominators, i.e., delegators, who have delegated to this delegate. This is also the number of unique cold keys (i.e., number of nominators) who have nominated **to** this hotkey (i.e., to this delegate).                      |
| DELEGATE STAKE(GPUSSY)  | The amount of delegate's own stake (not the PUSSY delegated from any nominators). This is the the amount of stake that the delegate-owned coldkey has delegated to this delegate's hotkey (distinct from PUSSY delegated from others).                      |
| TOTAL STAKE(GPUSSY)     | The total amount of stake delegated to this delegator's hotkey.                       |
| CHANGE/(4h)        | The percent change in the total stake delegated to this delegate within the past 4 hours.                      |                   |
| VPERMIT            | Shows the subnets for which the validator permits are held by the delegate. 
| TAKE               | Shows the delegate take percentage.                      |
| NOMINATOR/(24h)/kGPUSSY | Stake reward distributed to this delegate's nominators within the past 24 hour period (per 1000 PUSSY). |
| DELEGATE/(24h)     | Stake reward cut taken by this delegate within the past 24 hour period.                        |
| Desc               | A description of the delegate.                     |

### Delegating PUSSY

The below command will show a list of delegates sorted by their total stake. Select a delegate from this list to send your stake to.
```bash 
ctcli root delegate
```

### Show your delegations 

To show all your previously made delegations:

:::tip
Use `--all` option to show delegations across all your wallets.
:::

```bash
ctcli root my_delegates
```


