---
title: "Cybertensor CLI"
---

# Cybertensor CLI

After you [install Cybertensor](/getting-started/installation.md) you can use `ctcli` command line interface (CLI) to stake or unstake funds, run miners, check network state, and even deploy, analyze, and interface with the Cybertensor network. This section presents the command and subcommand options available in `ctcli` CLI.

## Usage

```bash
ctcli [COMMAND]
usage: ctcli <command> <command args>
positional arguments:
  {subnets,s,subnet,root,r,roots,wallet,w,wallets,stake,st,stakes,sudo,su,sudos}
    subnets (s, subnet)
                        Commands for managing and viewing subnetworks.
    root (r, roots)     Commands for managing and viewing the root network.
    wallet (w, wallets)
                        Commands for managing and viewing wallets.
    stake (st, stakes)  Commands for staking and removing stake from hotkey accounts.
    sudo (su, sudos)    Commands for subnet management

optional arguments:
  -h, --help            show this help message and exit
  --print-completion {bash,zsh,tcsh}
                        Print shell tab completion script
```
---

## Wallets 

### Show overview

```bash
ctcli wallet overview [OPTIONS]
```

Displays comprehensive information about each neuron associated with the user's wallets, including both hotkeys and coldkeys. It is especially useful for users managing multiple accounts or looking for a summary of their network activities and stake distributions.

#### Example

```bash
ctcli wallet overview
```

With example options:

```bash
ctcli wallet overview --all --sort_by stake --sort_order descending
```

Run,
```bash
ctcli wallet overview --help
```
for full options.


### List wallets

```bash
ctcli wallet list [OPTIONS]
```


- Lists all wallets locally stored on your machine under path `--wallet.path`. 
- Required as destinations for ```ctcli transfer```

```bash 
ctcli wallet list
Wallets
└─
    my_wallet (pussy1...)
       └── my_first_hotkey (pussy1...)
```

### Check balance in all wallets

```bash
ctcli wallet balance --all
```

Lists the balances in all the wallets in the user's configuration directory, showing the wallet name, coldkey address, and the free and staked balances.

### Check balance in a single wallet

```bash
ctcli w balance --wallet.name WALLET
```

or you can specify the wallet's name in the terminal prompt:

```bash
ctcli w balance
```

### New coldkey

```bash
ctcli wallet new_coldkey [OPTIONS]
```

Create a new wallet with encrypted coldkey:

```bash
ctcli wallet new_coldkey
```

### New hotkey

```bash
ctcli wallet new_hotkey [OPTIONS]
```

Create a hotkey associated with a wallet:

```bash
ctcli wallet new_hotkey
```

### Regenerate hotkey

```bash
ctcli wallet regen_hotkey [OPTIONS]
```

Regenerate a hotkey from mnemonic:
```bash
ctcli wallet regen_hotkey
```

### Regenerate coldkey

```bash
ctcli wallet regen_coldkey [OPTIONS]
```
Regenerate a wallet encrypted coldkey file from mnemonic or seed:

```bash
ctcli wallet regen_coldkey
```

### Regenerate coldkeypub

```bash
ctcli wallet regen_coldkeypub [OPTIONS]
```

Regenerate a wallet with just the public seed of your coldkey:

```bash
ctcli wallet regen_coldkeypub
```

## Subnets

### List subnets

Lists the existing subnets and shows their detailed information. In addition to the subnet details, the command fetches delegate information and provides the name of the subnet owner where available. If the owner's name is not available, the owner's address is displayed.

Defaults to subnets on the mainchain. 

```bash
ctcli subnets list [OPTIONS]
```

Use,

```bash
ctcli subnets list --help
```

to see the available OPTIONS.

### Show lock cost

Shows the locking cost required for creating a new subnet on the Cybertensor network. This command is designed to provide users with the current cost of registering a new subnet. If the cost is unappealing currently, check back in a day or two to see if it has improved.

```bash
ctcli subnets lock_cost [OPTIONS]
```

Use,

```bash
ctcli subnets lock_cost --help
```

to see the available OPTIONS.

### Create subnet

:::tip For advanced users only
This command is intended for advanced users of the Cybertensor network who wish to contribute by adding new subnets. It requires a clear understanding of the Cybertensor network's functioning and the roles of subnets. Users should ensure that they have secured their wallet and are aware of the implications of adding a new subnetwork to the Cybertensor ecosystem.
:::

