---
title: "Install Cybertensor"
---

# Install Cybertensor

Before you can start developing, you must install Cybertensor and then create Cybertensor wallet.

## Upgrade

If you already installed Cybertensor, make sure you upgrade to the latest version. Run the below command:

```bash
python3 -m pip install --upgrade cybertensor
```

or
```bash
python -m pip install --upgrade cybertensor
```

## Install on macOS and Linux

You can install Cybertensor on your local machine in either of the following ways. **Make sure you verify your installation after you install**:
- Using `pip3 install`.
- From source.

### Using `pip3 install`

```bash
pip3 install cybertensor
```

### From source

1. Clone the Cybertensor repo

    ```bash
    git clone https://github.com/cybercongress/cybertensor.git
    ```
2. We recommend you first activate a Python virtual environment
   ```bash
   cd cybertensor
   python3 -m venv venv
   . venv/bin/activate
   ```
3. Install with `python3`

    ```bash
    python3 -m pip install -e .
    ```

## Install on Windows

To install and run Cybertensor on Windows you must install [**WSL 2** (Windows Subsystem for Linux)](https://learn.microsoft.com/en-us/windows/wsl/about) on Windows and select [Ubuntu Linux distribution](https://github.com/ubuntu/WSL/blob/main/docs/guides/install-ubuntu-wsl2.md). 

After you installed the above, follow the same installation steps described above in [Install on macOS and Linux](#install-on-macos-and-linux).

:::danger Limited support on Windows
While wallet transactions like delegating, transfer, registering, staking can be performed on a Windows machine using WSL 2, the mining and validating operations are not recommended and are not supported on Windows machines.
 :::


## Verify the installation

You can verify your installation in either of the two ways as shown below:

### Verify using the `ctcli` command

Using the [Cybertensor Command Line Interface](/ctcli.md).

```bash
ctcli --help
```
which will give you the below output:

```text
usage: ctcli <command> <command args>

cybertensor cli <version number>

positional arguments:
...
```
You will see the version number you installed in place of `<version number>`. 

### Verify using Python interpreter

1. Launch the Python interpreter on your terminal.   

    ```bash
    python3
    ```
2. Enter the following two lines in the Python interpreter.
   
   ```python
    import cybertensor as ct
    print( ct.__version__ )
    ```
    The Python interpreter output will look like below:

    ```python
    Python 3.11.6 (main, Oct  2 2023, 13:45:54) [Clang 15.0.0 (clang-1500.0.40.1)] on darwin
    Type "help", "copyright", "credits" or "license" for more information.
    >>> import cybertensor as ct
    >>> print( ct.__version__ )
    <version number>
    ```
You will see the version number you installed in place of `<version number>`. 
### Verify by listing axon information

You can also verify the Cybertensor installation by listing the axon information for the neurons. Enter the following lines in the Python interpreter.

```python
>>> import cybertensor as ct
>>> metagraph = ct.metagraph(netuid=1, network='space-pussy')
>>> metagraph.axons[:10]
```
The Python interpreter output will look like below.

```bash
[AxonInfo( /ipv4/103.100.175.167:8091, pussy1ygxx9zslqjjcwmcd8wgejrue4vnz49k7fuzhku, pussy19nq6hgr8vl9x5tasymjl7hp2uqstl0mxjsq6x3, 17 ),
 AxonInfo( /ipv4/103.100.175.255:8091, pussy1n423wpcennjyjuvgkvlyhppgjd9lwrqfusqmgu, pussy18vctec6t9p4zt4k8u9j6g6ed7tnf4230h8c7a9, 17 )
 ...]
>>>
```

