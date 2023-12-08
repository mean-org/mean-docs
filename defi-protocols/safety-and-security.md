---
description: Mean Protocol safety and security is always front and center
---

# 🔒 Safety & Security

## Safety

DeFi is a brand new space; with each new frontier comes its associated risks. We advise care, caution, and a necessary curiosity while interacting with DeFi protocols.&#x20;

This section details the risks involved with using Mean Finance and some risks associated with the underlying services it gives access to. Please keep in mind that this page does not consider Solana network-level risks.

{% hint style="danger" %}
**This page is not an official nor a legal-binding statement.**&#x20;

It's user-focused documentation of the risk involved with the use of Mean Finance and the underlying protocols it provides access to. &#x20;
{% endhint %}

#### **Who holds your tokens?**

The users control all funds through their wallets and private keys. Mean Finance is a self-custodial set of applications and smart contracts and does not have access to spend the funds in the wallets. There are zero risks of losing funds from interacting with MeanFi if your funds are in your wallet.&#x20;

## Transparency

Decentralized Finance means complete transparency through digital smart contracts on public ledger blockchains. Check more details about the Contract Address and Fees [here](broken-reference).

**PERMISSIONLESS**: People and businesses require no permission from any company, government, or institution to interact with the Mean Protocol. You can interact with the MEAN PROTOCOL MAINNET smart contracts at any time or explore the code directly on the [GitHub](https://github.com/mean-dao/mean-core) repo to get started.&#x20;

**TRUSTLESS**: People and businesses do not need to identify themselves with the Mean Finance ecosystem of protocols and applications. That means no KYC, name, password, or centralized account management. Trustless also means you don't have to trust what we promise. Since these open-source apps and smart contracts are deployed into Solana's mainnet, anyone can contribute and inspect the code they are interacting with on [GitHub](https://github.com/mean-dao/mean-core). &#x20;

**NON-CUSTODIAL**: We don't ever have access to or custody of your money. You always control your money in a self-custody way and through your preferred wallet (see [Solana's Wallet Guide](https://docs.solana.com/wallet-guide)). So long you are in control of your keys, you are in control of your money. Our smart contracts and apps help you manage your money more efficiently while maintaining your privacy and control over those funds.&#x20;

## **Risks**

**Smart Contract / Program Risks**

As developers, we try our best to write safe code and do internal and external code reviews and audits by auditing firms. We have a strict implementation of code coverage for on-chain programs that must pass 100% before being deployed to production, and we perform penetration testing regularly on our web application.&#x20;

However, we do want to remind our users that issues could arise due to human error, and you should be aware that you are abiding by our Terms of Service by asserting you understand these risks.

**Oracle Risks**

We have price oracle redundancy between Chainlink and Pyth oracles. Even though this mitigates single-oracle spoofing attacks and DDOS attacks on their networks, under certain extreme market conditions, pricing data could be corrupted on BOTH oracle networks and, therefore affect the execution runtime of our DCAs. The risk of this happening is low, but if it did happen, it could trigger a swap that results in a potential loss of funds for the user.

## Audits

Mean Finance smart contracts use the Semantic Versioning 2.0 standard (SEMVER). Different versions receive different security audits according to our Security and Auditing Framework:&#x20;

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption><p>Mean Finance Security &#x26; Auditing Framework</p></figcaption></figure>

{% hint style="info" %}
#### NOTE&#x20;

#### The MEAN governance token uses Solana's SPL Token Standard, and it does not rely on a custom contract. Refer to the [Solana Security Audit Report](https://solana.com/solana-security-audit-2019.pdf) for details on the SPL Token Program.&#x20;
{% endhint %}

#### Soteria's Audit Report

Soteria is one of the top Security and auditing firms servicing Solana, with some of the top minds in software and blockchain security research and practice. Their team of experts has over ten years of development of rigorous automated verification and patented technology powered by mathematical proofs and maximal concolic execution.&#x20;

Download the Soteria Audit Security Report on Mean Protocol below:

{% file src="broken-reference" %}

#### Certik Audit Report

CertiK is a pioneer in blockchain security, utilizing best-in-class AI technology to secure and monitor blockchain protocols and smart contracts. CertiK's mission is to secure the cyber world.&#x20;

Download the Certik Audit Security Report on Mean Protocol below:

{% file src="broken-reference" %}

#### Additional Security Procedures

Security is a continuous effort that goes hand in hand with new product development, features, and improvements across our smart contracts.  We continuously evaluate our security measures with continuous code reviews, unit tests, integration tests, code coverage, bug bounties, and penetration tests.

## Multisig

Mean Protocol's programs are owned, deployed, and upgraded through a 3/5 multisig account:

* Programs MultiSig: 8RbALxTJZKK2q267ypXy7EyWckLBmZpnNpuCCcsqJvvn &#x20;

All Mean DAO Treasuries are also managed through multisig accounts, as defined below:

* Treasury MultiSig: Ffm9iByvunbBBkXXnBe6rz7UjLNaeq3VcAwaoZfkEJhw
