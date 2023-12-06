---
description: An on-chain smart contract for vesting and real-time finance
---

# 📦 Token Streamer Whitepaper

## Abstract

Token streaming represents the idea of continuous payments over time. Block numbers are used to measure time in the blockchain and continuously update the balances of the parties in the contract.

## Introduction

When a payment is made to a payee in exchange for time (i.e., employment), an implicit debt obligation is established from the payer to the payee, which is

1. non-mutual
2. carries 0% interest, and
3. financially favors the payer, to the detriment of the payee.

The macroeconomic consequences of this status quo in society are grossly misrepresented, and many attempts have been made to fix the issue.

The following describes a protocol whereby time is measured using block numbers, and the agreed-upon payment rate is streamed continuously to the recipient. The contractual terms are enforced by the Token Streaming Protocol (TSP).&#x20;

The reference implementation for the TSP is made in Solana Blockchain due to its many benefits, in particular, its \~400ms block times (a 3,000% improvement over Ethereum’s). Even though the reference implementation is built in Solana, the same concepts apply to most public permissionless blockchains with their unique operational individualities.

The general use of the TSP goes as follows:

1. A user creates a **Token Stream** by calling the **TSP**. We’ll refer to this user as the **manager** (aka treasurer).&#x20;
2. The recipient of the Token Stream is referred to as the **beneficiary**.
3. The Token Stream is set up with specific conditions such as vesting schedule, rate, cliff, start time, and beneficiary, among other setup options.
4. One or more **contributors** can fund the Token Stream with tokens (SPL Tokens).
5. Once the Token Stream starts, the beneficiary can withdraw tokens from it based on its current solvency.
6. The amount of tokens available for withdrawal is updated in near-real-time (at every block height, or \~400ms in Solana). That is:
   * &#x20;`rate * (current_block_height - starting_block_height)`
7. The Token Stream terms can be updated at any time and require the signatures of both the manager and the beneficiary to commit to the update.
8. The Token Stream can be closed unilaterally and without consensus by either the manager or the beneficiary.&#x20;
9. In the event of closure of the Token Stream, the TSP distributes any unvested funds back to the original contributors and all vested funds to the beneficiary automatically.

## Motivation

Token streaming is beneficial in scenarios where money obligations are defined as a direct function of time in discrete terms. A job ($20/hour) or a pension plan ($1,000/month from retirement and until death) are typical examples where money distributions are agreed upon as a function of time.

These types of time-based money contracts are common and stand in contrast to other scenarios where money is NOT a direct function of time, such as a clothing store ($25 for a pair of jeans). In these cases, the payment streaming utility is limited or does not exist at all.

## **Use Cases**

### **Consumer Use Cases**

#### **Simple Payments**

An alternative of one**-**time payments that works great for services received, such as handyman work, or to set up gifts over time**.**

