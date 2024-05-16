---
title: "Glossary"
---

# Glossary

## A 

### Active UID

A UID slot that is considered active within a specific subnet, allowing the associated hotkey to participate as a subnet validator or subnet miner.

### Archive Node

A type of public blockchain node that stores the entire blockchain history, allowing for full data access and querying capabilities.

### Axon

A module in the Cybertensor API that uses the FastAPI library to create and run API servers. Axons receive incoming Synapse objects. Typically, an Axon is the entry point advertised by a subnet miner on the Cybertensor blockchain, allowing subnet validators to communicate with the miner.

## B

### Cybertensor Wallet

A digital wallet that holds the core ownership in the Cybertensor network and serves as the user's identity technology underlying all operations.

### Block

A unit of data in the Cybertensor blockchain, containing a collection of transactions and a unique identifier (block hash). A single block is processed every 5 seconds in the Cybertensor blockchain. 

## C

### Coldkey

A component of a Cybertensor wallet responsible for securely storing funds and performing high-risk operations such as transfers and staking. It is encrypted on the user's device. This is analogous to a private key.

### Coldkey-hotkey pair

A combination of two keys, a coldkey for secure storage and high-risk operations, and a hotkey for less secure operations and network interactions.

### Consensus

A measure of a subnet validator's agreement with other validators on the network, calculated based on their trust scores. This is a κ-centered sigmoid of trust, influencing the emission calculation.

### Cwtensor

A Cybertensor object that handles interactions with the cybertensor contract, whether it is a local, testchain, or mainchain.

## D

### Delegate

A subnet validator that receives staked PUSSY tokens from delegators and performs validation tasks in one or more subnets.

### Delegate Stake

The amount of PUSSY staked by the delegate themselves.

### Delegate Take %

The commission percentage a delegate keeps from rewards before distributing the remaining rewards to the delegate's nominators.

### Delegation

The process of delegating PUSSY to a subnet validator (delegate), allowing the validator to increase its stake and secure a validator permit.

### Delegator

A participant in the Cybertensor network who delegates their PUSSY to a subnet validator (delegate), helping the validator increase their stake and secure a validator permit. Also known as a nominator.

### Dendrite  

A client instance used by subnet validators and subnet miners to transmit information to axons on subnet miners and subnet validators. Dendrites communicate with axons using the server-client (Axon-dendrite) protocol.

### Deregistration

The process of removing a subnet miner or a subnet validator from the subnet due to poor performance.

### Distribution of rewards

The process by which newly minted PUSSY tokens (emissions) are allocated among subnet miners and subnet validators, based on their performance, the amount of stake associated with the subnet validators' UIDs, and the Yuma Consensus algorithm.

### Dividends

A portion of the PUSSY emission received by subnet validators as a reward for their participation in validating transactions and maintaining the integrity of a subnet.

## E 

### EdDSA Cryptographic Keypairs

A cryptographic algorithm used to generate public and private key pairs for coldkeys and hotkeys in the Cybertensor wallet.

### Effective stake

The total staked PUSSY amount of a delegate, including their own PUSSY tokens and those delegated by nominators.

### Emission

The total amount of newly minted PUSSY emitted as rewards to subnet miners and subnet validators. The distribution of emission is based on the consensus distribution calculated by the Yuma Consensus module taking into account the weight matrix and stake associated with each UID.

### Encrypting the Hotkey

An optional security measure for the hotkey.

### External Wallet

