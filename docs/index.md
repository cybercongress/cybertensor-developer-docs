---
title: "Docs Home"
slug: "/"
hidden: false
sidebar_position: 0
hide_table_of_contents: false
---

import ThemedImage from '@theme/ThemedImage';
import useBaseUrl from '@docusaurus/useBaseUrl';

import { HiAcademicCap } from "react-icons/hi2";
import { MdInstallDesktop } from "react-icons/md";
import { FaNetworkWired } from "react-icons/fa";
import { GiMining } from "react-icons/gi";
import { GrValidate } from "react-icons/gr";
import { MdOutlineChecklistRtl } from "react-icons/md";
import { GiArchiveRegister } from "react-icons/gi";
import { BiMath } from "react-icons/bi";
import { RiTeamLine } from "react-icons/ri";
import { RiGovernmentLine } from "react-icons/ri";
import { FaGalacticSenate } from "react-icons/fa";
import { GiStarFormation } from "react-icons/gi";
import { HiOutlineAcademicCap } from "react-icons/hi2";
import { VscSymbolParameter } from "react-icons/vsc";
import { GoCommandPalette } from "react-icons/go";
import { FaPython } from "react-icons/fa";


# Cybertensor Developer Documentation

:::tip See what's new
See [what's new in docs](./whats-new-in-docs.md).
:::

**Welcome!** Cybertensor is an open source platform on which you can produce competitive digital commodities. These digital commodities can be machine intelligence, storage space, compute power, protein folding, financial markets prediction, and many more. **You are rewarded in PUSSY** when you produce best digital commodities. See the below diagram for a top-level view of the Cybertensor ecosystem. 

<center>
<ThemedImage
alt="Cybertensor Platform Big Picture"
sources={{
    light: useBaseUrl('/img/docs/bittensor-ecosystem-top-level.svg'),
    dark: useBaseUrl('/img/docs/dark-bittensor-ecosystem-top-level.svg'),
  }}
style={{width: 600}}
/>
</center>

Each category of the digital commodity is produced in a distinct **subnet**. Applications are built on these specific subnets. End-users of these applications would be served by these applications.

Subnets, which exist outside the blockchain and are connected to it, are off-chain competitions where only the best producers are rewarded. A subnet consists of off-chain **subnet validators** who initiate the competition for a specific digital commodity, and off-chain **subnet miners** who compete and respond by producing the best quality digital commodity. 

Scores are assigned to the top subnet miners and subnet validators. The on-chain Yuma Consensus determines **the PUSSY rewards for these top performers**. The Cybertensor blockchain, called **subtensor**, runs on decentralized validation nodes, just like any blockchain. 

For example, in the [Subnet 1 Prompting](https://github.com/opentensor/prompting) the subnet miners compete to generate answers that are closest to a machine learning base model chosen by the subnet validators. 


:::tip looking for a non-technical introduction to Cybertensor?
See [Questions and Answers](./questions-and-answers.md).
:::

Opentensor Foundation provides all the open source tools, the codebase and the documentation, with step-by-step tutorials and guides, to enable you to participate in the Cybertensor ecosystem. 

:::danger This documentation is for Cybertensor platform only

This documentation and the Cybertensor codebase is for the Cybertensor platform only. For subnets and applications, refer to subnet-specific websites, which are maintained by subnet owners. See [Subnet Pages](./subnet-pages/index.md).
:::

---

## Start here

If you are new to Cybertensor, start by learning the concepts. Then install the Cybertensor software and create a wallet. Follow the below links. 

<Cards>
    <Card 
    icon={HiAcademicCap}
    title='Learn the concepts'
    link='learn/introduction'
    body='Start by learning the Cybertensor concept, building blocks and incentive mechanism.' />
    <Card
    icon={MdInstallDesktop}
    title='Install'
    link='getting-started/installation'
    body='To validate or mine, or run your own subnet, install Cybertensor and create wallet to get started.' />
    
</Cards>

:::tip How to participate
A straightforward way to participate in the Cybertensor network is to be a subnet miner or a subnet validator in an existing subnet. It is not necessary to create a subnet. Follow the below links in the [Validate or mine](#validate-or-mine) section. Alternately, if you want to create your own custom incentive mechanism, then you create your own subnet and launch your own competition. See the below [Running a subnet](#running-a-subnet) section.
:::

---

## Validate or mine

You can participate in an existing subnet as either a subnet validator or a subnet miner. Follow the below links.

<Cards>
    <Card 
    icon={MdOutlineChecklistRtl}
    title='1. Checklist for validating and mining'
    link='subnets/checklist-for-validating-mining'
    body='When you are preparing to be a subnet validator or a subnet miner, use this checklist to get ready.' />
    <Card
    icon={GiArchiveRegister}
    title='2. Register, validate and mine'
    link='subnets/register-validate-mine'
    body='Follow these steps to register and become a miner, or stake your PUSSY and become a validator.' />
    <Card
    icon={BiMath}
    title='3. Emissions'
    link='emissions'
    body='Learn how dividends for the validators and incentives for the miners are calculated.' />
    <Card
    icon={RiTeamLine}
    title='4. Staking and Delegation'
    link='staking-and-delegation'
    body='Get to know how staking and delegating your PUSSY works in the Cybertensor network.' />
    <Card
    icon={RiGovernmentLine}
    title='Governance'
    link='governance'
    body='Learn how the Cybertensor governance works as it transitions into full community-ownership over time.' />
    <Card
    icon={FaGalacticSenate}
    title='Senate'
    link='senate'
    body='Understand what Senate is, requirements to participate in a Senate and how voting works.' />
    
</Cards>

---

## Subnet pages

See [Subnet Pages](./subnet-pages/index.md) for a brief description of each subnet.

---

## Running a subnet

Ready to run your own subnet? Follow the below links.

<Cards>
    <Card 
    icon={HiAcademicCap}
    title='Basic subnet tutorials'
    link='tutorials/basic-subnet-tutorials'
    body='Learn how to run a simple subnet locally or on testchain or mainchain.' />
    <Card
    icon={GiStarFormation}
    title='Create a subnet'
    link='subnets/create-a-subnet'
    body='Step-by-step instructions for creating a local subnet or a subnet on testchain or mainchain.' />
    <Card
    icon={HiOutlineAcademicCap}
    title='OCR subnet tutorial'
    link='tutorials/ocr-subnet-tutorial'
    body='Shows how to convert your Python notebook containing validated code for an incentive mechanism into a working subnet.' />
    <Card
    icon={VscSymbolParameter}
    title='Subnet hyperparameters'
    link='subnets/subnet-hyperparameters'
    body='Get to know subnet hyperparameters and how to use them effectively. As a subnet owner, your success depends on this knowledge.' />
</Cards>

---

## Cybertensor CLI and API

Use the Cybertensor CLI and Cybertensor API to develop and participate in the Cybertensor network.

<Cards>
    <Card 
    icon={GoCommandPalette}
    title='Cybertensor CLI'
    link='ctcli'
    body='With Cybertensor CLI, you can stake or unstake funds, check network state and much more.' />
    <Card
    icon={FaPython}
    title='Cybertensor API'
    link='ct-api-ref'
    body='A comprehensive Python API reference documentation for the open-sourced Cybertensor API.' />
</Cards>