![](https://lh3.googleusercontent.com/m4Vo2KVkJS8g7-BRqfuhcWDMNhV23lxID9TU3kCNvBkdkMyK1QUs-aSruVs4pKyH\_SEi\_-DEMOEi18sC6Kef82EPxfm7BpbMXWeTrMvWNMkHwkh7feToEoSHMh2bAbvUbqSyNYyg=s0)

#### **Remittances & Family Allowance**&#x20;

Allocate funds regularly to help family members abroad and let them decide when they need to use them. Child allowances for college expenses also fit this use case well.&#x20;

![](https://lh5.googleusercontent.com/JKGGer64y4KeTS\_l4PUGF1LP8-ltZcAbz\_INZlwQ3\_GQUHQULKSc6P8kyPiwW8HzbQo7t6NpmiEQqiporYQCffT0IwuZa3cdNvq4Nk4fpUYc83ZY0GuqGru0CPw\_3Y7AyumBygNE=s0)

#### **Pay For Parking**

Pay only for the time you are occupying a parking spot.

### **Business Use Cases**

#### **Subscriptions**

SaaS subscriptions for products or services (i.e., Netflix, Cellular Service, etc.)&#x20;

![](https://lh3.googleusercontent.com/atIwtRUHoVrSh5cX3BDVY3vqlcAckjdfFypWovuNfmMz1GveGTKfZ4PDL5PFUja4hK1eGjtdLi8AMCQX\_A7EaL1nDGrU02amV\_semlO31mflWVoM2rOxx2ptRcP-AjXqKQCPK-Xa=s0)

#### **Payroll**

Pay your employees from the company treasury. Remove all payroll nightmares. Employees get paid by the second.&#x20;

![](https://lh3.googleusercontent.com/1xzFebYClsAS7RVTtGhzWMmDVVajZ3baUMQw-AvRUtu9\_XDNuvOCB4k4ARYvkKOsGNC\_Oexo7wXPMAHylj39vlyv4lTz\_Ij8wgLokHMkfWOy\_6zE2JWgOYL-1X1UPnD1F4b1-z7z=s0)

### **Retirement and Fundraising**

#### **Pension Plan Payments**

Retirement distributions from retirement age until death.&#x20;

![](https://lh6.googleusercontent.com/O1tcxhbw7JsWG8T-c0gS2UzQnkJoIsLk2NHpMrMnuWV7PM\_KPzkse4Hup0NgMlUVC4SfoTErzDwmjDkNn23JxJu-8DkQcPGEaaD6tzSZpZyDWnCJBVL0G2Kn\_k6\_cmBK1kQrO58M=s0)

#### **Company RSUs**

Employee Restricted Stock Unit benefit plans are commonly seen in tech companies in Silicon Valley.

#### **IPOs, ICOs, IEOs, etc.**

Fundraising for a company or a project. Founders can give investors peace of mind, proving they will not run away with the money unless they meet their milestones.&#x20;

![](https://lh6.googleusercontent.com/O4H7D15PbLa6615c1KYE5K0cHHrSvD9Lv1uTEHXfKTiBWeV53wz5JiNPVdLGvbIFoNwW55sH8t\_w\_EyCslEcDukQXDNFH6oJACSRy0ov\_Uua3TZorqmdMEJGBXMtd3bWtIgdIbJq=s0)

### Real Estate Use Cases

#### **Rent Payments**

Pay Rent / Collect Rent without being bound to monthly installments. This also applies to hotels, motels, and hostels where they can charge by the minute, etc.

![](https://lh3.googleusercontent.com/g7LYqWW5-FNBlDli-hRksMKK07GCp8JgPq71bcwgbs0m8-qkLznzFnN3Xv5N8881rXlJ5-\_Y6feiFNEuNmNlHz4fqjdBaolFkIMJjMdsMth6YbkfgxydFMwNEnbBE21vSWfXd9Mp=s0)

#### **Real Estate Sales**

Manage the escrow payments and distributions in a real estate sale transaction.

![](https://lh4.googleusercontent.com/H6Hp411vbgXyi1G-vxEApzqiTM7vm84HmxG4oXlJcRyo25wlX0\_TTrx7vez-1T1DSUpsNZ660GyhqNIxwmsNyQwqUfU4RNWqIfsJZ50HcGezAA4hbd6Yx2Nhv6kVrIR9XACPY7Zm=s0)

### Government Use Cases

#### Tax Collection

Tax payments are received by governments and distributed to serve different public services, such as Schools, Firefighters, Police, etc. Current systems to distribute collected tax funds require significant overhead and a lack of transparency in the process. A Token Streaming Contract where multiple beneficiaries (School District, Firefighter Dept, etc.) are set up to receive a percentage of the stream automatically creates a great deal of automation and transparency in the tax distribution and benefits system.&#x20;

![](https://lh6.googleusercontent.com/FTFFIFMVIYwZcMXxeXT-B-0uNjA9dC5FvQjQWhjqt31YAHkbekrGJKN6JRGRc-soIVAaMsxf55jMK7j7dPrKu4UPTaoTjq4OfjMC2gMcGhpmgSsB7MCb-ym4xt9XG1p0lDu5g9YL=s0)

#### Government Program Distribution

Social programs from governments around the world must distribute money in the form of vouchers or direct deposits to their citizens. The traditional way of doing this is by delegating a portion of the funds to local governments with the hope they know how to get the money to the right hands and organizations. This creates a lot of redundancy and overhead, causing anywhere between 30% and 40% of the funds to be lost in bureaucratic middlemen overhead.&#x20;

Program distributions can be easily solved with a Token Streaming Contract, whereby taxpayers are identified and registered with the contract and set up to receive their pre-approved vouchers or money directly in the form of NFTs or stable tokens. Using a TSP creates a direct-to-taxpayer route from central governments with ultimate transparency that has never been seen before.  &#x20;

### Other Use Cases

#### Donations

NGOs and Nonprofits can set up a stream that allocates the funds little by little and allows anyone worldwide to contribute to the stream.

#### Inheritance

Distributions to heirs over time to guarantee continuous access to the funds previously owned by the deceased over time.

## **Streaming Accounts**

There are two types of Token Streaming Accounts: **Open** or **Locked**.

With an **Open Streaming Account**, you can create token streams that run indefinitely (no end date). When the streaming account runs out of tokens, all streams stop running until it gets replenished. After replenishing the account, all paused payment streams can resume their operation.

With a **Locked Streaming Account**, you can create token streams that act like a vesting contract for reserved allocations, like the ones needed for investors. These payment streams usually have a fixed end date and may or may not guarantee funds through Reserved Allocations.

Reserving an allocation from a **Locked Streaming Account** into a specific token stream means the beneficiary immediately becomes the OWNER of the allocation. However, the owner-beneficiary is locked from accessing these funds as specified by the rate and frequency of the token stream. This is useful for investors or any pre-paid contracts since the beneficiary has already paid for their tokens, and the intent is to delay their distribution.

This stands in contrast with **Open Streaming Accounts**, like those for Payroll, where work needs to be completed to EARN that allocation. The beneficiary is not the OWNER of their allocated tokens until they vest in the payment stream.

## Token **Streaming** Actors

The payment streaming program specification defines how the different players, actors, and components interact with each other.

The basic premise of a token streaming smart contract is that once it gets executed between a manager **(**sender) and a beneficiary (recipient), its terms are enforced by code instead of humans. The manager cannot run away with the tokens owed to the beneficiary, and the beneficiary cannot take the tokens he/she has not yet earned.

In order to stream tokens from A→B at a specific rate/flow over time, the following participants are defined.

1. **Token Streaming Program (TSP)**: A smart contract or program deployed to a permissionless blockchain that uses this protocol as a reference implementation.&#x20;
2. **Streaming Account**: An account (wallet address) used to escrow the tokens being streamed. This account is under the sole custody/ownership of the TSP smart contract.
3. **Manager**: A person or organization creating and managing a Streaming Account and its Token Streams.
4. **Contributor**: Any person or organization contributing tokens to a Streaming Account.
5. **Beneficiary**: A person or organization receiving tokens from a Token Stream.
6. **Stream Terms**: A set of terms and an amount of tokens, expressed as a rate over time, that should be streamed to a beneficiary from the Streaming Account.
7. **Token Stream**: An account maintained by the TSP, which maintains the state of a stream in near-real-time based on the terms encoded, along with the vested and unvested amounts on behalf of a beneficiary. &#x20;

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

## **State Machine**

A token stream is a finite-state-machine (FSM) with the following states and transitions:&#x20;

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

<table data-header-hidden><thead><tr><th width="156">Current State</th><th width="194">Input</th><th width="129">Next State</th><th>Output</th></tr></thead><tbody><tr><td>Current State</td><td>Input</td><td>Next State</td><td>Output</td></tr><tr><td>Scheduled</td><td>Pause CTA</td><td>Paused</td><td>Stops the token from streaming to the beneficiary. This is reversible.</td></tr><tr><td>Scheduled</td><td>Planned time arrived</td><td>Running</td><td>Starts streaming tokens from the streaming account to the beneficiary.</td></tr><tr><td>Running</td><td>Manager or Beneficiary manually stops the stream</td><td>Paused</td><td>The stream is paused, and tokens stop flowing to the beneficiary.</td></tr><tr><td>Running</td><td>Streaming Account ran out of tokens</td><td>Paused</td><td>Since there are no token to stream, the stream is stopped, and the beneficiary does not get any more tokens. This is reversible if the streaming account is reloaded.</td></tr><tr><td>Paused</td><td>Streaming Account reloaded with tokens</td><td>Running</td><td>Resumes streaming tokens from the streaming account to the beneficiary.</td></tr></tbody></table>

The token stream can be closed unilaterally and without consensus by the manager or the beneficiary. Closing a stream will result in all the vested amounts being distributed to the beneficiary, and the unvested amounts and any rent returned to the streaming account.

## **Related Works**

ERC-1620 is a protocol specification on Ethereum defining a standard for money streaming with similar motivations to those expressed here. The MSP builds upon this work to make a general-purpose protocol that can serve all time-bounded contracts, with or without a present end date and upfront locks. The specification for ERC-1620 is here: [https://eips.ethereum.org/EIPS/eip-1620](https://eips.ethereum.org/EIPS/eip-1620)

EIP-2100 is an improvement proposal expanding some of the concepts introduced in ERC-1620 by adding options related to the settlement of the funds in the stream. The proposal for EIP-2100 is here: [https://github.com/ethereum/EIPs/issues/2100](https://github.com/ethereum/EIPs/issues/2100)&#x20;

Sablier Finance ([https://sablier.finance/](https://sablier.finance/)) is an implementation of ERC1620. The protocol focuses on the payroll use case and enforces the stream's start and end time, which is a limitation to those use cases where the end date is unknown (such as a pension fund). Sablier was launched in 2019 and, in less than 12 months, had a Total Value Locked (TVL) of over $1M, and by Jan 2021, TVL was over $100M, showing the extreme demand for this token building block.

Circle’s CEO comments on streaming payments: [https://www.pymnts.com/news/payment-methods/2021/circle-ceo-programmable-money-ushers-in-era-of-continuous-streaming-payments/ ](https://www.pymnts.com/news/payment-methods/2021/circle-ceo-programmable-money-ushers-in-era-of-continuous-streaming-payments/)

## **Other Considerations**

#### **Conditional Streams**

Hourly employees get paid by the exact number of hours or minutes they work. The process works like this:

1. Employer and employee agree on an hourly rate (i.e., $20/h)
2. The employer gives the employee a way to clock in and out, like a physical clocking card at a factory.
3. At the end of the month, the employer inspects the hours reported by the employee and pays him accordingly.

To support this use case with the Token Streaming Contract, we would need to:

1. Allow the token stream to be configured with an **auto\_pause\_in\_seconds** parameter on creation, such that he/she can set this value to something like 8 hours, assuming the factory shifts are at most that long.
2. Allow the beneficiary to **ResumeStream** to signal the contract that he/she is indeed “on the clock” and, therefore, should be earning tokens from the stream.
3. Allow the beneficiary to **PauseStream** to signal the contract that he/she is “off the clock” and, therefore, should NOT be earning tokens from the stream.&#x20;
   1. This API should also allow the manager invocation for overrides in case a worker forgets to clock out or clock in.

The biggest challenge with these conditional on/off-clock triggers is the timekeeping shenanigans calculating the escrow\_vested\_amount, and the formula to calculate this field already accounts for this.

#### The Rogue Manager

**Problem**: Consider the following case.

1. A new streaming account is set up by John with one beneficiary, Alice
2. John adds a stream guaranteeing Alice a pay rate of $1,000/month
3. John then talks to contributors Bob and Jane to fund Alice’s operation through the streaming account.&#x20;
4. Bob and Jane like Alice’s project and agree to fund the streaming account with $1,000,000. Knowing Alice can only take $1,000/month, they feel they are giving the project long-term stability.
5. Now John goes rogue and secretly decides to add his accomplice Pepe as another beneficiary to the streaming account without asking Bob and Jane.
6. John sets up Pepe with a rate of $999,000 per minute.
7. The results next morning are catastrophic:
   1. John is kaput, nowhere to be found.&#x20;
   2. Alice wakes up to an empty streaming account, and her project is toast.
   3. Bob and Jane lost $1,000,000 and have no project to back up.
8. This is a classic rug pull.

**Solution**: Contributors should take special care in ensuring the streaming account is managed through a multisig wallet (like [Solar Shield](solar-shield-solana-multisig.md)) and require a super-majority vote to add new Token Streams.