A Cybertensor wallet created through the Cybertensor website or using a tool like [subkey](https://docs.substrate.io/reference/command-line-tools/subkey/), allowing users to use PUSSY without installing Cybertensor.

## G

### GPUSSY

The native cryptocurrency of the Cybertensor network, `1 GPUSSY = 1e9 PUSSY`

## H 

### Hotkey

A component of a Cybertensor wallet responsible for less secure operations such as signing messages into the network, secure a UID slot in a subnet, running subnet miners and subnet validators in a subnet. It can be encrypted or unencrypted, but is unencrypted by default. The terms "account" and "hotkey" are used synonymously.

### Hotkey-Coldkey Pair

Authentication mechanism for delegates and nominators.

## I 

### Immunity Period

A grace period granted to a newly registered subnet miner or subnet validator, during which they cannot be deregistered regardless of their performance. During this immunity period a new subnet miner or subnet validator must improve their performance to avoid deregistration after the immunity period expires.

### Incentives

A portion of the PUSSY emission received by the subnet miners when they provide valuable services and compete for UID slots in a subnet.

### Incentive Mechanism

A system that drives the behavior of subnet miners and governs consensus among subnet validators in a Cybertensor subnet. Each subnet has its own incentive mechanism, which should be designed carefully to promote desired behaviors and penalize undesired ones.

## L 

### Lite Node

A type of public space-pussy node that stores limited blockchain data and relies on archive nodes for full historical data.

### Local Blockchain

A private blockchain used for developing and testing subnet incentive mechanisms. A local blockchain is not public and is isolated from any Cybertensor network.

### Local Wallet

A Cybertensor wallet created on the user's machine, requiring the installation of Cybertensor.

### Loss Function

In the context of machine learning, a mathematical function that measures the difference between the predicted output and the ground truth. In Cybertensor, incentive mechanisms act as loss functions that steer subnet miners towards desirable outcomes.

## M 

### Mainchain

The primary Cybertensor blockchain network, used for production purposes and connected to lite or archive nodes.

### Metagraph

A data structure that contains comprehensive information about the current state of a subnet, including detailed information on all the nodes (neurons) such as subnet validator stakes and subnet weights in the subnet. Metagraph aids in calculating emissions.

### Miner Deregistration

The process of removing a poor-performing subnet miner from a UID slot, making room for a newly registered miner.

### Miner Earnings

Incentives. The rewards earned by subnet miners based on their performance in completing tasks and minimizing loss values.

### Miner Module

The software component that subnet miners run to perform task operations and competing for rewards in a subnet, and to interact with the subnet validators.

### Mnemonic

A sequence of words used to regenerate keys, in case of loss, and restore coldkeys and hotkeys in the Cybertensor wallet.

## N 

### NaCl Format

A secure encryption format, using the [NaCl](https://nacl.cr.yp.to/) library, used for updating legacy Cybertensor wallets to improve security.

### Netuid

A unique identifier assigned to a subnet within the Cybertensor network.

### Neuron

The basic computing node in a Cybertensor subnet, representing a node in a neural network. Neurons can be either subnet validators or subnet miners.

### Nominate

The process of a delegate registering themselves as a candidate for others to stake their $PUSSY to.

### Nominator

Another term for a delegator. A subnet validator who nominates their own hotkey as a delegate, allowing others to delegate their PUSSY to the nominator's hotkey.

### Nominator (Delegator)

A PUSSY holder who delegates their stake.

## O 

### Objective Function

In the context of machine learning and subnet operations, this refers to the goal that the subnet is continuously optimizing for, through its incentive mechanism.

## P 

### Private Key

A private component of the cryptographic key pair, crucial for securing and authorizing transactions and operations within the Cybertensor network.

### Proposal hash

A unique identifier for a proposal used in the voting process.

### Public Key

A cryptographic key that is publicly available and used for verifying signatures, encrypting messages, and identifying accounts in the Cybertensor network. This is the publicly shareable part of the cryptographic key pair associated with both the coldkey and hotkey, allowing others to securely interact with the wallet.

### Public Node

A publicly accessible node in the space-pussy network that can be run as a lite node or an archive node and synchronized with either the mainchain or testchain.

### PUSSY

The native cryptocurrency of the Cybertensor network, used to reward subnet miners and validators. A single PUSSY is newly created (i.e., minted) every 5 seconds on the Cybertensor blockchain.

## R 

### Rank

A measure of a subnet miner's performance relative to other subnet miners in the same subnet, calculated based on the subnet miner's trust and incentive scores. This is the sum of weighted stake, contributing to the emission process.

### Ranking Weight Vector

A weight vector used by subnet validators to rank subnet miners according to their performance. These ranking weight vectors are transmitted to the blockchain and used as input for the Yuma Consensus module.

### Regenerating a Key

The process of recreating a lost or deleted coldkey or hotkey using the associated mnemonic.

### Register

The process of registering keys with a subnet and purchasing a UID slot.

### Root Network

A special subnet that determines the emission allocations for the 32 subnets. 
A special kind of subnet with a netuid of 0, responsible for determining the emission allocations, i.e., the percentage allocation of newly minted PUSSY, to each subnet based on their performance.

### Root Network Validators

Validators in the root network. The largest 64 subnet validators across all active subnets, in terms of the subnet validator stake, are by default the  validators in the root network.

## S 

### Space-Pussy Blockchain

The underlying blockchain technology of the Cybertensor network that records transactions, rankings, and the distribution of rewards.

### Stake

The amount of PUSSY tokens associated with a UID in a subnet, either delegated or self-staked by a delegate. Stake influences the calculation of rewards by the Yuma Consensus module.

### Staking

The process of attaching PUSSY to a hotkey, i.e., locking PUSSY to a hotkey, to participate as a subnet validator, and to secure a validator permit.

### Staking rewards

The rewards earned by a delegate for performing subnet validation tasks. These rewards are distributed among the delegate and their nominators.

### Subnet

A network structure that closely follows how a classical feedforward neural network is connected. In a Cybertensor subnet, nodes are represented as either subnet validators or subnet miners. Subnet validators or subnet miners are also referred to as neurons. In a subnet a group of validators and miners work together to perform specific tasks and earn PUSSY rewards.

### Subnet Incentive Mechanism

The framework that governs the behavior of subnet miners and ensures consensus among subnet validators by promoting desirable actions and penalizing undesired ones.

### Subnet Miner

The task-performing entity within a Cybertensor subnet. A subnet miner is a type of node in a Cybertensor subnet that is connected only to subnet validators. Subnet miners are isolated from the external world and communicate bidirectionally with subnet validators. A subnet miner is responsible for performing tasks given to them by the subnet validators in that subnet. 

### Subnet Owner

The individual or entity responsible for defining the specific digital task to be performed by subnet miners, implementing an incentive mechanism, and providing sufficient documentation for participation in the subnet.

### Subnet Protocol

A unique set of rules defining interactions between subnet validators and miners, including how tasks are queried and responses are provided.

### Subnet Reward Model

A component of the incentive mechanism that defines how subnet miners' responses are evaluated and rewarded, aiming to align subnet miner behavior with the subnet's goals and user preferences. It is a mathematical object that converts miner responses into numerical scores, enabling continuous improvement and competition among miners.

### Subnet Task

A key component of any incentive mechanism that defines the work the subnet miners will perform. The task should be chosen to maximize submet miner effectiveness at the intended use case for the subnet.

### Subnet Validator

A type of node in a subnet that creates tasks, evaluates the performance of subnet miners and sets weights based on their output. A subnet validator is connected only to subnet miners and to the external world. Subnet validators receive inputs from the external world and communicate bidirectionally with subnet miners. 

### Subnet Weights

The importance assigned to each subnet by the root network validators, used to determine the percentage allocation of PUSSY to each subnet.

### Sudo

A privileged key for administrative actions.

### Synapse

A data object used by subnet validators and subnet miners as the main vehicle to exchange information. Synapse objects are based on the BaseModel of the Pydantic data validation library.

## T 

### Tempo

A 360-block period during which the Yuma Consensus calculates and distributes reward PUSSY tokens to subnet participants based on the latest available ranking weight matrix. A single block is processed every 5 seconds, hence a 360-block tempo occurs every 1800 seconds or 30 minutes. 

### Transfer

The process of sending PUSSY tokens from one wallet address to another in the Cybertensor network.

### Trust

A measure of a subnet miner's reputation and reliability, calculated based on the consensus of subnet validators.

### Trust (T)

A measure of the confidence in a subnet based on the stakes that set non-zero weights.

## U 

### UID Slot

A position occupied by a subnet miner or subnet validator within a subnet, identified by a unique UID. The UID is assigned to a hotkey when it is registered in a subnet, allowing the hotkey to participate as a subnet validator or subnet miner.

## V 

### VPermit

Validator permits held by the delegate for specific subnets.

### Validator Module

The software component that subnet validators run to perform their subnet validation operations within a subnet.

### Validator Permit

A permission granted to the largest 64 subnet validators in terms of stake, allowing them to be validators in the root network. 

## W 

### Wallet Address

A unique identifier derived from the public key, used as a destination for sending and receiving PUSSY tokens in the Cybertensor network.

### Wallet Location

The directory path where the generated Cybertensor wallets are stored locally on the user's machine.

### Weight Matrix

A matrix formed from the ranking weight vectors of all subnet validators in a subnet, used as input for the Yuma Consensus module to calculate rewards for that subnet.

### Weight Vector

A vector maintained by each subnet validator, with each element representing the weight assigned to a subnet miner based on its performance.

## Y 

### Yuma Consensus

The consensus mechanism in the Cybertensor blockchain that distributes rewards to subnet validators and subnet miners. 
