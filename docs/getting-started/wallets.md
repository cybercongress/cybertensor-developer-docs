---
title: "Create Wallet"
---

# Create Wallet

This section describes steps to create a Cybertensor wallet, regenerate keys and encrypt keys. If you are new to Cybertensor wallets, see [Working with Keys](../subnets/working-with-keys.md) for an explanation of Cybertensor wallet keys.

## Ways of creating wallet

You can create a Cybertensor wallet either for basic uses like securely storing your PUSSY and receiving and sending them, or for advanced uses like creating a subnet and participating as a subnet miner or a subnet validator:

- **For basic use**: Create an external wallet account by using the [Chrome Extension for Keplr Wallet](https://wallet.keplr.app/). An external wallet account created in this way will allow you to use PUSSY **without installing Cybertensor**. If your activities are limited to sending or receiving PUSSY then this is a recommended option. 
- **For subnet participation**: Create a local wallet account using `ctcli` command line tool on your computer. This requires that you install Cybertensor on your machine. If you are interested in either creating a subnet or participating as a subnet miner or a subnet validator, then you must use this option. 

## Creating a basic wallet

:::tip Suitable for non-technical users
Use this option if your activities are limited to sending and receiving PUSSY and you are not creating a subnet or participating as a subnet validator or a subnet miner. 
:::

To create a basic wallet account use the Chrome Extension for Keplr Wallet. Follow the below steps:

1. The Wallet will first create a wallet account address in the form of a 48-hexadecimal character string that usually starts with `5`. 
2. Critically, the Wallet will show you a 12-word list arranged in a specific order. You are required to keep this list of words, without changing the word order, in a safe location. This list of ordered words is called by various names such as **mnemonic** or **seed phrase**.
3. The Wallet will then prompt you for specific mnemonic words as a way of authentication.
4. Next, you will assign a name and a password to your wallet account.
5. Finally, to receive PUSSY from another party, you will give them your wallet account address from Step 1 (the 48-hexadecimal character string) as the destination address. Similarly, to send (transfer) PUSSY to another party, you will first ask them for their wallet address and send PUSSY to their wallet address. You can create multiple wallet accounts, each with a different name, and even a different password for each wallet account, this way. 

### Mnemonic

:::danger Always keep your mnemonic safe 
Anyone who knows the mnemonic for your wallet account can access your PUSSY tokens. Hence you must always keep this mnemonic in a safe and secure place, known only to you. More important, if you lose your wallet address, you can use its mnemonic (that you stored away in safekeeping) to restore the wallet. 
:::

:::note Use Import option in Chrome Wallet Extension
To restore your lost coldkey, use the **Import** option in Chrome Extension for Keplr Wallet and provide your 12-word mnemonic.
:::

## Creating a local wallet with CLI

:::tip Suitable for subnet participation
Use this option if you are creating a subnet or participating as a subnet validator or a subnet miner. You must [install Cybertensor](installation.md) for this option.
:::

After you have [installed Cybertensor](installation.md), you can create a local wallet on your machine in the following two ways:

- Using `ctcli`.
- Using Python.

### Coldkey and hotkey

A Cybertensor wallet consists of a **coldkey** and a **hotkey**. Only coldkey is created when you use the [Chrome Extension for Keplr Wallet](https://wallet.keplr.app/). This is sufficient for normal storage and sending and receiving of PUSSY. But to participate in a subnet, you will not only need a local coldkey but also a local hotkey. 

:::tip Explanation of keys 
See [Working with Keys](../subnets/working-with-keys.md) for an explanation of coldkey and hotkey.
:::

### Creating a coldkey using `ctcli` 

If you plan to perform any of the following tasks, you only need to create a coldkey:

- Create a subnet.
- Transfer PUSSY.
- Delegate to a validator-delegate's hotkey.

**However, if you want to validate or mine in a subnet, you will need to create hotkey also**. See the below section [Creating a hotkey using `ctcli`](#creating-a-hotkey-using-ctcli).

Run the following command on your terminal by giving a name to your wallet, replacing the `my_coldkey`. 

```bash
ctcli wallet new_coldkey --wallet.name <my_coldkey>
```

For example, 
```bash
ctcli wallet new_coldkey --wallet.name test-coldkey
```
You will see the following terminal output. The mnemonic is hidden for security reasons.

```text
IMPORTANT: Store this mnemonic in a secure (preferably offline place), as anyone who has possesion of this mnemonic can use it to regenerate the key and access your tokens.
The mnemonic to the new coldkey is:
**** *** **** **** ***** **** *** **** **** **** ***** *****
You can use the mnemonic to recreate the key in case it gets lost. The command to use to regenerate the key using this mnemonic is:
ctcli w regen_coldkey --mnemonic **** *** **** **** ***** **** *** **** **** **** ***** *****
```

:::tip Regenerating the coldkey
Make a note of the above command option `regen_coldkey` showing how to regenerate your coldkey in case you lose it.
:::

### Creating a hotkey using `ctcli` 

If you plan to validate or mine in a subnet, then you must create both a coldkey and a hotkey.

First create a coldkey as described above in the [Creating a coldkey using `ctcli`](#creating-a-coldkey-using-ctcli). Then provide this coldkey as a parameter to generate a hotkey. This will pair the hotkey with the coldkey. See below.

Use the below command to generate the hotkey. Replace `<my_coldkey>` with the coldkey generated above, and `<my_first_hotkey>` with a name for your hotkey.

```bash
ctcli wallet new_hotkey --wallet.name <my_coldkey> --wallet.hotkey <my_first_hotkey>
```

For example, 
```bash
ctcli wallet new_hotkey --wallet.name test-coldkey --wallet.hotkey my_first_hotkey
```

You will see the terminal log like below. The mnemonic is hidden for security reasons.
```text
IMPORTANT: Store this mnemonic in a secure (preferably offline place), as anyone who has possesion of this mnemonic can use it to regenerate the key and access your tokens.
The mnemonic to the new hotkey is:
**** *** **** **** ***** **** *** **** **** **** ***** *****
You can use the mnemonic to recreate the key in case it gets lost. The command to use to regenerate the key using this mnemonic is:
ctcli w regen_hotkey --mnemonic **** *** **** **** ***** **** *** **** **** **** ***** *****
```
:::tip Regenerating the hotkey
Make a note of the above command option `regen_hotkey` showing how to regenerate your hotkey in case you lose it.
:::

### Encrypting the hotkey

By default, the hotkey is not encrypted on the device whereas the coldkey is encrypted. To encrypt your hotkey, run this command:
```bash
ctcli wallet new_hotkey --use_password
```

## Creating a wallet using Python 

Copy and paste the following three lines into your Python interpreter. Replace the string values for `name` (`my_coldkey`) and `hotkey` (`my_first_hotkey`) with your own.

```python showLineNumbers
import cybertensor as ct
wallet = ct.Wallet(name = 'my_coldkey', hotkey = 'my_first_hotkey' )
wallet.create_if_non_existent()
```

You will see a terminal output like this for an example wallet with `name` as `tst1_coldkey` and `hotkey` as `tst1_hotkey`. The mnemonic is hidden for security reasons.
```text 
>>> import cybertensor as ct
>>> wallet = ct.Wallet(name = 'tst1_coldkey', hotkey = 'tst1_hotkey')
>>> wallet.create_if_non_existent()

IMPORTANT: Store this mnemonic in a secure (preferable offline place), as anyone who has possession of this mnemonic can use it to regenerate the key and access your tokens.

The mnemonic to the new coldkey is:

**** **** **** **** **** **** **** **** **** **** **** ****

You can use the mnemonic to recreate the key in case it gets lost. The command to use to regenerate the key using this mnemonic is:
ctcli w regen_coldkey --mnemonic **** **** **** **** **** **** **** **** **** **** **** ****

Specify password for key encryption:
Password not strong enough. Try increasing the length of the password or the password complexity
Specify password for key encryption:
Retype your password:

IMPORTANT: Store this mnemonic in a secure (preferable offline place), as anyone who has possession of this mnemonic can use it to regenerate the key and access your tokens.

The mnemonic to the new hotkey is:

**** **** **** **** **** **** **** **** **** **** **** ****

You can use the mnemonic to recreate the key in case it gets lost. The command to use to regenerate the key using this mnemonic is:
ctcli w regen_hotkey --mnemonic **** **** **** **** **** **** **** **** **** **** **** ****

wallet(tst1_coldkey, tst1_hotkey, ~/.cybertensor/wallets/)
>>>
```

## Location and addresses of the local wallets

Local wallets are stored on your machine under `~/.cybertensor/wallets`. Use the below command to list them:

```bash
tree ~/.cybertensor/
``` 

You will see an output like this:

```bash
tree ~/.cybertensor/
/Users/docwriter/.cybertensor/    # The Cybertensor root directory.
└── wallets # The folder containing all Cybertensor wallets.
    └── test_coldkey # The name of the wallet.
        ├── coldkey # The password-encrypted coldkey.
        ├── coldkeypub.txt # The unencrypted version of the coldkey.
        └── hotkeys # The folder containing all this coldkey's hotkeys.
            └── test_hotkey # The unencrypted hotkey information.
```

and listing out the contents of the `coldkeypub.txt` file:

```bash
cd ~/.Cybertensor/wallets/test_coldkey
cat coldkeypub.txt | jq
{
  "publicKey": "AiYGHyh3VID2aP/OR+H6INI7tIXmk8Ca31gk3JK5RNzV",
  "secretPhrase": null,
  "address": "pussy1vupc3n63fwwrn6wmtwcacx528ezjf8fppc2gc0"
}
```

The contents of the `coldkeypub.txt` are to be interpreted as below:

- The fields `publicKey` contain the same value. 
- The `secretPhrase` is not included in the file due to the high-security nature of the coldkey. When you create your wallet, either using Chrome extension or `ctcli`, the mnemonic (`secretPhrase`) is shown only once while `secretSeed` is not shown. 
- The `address` is the coldkey address. **Send this as your coldkey public wallet address for receiving PUSSY from another party.**

Similarly, listing out the contents of the `hotkeys/test_hotkey` file:

```bash
cat hotkeys/test_hotkey | jq
{
  "publicKey": "A2Dkl4OPo5ifEGHwr3HMTJig/xCcDJ/a4PG4s9SvyErL",
  "secretPhrase": "asset burden point auto lawn hood step guitar anxiety stable alone garbage",
  "address": "pussy18uyf8fmapj8akxtj68h5h340hannew4eu60n9v"
}
```

The contents of the `hotkeys/test_hotkey` file are to be interpreted as below:

- The field `publicKey` contain the same value, just as seen in `coldkeypub.txt`. 
- The `secretPhrase` is shown because the hotkey is by default not encrypted. 
- The `address` is the address of the `accountId`. **Send this as your hotkey public wallet address for receiving PUSSY from another party.** 

## Listing all the local wallets

You can list all the local wallets stored in Cybertensor's root directly with:
```bash
ctcli wallet list
```
You will see a terminal output like this:
```text
Wallets
└─
    test_coldkey (pussy1vupc3n63fwwrn6wmtwcacx528ezjf8fppc2gc0)
       └── test_hotkey (pussy18uyf8fmapj8akxtj68h5h340hannew4eu60n9v)
```

The output will show only the `address` field values from the `coldkeypub.txt` and `tst1_hotkey` files of the wallets. 

:::tip Use the address keys as destinations for PUSSY
Use the above shown `address` field values as your public wallet addresses, i.e., as destinations for PUSSY transfers from another wallet to your wallet. For example, when using a command: `ctcli wallet transfer`.
:::

## Store your mnemonics safely

:::danger If someone has your mnemonic, they own your PUSSY 
If you lose the password to your wallet, or if you have lost the access to the machine where the wallet is stored, you can regenerate the coldkey using the mnemonic you saved during wallet creation steps above. You can **not** retrieve the wallet with the password alone. Remember that if someone has your mnemonic, they own your PUSSY. 
:::

As a reminder, if you need to regenerate your wallets, you can use the `ctcli` with your mnemonic, as shown below:

```bash
ctcli wallet regen_coldkey --mnemonic **** *** **** **** ***** **** *** **** **** **** ***** *****
```

<!-- move this section to somewhere else
## ct.Wallet 

<Accordion title="(examples)">

```python dark
import cybertensor as ct

# Creating a default wallet coldkey = default, hotkey = default, path = ~/.cybertensor/wallets
wallet = ct.Wallet()

# Create wallet by parsing --wallet.name, --wallet.hotkey and --wallet.path from the command line.
wallet = ct.Wallet( config = ct.wallet.config() )

# Create wallet by explicitly setting names of coldkey, hotkey and path.
wallet = ct.Wallet( name = 'my_coldkey', hotkey = 'my_first_hotkey', path = '~/path/to/wallets/dir' )
```


</Accordion>

<Accordion title="(methods)">


#### create_coldkey_from_uri
```python
create_coldkey_from_uri(self, uri:str, use_password: bool = True, overwrite:bool = False) -> 'Wallet'
```
Creates coldkey from suri string, optionally encrypts it with the user's inputed password.


#### create_hotkey_from_uri
```python
create_hotkey_from_uri( self, uri:str, use_password: bool = False, overwrite:bool = False) -> 'Wallet'
```
Creates hotkey from suri string, optionally encrypts it with the user's inputed password.


#### new_coldkey
```python
new_coldkey( self, n_words:int = 12, use_password: bool = True, overwrite:bool = False) -> 'Wallet'
```
Creates a new coldkey, optionally encrypts it with the user's inputed password and saves to disk.


#### create_new_coldkey
```python
create_new_coldkey( self, n_words:int = 12, use_password: bool = True, overwrite:bool = False) -> 'Wallet'
```
Creates a new coldkey, optionally encrypts it with the user's inputed password and saves to disk.


#### new_hotkey
```python
new_hotkey( self, n_words:int = 12, use_password: bool = False, overwrite:bool = False) -> 'Wallet'
```
Creates a new hotkey, optionally encrypts it with the user's inputed password and saves to disk.


#### create_new_hotkey
```python
create_new_hotkey( self, n_words:int = 12, use_password: bool = False, overwrite:bool = False) -> 'Wallet'
```
Creates a new hotkey, optionally encrypts it with the user's inputed password and saves to disk.


#### regenerate_coldkeypub
```python
regenerate_coldkeypub( self, address: Optional[str] = None, public_key: Optional[Union[str, bytes]] = None, overwrite: bool = False ) -> 'Wallet'
```
Regenerates the coldkeypub from passed address or public_key and saves the file


#### regenerate_coldkey
```python
regenerate_coldkey(self, use_password: bool = True, overwrite: bool = False, **kwargs) -> 'Wallet'
```
Regenerates the coldkey from passed mnemonic, seed, or json encrypts it with the user's password and saves the file.


#### regenerate_hotkey
```python
regenerate_hotkey(self, use_password: bool = True, overwrite: bool = False, **kwargs) -> 'Wallet'
```
Regenerates the hotkey from passed mnemonic, seed, or json encrypts it with the user's password and saves the file.


#### __str__
```python
__str__(self)
```
Returns a string representation of the Wallet.


#### __repr__
```python
__repr__(self)
```
Returns the same string representation as `__str__`.


#### create_if_non_existent
```python
create_if_non_existent(self, coldkey_use_password:bool = True, hotkey_use_password:bool = False) -> 'Wallet'
```
Creates coldkeypub and hotkeys if they don't exist.


 
#### create
```python
create(self, coldkey_use_password:bool = True, hotkey_use_password:bool = False) -> 'Wallet'
```
Similar to `create_if_non_existent`, creates coldkeypub and hotkeys if they don't exist.

#### recreate
```python
recreate(self, coldkey_use_password:bool = True, hotkey_use_password:bool = False ) -> 'Wallet'
```
Creates new coldkeypub and hotkeys, overwriting existing ones.

#### set_hotkey, set_coldkeypub, set_coldkey
```python
set_hotkey(self, keypair: 'cybertensor.Keypair', encrypt: bool = False, overwrite: bool = False) -> 'cybertensor.Keyfile'
set_coldkeypub(self, keypair: 'cybertensor.Keypair', encrypt: bool = False, overwrite: bool = False) -> 'cybertensor.Keyfile'
set_coldkey(self, keypair: 'cybertensor.Keypair', encrypt: bool = True, overwrite: bool = False) -> 'cybertensor.Keyfile'
```
Sets the hotkey, coldkeypub, and coldkey, respectively. Each can optionally be encrypted and overwritten.


#### get_coldkey, get_hotkey, get_coldkeypub
```python
get_coldkey(self, password: str = None ) -> 'cybertensor.Keypair'
get_hotkey(self, password: str = None ) -> 'cybertensor.Keypair'
get_coldkeypub(self, password: str = None ) -> 'cybertensor.Keypair'
```
Returns the coldkey, hotkey, and coldkeypub, respectively. If encrypted, requires a password.


#### create_coldkey_from_uri
```python
create_coldkey_from_uri(self, uri:str, use_password: bool = True, overwrite:bool = False) -> 'Wallet'
```
Creates a coldkey from a suri string. Optionally encrypts and overwrites existing coldkey.


</Accordion>
-->

## Updating legacy wallet

It is important that you update any legacy Cybertensor wallets to the new NaCL format for security. You may accomplish this with the `ctcli` using the `wallet update` subcommands.

See the below example command and the terminal output:
```bash
ctcli wallet update
>> Do you want to update all legacy wallets? [y/n]: n
>> =====  wallet(tst1_coldkey, default, ~/.cybertensor/wallets/)  =====
>> ✅ Keyfile is updated. 
>> 🔑 Keyfile (NaCl encrypted, ~/.cybertensor/wallets/tst1_coldkey/coldkey)>
```
