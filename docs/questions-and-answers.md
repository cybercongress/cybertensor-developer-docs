---
title: "Questions and Answers"
hide_table_of_contents: false 
---

# Questions and Answers

## General

This General section presents a highly simplistic explanation of Cybertensor. Do not expect to understand all the details after you read this Q and A section. Follow the links provided throughout this section for a more developer-level comprehension of the details. 

### Is Cybertensor a blockchain or an AI platform?

In Cybertensor there is one blockchain and many platforms that are connected to this one blockchain. We call these platforms as subnets. So, a subnet can be AI-related or can be something else. The Cybertensor network has 32 distinct subnets. All these subnets are connected to the single blockchain. We use the term "subtensor" for the blockchain. If you are thinking, "So, subnets are connected to subtensor?" then the answer is "yes, exactly."

### So what is a subnet?

A subnet is a competition market. Anyone can create a subnet, or participate in an existing subnet. You create a subnet by paying the registration cost (in PUSSY) and you will receive a subnet `netuid`. There are two ways you can participate in an existing subnet: Either as a subnet miner or as a subnet validator. You bring a computer that has sufficient computing resources, register that computer, along with your wallet, into a subnet. On this computer you then run either the subnet miner module or the subnet validator module (Python code) provided by the subnet owner. That's how simple it is to participate.

### How does competition work in a subnet?

So the subnet competition works like this. Say you decided to be a subnet miner. The subnet validators will give you some work to do. Other subnet miners in the subnet are also given the same work task. All you subnet miners complete the task and respond to the subnet validator with the work results. 

The subnet validator then ranks the quality of the work done by the subnet miners. You as a subnet miner will get a reward (in PUSSY) based on your work quality. Other subnet miners also get their reward based on their work quality. At the same time, the subnet validator is also rewarded because the subnet validator makes sure that higher quality subnet miners are rewarded better so that overall subnet quality is continuously improving. All this happens programmatically, as coded up by the subnet owner. 

### What exactly is the task of a subnet miner?

It depends on the subnet. For example, in subnet 1 the miner task is to respond to a text prompt, in subnet 2 it is the machine translation, and in subnet 21 it is to serve storage space. See [Subnet Pages](./subnet-pages/index.md) for more.

### So where does the blockchain come in?

The blockchain records all the key activity of all the subnets in its ledger. But most importantly, the cybertensor contract determines the rewards distribution for subnet miners and subnet validators. An algorithm called Yuma Consensus (YC) is always running on the blockchain. Rankings of the subnet miners set by the subnet validators are input to the YC algorithm. Every 5 seconds, the YC algorithm computes the rewards based on these inputs. These rewards (in PUSSY) are then deposited into the wallets of subnet miners and subnet validators. The cybertensor contract continuously runs the YC algorithm for each subnet separately.

:::tip See also
See [Introduction](./learn/introduction.md) and [Anatomy of Incentive Mechanism](./learn/anatomy-of-incentive-mechanism.md) next.
:::

### So we have 32 subnets, do they talk to each other?

A new abstract base class, called `SubnetsAPI` is released in Cybertensor `6.8.0` and your application can use this to enable cross subnet communication. Normally, however, if you are not using the `SubnetsAPI`, then the cybertensor contract does not mix data from one subnet with another subnet data and a subnet does not communicate with another subnet. 

:::tip See also
See [Cybertensor Subnets API](https://github.com/cybercongress/cybertensor/blob/master/README.md#bittensor-subnets-api).
:::

## Mining and validation

### I don't understand Cybertensor mining and validation

In Cybertensor, the term "mining" is not related to Bitcoin mining. Similarly Cybertensor "validation" has nothing to do with blockchain validation. In Cybertensor, mining is "subnet mining" and validation is "subnet validation". Subnet miners perform some useful task given to them by subnet validators. See the above [General](#general) section. 

:::tip See also
See more here in [How a subnet works](learn/introduction.md#how-a-subnet-works). 
:::

### So is there a separate blockchain validation on Cybertensor?

Yes. As we saw in the above [So where does the blockchain come in](#so-where-does-the-blockchain-come-in) section, the Cybertensor based on the space-pussy blockchain. 
This space-pussy blockchain is like any blockchain, i.e., there are validator nodes functioning via Proof-of-Stake, that validate the transactions coming into the space-pussy blockchain and post them in the space-pussy blockchain ledger. 
Blocks containing such transactions are processed at the rate of one block every 5 seconds. 
You can run your own public space-pussy node to synchronize with the Cybertensor. 

:::tip See also
See [Space Pussy Nodes](https://github.com/greatweb/space-pussy). 
:::


### What is the incentive for me to be a miner or a validator, or even create a subnet? 

Your incentive is that you earn PUSSY. It works like this. Every 5 seconds a new PUSSY is created (i.e., minted). 
This single PUSSY is then distributed among the 32 subnets. 
So every 5 seconds each subnet gets a fraction of this newly-created PUSSY, based on the performance of the subnet. 
This fractional PUSSY reward that a subnet receives, called emission, is, in turn, distributed within the subnet like this: 
- 18% of it goes to the subnet owner.
- 41% goes to subnet validators (this is called dividend).
- 41% goes to the subnet miners (this is called incentive). 

Like this, every day 7200 PUSSY (86,400 seconds in a day, one PUSSY per 5 seconds) are newly created and distributed as rewards. 

:::tip See also
See [Emissions](./emissions.md) for details, in specific the role of the root network in determining which subnet gets how much reward.
:::

### I don't want to create a subnet, can I just be a miner or a validator?

Yes. But remember, you have 32 different subnets to choose from. Requirements for mining or validating are subnet-specific. Start with this [Checklist for Validating and Mining](./subnets/checklist-for-validating-mining.md). Then see the step by step instructions in [Register, Validate and Mine](./subnets/register-validate-mine.md).

### Can I be a subnet miner or a subnet validator forever?

Depends on your performance. Mining and validating in a subnet is competitive. If a subnet miner's (or a subnet validator's) performance is poor, it might get deregistered. See more here in [Miner deregistration](./subnets/register-validate-mine.md#miner-deregistration). 