Creates and registers a new subnet. This involves interaction with the user's wallet and the Cybertensor contract. It ensures that the user has the necessary credentials and configurations to successfully register a new subnet.

```bash
ctcli subnets create [OPTIONS]
```

Use,

```bash
ctcli subnets create --help
```

to see the available OPTIONS.


### Register

```bash

ctcli subnets register [OPTIONS]
```

Registers a new neuron using the `recycle_register` option. Adds a new neuron to the specified subnet `--netuid`.

:::caution alert
The command option `recycle_register` is removed. Instead, use the above `register` option.
:::

To register in a subnet of `netuid` of `1`:

```bash

ctcli subnets register --netuid 1
```

Use,

```bash
ctcli subnets register --help
```

to see the available OPTIONS.

### PoW registration

```bash
ctcli subnets pow_register [OPTIONS]
```

Registers a neuron on the Cybertensor network using Proof of Work (PoW). This method is an alternative registration process that leverages computational work for securing a neuron's place on the network.

Example:

```bash
ctcli subnets pow_register --netuid 1 --pow_register.num_processes 4 --cuda.use_cuda
```

Use,

```bash
ctcli subnets pow_register --help
```

to see the available OPTIONS.

:::caution
This command is for users with adequate computational resources to participate in PoW registration. It requires a sound understanding of the network's operations and PoW mechanics. Users should ensure their systems meet the necessary hardware and software requirements, particularly when opting for CUDA-based GPU acceleration.
:::

### Show metagraph

Shows the metagraph of the desired subnet. Defaults to subnets on the mainchain. 

```bash
ctcli subnets metagraph [OPTIONS]
```

Use,

```bash
ctcli subnets metagraph --help
```

to see the available OPTIONS.

### Show hyperparameters

Shows the current hyperparameters for the desired subnet. This command is useful for users who wish to understand the configuration and operational parameters of a particular subnet.

```bash
ctcli subnets hyperparameters [OPTIONS]
```

Use,

```bash
ctcli subnets hyperparameters --help
```

to see the available OPTIONS.

---

## Transfers and staking 

### Transfer

```bash
ctcli wallet transfer [OPTIONS]
```

- Transfers PUSSY from a wallet coldkey to another wallet public key address.

```bash
ctcli wallet transfer
```

### Stake 

```bash
ctcli stake add [OPTIONS]
```

Stake PUSSY from the coldkey balance to the hotkey staking account.

```bash
ctcli stake add
```

### Unstake


```bash
ctcli stake remove [OPTIONS]
```

Remove stake PUSSY from the hotkey staking account and add it to the coldkey.

```bash
ctcli stake remove
```

---

## Delegation

### See available delegates

```bash
ctcli root list_delegates
```

List all active delegates available for delegated PUSSY. Displays the below output:

[![List Delegates](/img/docs/list_delegates_screenshot.png 'Output of List Delegates')](/img/docs/list_delegates_screenshot.png)


### Delegate

```bash
ctcli root delegate [OPTIONS]
```

Delegate PUSSY from the coldkey balance to the hotkey staking account of a delegate.

```bash
ctcli root delegate
```

### Set delegate take

```bash
ctcli root set_delegate_take [OPTIONS]
```
Sets the take percentage of the delegate.

To set the delegate take at 10%:

```bash
ctcli root set_delegate_take --take 0.1
```

The `--take` value must be a floating point number between `0` and `1`.

To use a specific wallet:

```bash
ctcli root set_delegate_take --wallet.name my_wallet --wallet.hotkey my_hotkey --take 0.1
```

### Undelegate

```bash
ctcli root undelegate [OPTIONS]
```
Remove PUSSY from the hotkey balance of delegate you have previously delegated to.

```bash
ctcli root undelegate
```

### My delegates

```bash
ctcli root my_delegates
```

Show all your previously made delegations.

:::tip
Use `--all` option to show delegations across all your wallets.
:::

---

## Root network

### Root network list

```bash
ctcli root list
```

Lists all the root network members. Shows the top 64 validators in the root network.


### Root register

```bash
ctcli root register [OPTIONS]
```

Elect to join the root subnet with your nominated hotkey.

```bash dark
ctcli root register
```
