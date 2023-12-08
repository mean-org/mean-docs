---
description: An on-chain smart contract for threshold multisig wallet account abstraction
---

# 🕶 Solar Safe Whitepaper

## Abstract

This paper discusses the Solar Safe Multisig (a social engineering solution) to address the security trilemma of crypto assets through the use of BLS Threshold Multisigs, Smart Contracts, and MFA (multi-factor authentication) mechanisms.&#x20;

## Motivation

The current state of self-custody asset management with institutional-grade security is in its infancy across crypto. As the overall market cap of crypto continues to expand, the need for a highly secure, simple, private, and affordable self-custody solution remains elusive for crypto asset management.

We'll deconstruct in this paper a solution through Mean Multisig that will address these issues while maintaining the three basic principles that underpin its development:

1. **Security**: We handle digital assets. Security and auditing are first-class citizens here.
2. **Usability**: Batteries included; it just works; as easy as apple pie; no manual needed.
3. **Privacy:** No authority or control is set over our users. Self-custody is the standard.

Crypto custody solutions in the market today always compromise by meeting only two of these three basic tenets. For example:

* Good <mark style="color:green;">**Security**</mark> + <mark style="color:green;">**Usability**</mark> at the cost of <mark style="color:red;">**Privacy**</mark> → Coinbase, Kraken, Celsius (all custody solutions)
* Good <mark style="color:green;">**Security**</mark> + <mark style="color:green;">**Privacy**</mark> at the cost of <mark style="color:red;">**Usability**</mark> → All hardware wallets (Trezor, Ledger, etc.), and all web institutional web wallets like Fireblocks, Gnosis, Coinbase Institutional Custody, etc.
* Good <mark style="color:green;">**Usability**</mark> + <mark style="color:green;">**Privacy**</mark> at the cost of <mark style="color:red;">**Security**</mark> → Metamask, Phantom, and most popular software wallets

The primary cause for this widespread conundrum is that security-conscious wallets have come up with solutions to the security challenge from an engineering and cryptographic standpoint. Complex solutions like MPC (Multi-Party Computation) and CMP (Certificate Management Protocol) have been implemented all the way down to the chipset level. While these solutions do a lot of good from the security standpoint, their implementation is complex and creates often misunderstood processes and usability issues for the vast majority of users.

With these in mind, the aim is to deliver the next generation of self-custody asset management solutions with institutional-grade security and support for real-time finance and make it accessible and affordable for anyone to use.

## Background

Crypto asset management requires the safeguarding of a PRIVATE KEY. Whoever holds the key, holds the asset.

### Private Key Management

A private key looks like this: _<mark style="color:red;">5Kb8kLf9zgWQnogidDA76MzPL6TsZZY36hWXMssSzNydYXYB9KF</mark>_… which, clearly, is a nightmare to remember. So we, humans, decided is better to “save” it in a better place other than our brains.&#x20;

You can save it on a piece of paper, and then type that in every time you want to access your funds or make a transfer… but that’s too much typing, so you decide to send yourself an email with it in the subject line… but having to search for it every time is too time-consuming, so you save it in a Word doc with the name “BTC private key” on your desktop.&#x20;

These (really unsafe methods) were the state of crypto asset management, and therefore "wallets" for the first few years of crypto (which was no bueno, if the tone didn’t give it away).&#x20;

Then the great “mnemonic phrase” came to the rescue with the BIP39 standard and its cousins. It’s basically a bunch of words from a list of 2,048 words with certain entropy characteristics that make it statistically impossible for a random selection of them to be in the exact same order twice in the history of the universe. And so, a group of cyberpunks decided that instead of remembering this: _<mark style="color:red;">5Kb8kLf9zgWQnogidDA76MzPL6TsZZY36hWXMssSzNydYXYB9KF</mark>_… we humans are going to be sooo much better remembering this:&#x20;

<mark style="background-color:green;">involve</mark> <mark style="background-color:green;">layer</mark> <mark style="background-color:green;">staff</mark> <mark style="background-color:green;">express</mark> <mark style="background-color:green;">urban</mark> <mark style="background-color:green;">catch</mark> <mark style="background-color:green;">group</mark> <mark style="background-color:green;">congress</mark> <mark style="background-color:green;">addict</mark> <mark style="background-color:green;">behind</mark> <mark style="background-color:green;">drama</mark> <mark style="background-color:green;">reopen</mark>

I want some of what they are having, please! The idea is that these words are used as the input to a function that spits out the private key that was hard to remember in the first place, so… problem solved? 🤦&#x20;

We crypto-geniuses basically moved the problem of “private key storage” from (1) our heads to (2) the paper to (3) a digital file, to (4) a digital file + a digital program… way to go! Some people call this _**progress**_.

### Crypto Wallets

Ohhh software... the solution to all our problems. Welcome to the crypto wallet orgy.

Generally speaking, a crypto wallet refers to a piece of software (usually a browser extension or a mobile app) that basically knows how to store your private key and corresponding seed phrase in the local environment where the app runs (the browser or the OS of the device where it runs, like macOS, Windows, iOS or Android).&#x20;

That’s it.&#x20;

Some are better looking than others, some have extensibility features, and some let you do basic functions like token swaps, etc, but the essence of most wallets is the same: a self-custody solution for your crypto assets.

* Passphrase <-> Private Key conversion logic, plus
* Local storage of your crypto keys.

### Custody Solutions&#x20;

Then some actual PMs and Designers saw the crypto-gurus struggling and came to the rescue with some clever solutions. _**“What if we give you a good-old username and password and WE store your complicated private key in our servers, we’ll make it simple and awesome and familiar to you dear user, and you’ll never have to worry about your private key ever again. We’ll become your Custodian”**_, they said. Brilliant… everyone going bananas over Blue Labels and Caviar.&#x20;

The problem these new geniuses created was that they took risks that used to be spread across thousands of individual wallets and concentrated them into single points of attack. Now the hackers don’t need to find individual users, they can simply focus on going after these servers where companies like MtGox, Cryptopia, and Coinbase (all hacked) store thousands of private keys and hold billions of assets because they are an easier target. So now these companies need to invest millions of dollars in security, violate your privacy and charge exorbitant fees for their services, and share your information with governments and marketing partners… so, bye-bye privacy there.&#x20;

With centralized custody solutions, you risk PRIVACY and SECURITY for the CONVENIENCE of not having to deal with private keys. There is a popular saying in crypto that goes like this:&#x20;

> <mark style="color:red;background-color:yellow;">**NOT YOUR KEYS, NOT YOUR CRYPTO**</mark>

### **Hardware Wallets**

So, going back to owning your own keys… what’s next… well there’s this thing in security called multifactor authentication… let’s use it here. First, let’s break it down:

1. Single-Factor Authentication = Something you **KNOW** (like a password)&#x20;
2. Two-Factor Authentication (2FA) = Something you **KNOW** + Something you **HAVE** (like a phone)
3. Multi-Factor Authentication (MFA) = Something you **KNOW** + Something you **HAVE** + Something you **ARE** (like biometrics… fingerprint, face id, etc.)

**Higher factors = higher security. Ok, let’s do this crypto fam! → Welcome to hardware wallets. With a hardware wallet, we get to 2FA really quickly. It’s simple, here’s how they work:**

1. Buy a hardware wallet
2. Set it up with the same seed phrase with a bunch of words like we covered before, then write them down and store that in your closet. The real private key is stored in the device (that’s your 2FA)&#x20;
3. Set up a PIN with tiny physical buttons (this will be your equivalent to a password)&#x20;
4. Install a software wallet, follow 10 tutorials online, and connect it to the hardware wallet you just bought&#x20;
5. Test it and make sure it works&#x20;
6. Be miserable for the rest of your life carrying around and protecting a piece of junk that removes the joy out of your crypto experience.&#x20;
7. But sleep like a baby knowing that IF YOU CAN REALLY MAKE SURE NOBODY WILL EVER COPY THAT SEED PHRASE from #2, your assets will be safe.

Not only is this solution shitty because it is cumbersome to set up and pretty much nails it as the WORST onboarding experience of any product ever made by mankind, but in reality, it only removes the digital risks to your assets and moves that risk to the physical world.&#x20;

,Good luck if you share that SentrySafe hunk of metal with your significant other who’ll no longer be so tomorrow. Fuck! Run, run, move your shit to a new hardware device, and do steps 1-7 again, and then remove all your tokens out of the old wallet into the new one before he/she makes a gangster move to wipe you out and… wait… it’s all gone!&#x20;

You just got socially engineered out of your money by an angry ex. But how is that possible?! You had what was supposed to be the safest way to guard your crypto assets.

### Smart Wallets&#x20;

Ok, that angry partner was not cool. So, a technical PM, watching his friend go through this pain, thought of a solution to fix the hardware wallet problem: Enter the SMART WALLET.&#x20;

Smart Wallets are wallets owned by a Smart Contract instead of a public key kept by you. This little nuance gives smart wallets two super-powers:&#x20;

1. **You can add all the logic and rules you want**, like account recovery process, account locks, or transfer limits per-day/per-week/per-anything-you-want-really… just like regular people are used to in any good’ol bank.
2. **You remain in control of the assets in it without the responsibility of safekeeping the private key**. This is accomplished by making one of the rules in #1 be that only certain other addresses can perform certain functions with the money in it.&#x20;

So, in essence, smart wallets separate the storage of the assets from the storage of the keys that can access these assets. You now can simply have your “access wallet” be a regular crypto wallet that holds nothing, and move all your assets to a “smart wallet” that can be accessed any time by that “access wallet” to perform operations on those assets.&#x20;

But once more, this is a technical solution to a social engineering problem. Besides the clear benefits of having a programmable wallet with a “smart wallet”, the security features are “more secure” to the extent they are more obscure.&#x20;

Security by obscurity is inversely correlated to the net worth of the assets being secured. The higher the net worth, the more interest will generate, the more malicious eyes you have in it, the less obscure it becomes, and the easier it is to exploit.&#x20;

### Social Engineering

Most security hacks on wallets are NOT the result of poorly implemented wallet security, but the result of social engineering attacks on the owner of the wallet hosting the private key, like the one orchestrated by the angry partner, or some phishing email the owner fell for.&#x20;

Therefore it stands to reason that social engineering security should be mitigated with a social engineering solution.&#x20;

Such is the case for SSS (Shamir’s Shared Secret), BLS (Boneh–Lynn–Shacham), MPC (Multi-party computation), and Multisig solutions. Even though technically they are not the same, their motivations come from similar realizations that we need more than a single point of failure to secure assets. It is not the focus of this paper to discuss the specific implementations of each of these technologies, so we'll limit ourselves to a handy diagram:

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

All these rely on the idea of maintaining a set of public keys or parts to verify a signature ultimately.  However, beyond the technical complications of these methods, their weakness is having a single point of failure for the entire system on any of their keys/parts.

Enter Threshold Schemes.

### Threshold Schemes&#x20;

A threshold scheme is fundamentally a social construct where to operate with assets, a consensus must be reached first by a minimum number of participants in the system (the threshold). Threshold Multisigs, Distributed Key Generation (DKG), and, more generally, Multi-Party Computation (MPC) algorithms are all forms of threshold scheme cryptography. The takeaway is that if someone loses their keys or is away on vacation, we can still sign.&#x20;

Proof of work and proof of stake blockchains are massive threshold schemes asking hundreds of thousands of nodes and validators to sign when they agree with a transaction. The Bitcoin network is the most attacked in the world and has yet to suffer from a single breach of this algorithm since its inception in 2009.&#x20;

### Threshold Multisig

A threshold multisig, as the name suggests, will have multiple signers (aka owners), and a minimum number of them (the threshold) must sign in order to execute transactions. This is usually referred to as n/m multisig, where **n** is the threshold required out of the **m** owners that can sign for the multisig.&#x20;

Hacking a multisig requires coordinated social engineering attacks that are time-sensitive and operationally complex. It is the hardest to pull off, and besides serving as a deterrent for hackers, it is impossible to accurately identify all owners at the same time and have them react in the same way to the planned attack.&#x20;

## Solar Safe Multisig&#x20;

Even though threshold multisigs are a massive improvement in security over their technical counterparts, they lack the simplicity and familiarity of MFA and the flexibility of the logic of smart contracts.&#x20;

We propose combining a specific set of these technologies, specifically Smart Contracts, BLS, Threshold Multisigs, and MFAs, to bring a Solar Safe Multisig to life. With clever UX and the right technology combo, we are ticking our three core tenants for self-custody asset management:&#x20;

* <mark style="color:green;">**Security**</mark>: Driven by the Mean Threshold Multisig, BLS, Smart Contract Accounts/Wallets, and MFA, hacking a Solar Safe Multisig wallet becomes exponentially challenging as the attacker will need to perform social engineering and technology penetrations on more than one person across multiple devices to execute a malicious transaction.
* <mark style="color:green;">**Usability**</mark>: The easiest way to think about the usability of a Solar Safe Multisig is like a Business Bank account (think Brex, or whatever you consider the best banking experience you’ve ever had for a business). In this “business” setting, a set of owners/authorized personnel can configure a set of rules and policies for the Solar Safe Multisig, such as expenses, limits, account locking, etc., for each of the people in the organization, therefore limiting beforehand the worst-case scenario in the case anyone gets compromised.
* <mark style="color:green;">**Privacy**</mark>: Across the different technologies leveraged for Solar Safe Multisig, privacy is at the core of all of them. The Mean Multisig is 100% DeFi without any centralized infrastructure. The MFA security around it has a minimal centralized infrastructure blueprint to support multisig MFA for the Solar Safe Multisig, mainly through on-device biometric verification (FaceID, TouchID, etc.) or 3rd party authenticator apps (Google Auth, Authy, etc.) or traditional communication infrastructure (email and SMS). Solar Safe keeps privacy as a core tenant with no KYC/B, no custody, and no login required.&#x20;

A Solar Safe Multisig also offers an incredible solution to complex asset management, like account delegations, social account recovery with guardians or witnesses, dead man’s switch workflows for asset legacy and inheritance, and more, all through the simple concept of security via social engineering afforded via multisigs.

<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption><p>Solar Safe Components</p></figcaption></figure>

{% hint style="info" %}
We know you want more details, more specs about Solar Safe Multisig, the formulas, the design, the architecture, more, more, more.&#x20;

We are, however, the kind of team that doesn't do well with premature promises. We prefer identifying a really big problem, proposing a solution (like we did here), and iterating on it as we build it. As we do these iterations and details about the final implementation become clearer and more concrete, they will be added here.&#x20;
{% endhint %}

## Summary

In this whitepaper, we covered how the importance of self-custody asset management, the state of cryptographic solutions and their complexity, the security trilemma, and other industry challenges related to crypto assets custody.&#x20;

We also explored what a Solar Safe Multisig is, and how it leverages BLS, Threshold Multisigs, MFA, and Smart Contracts (Programs in Solana) to deliver the next generation of self-custody asset management solutions with institutional-grade security and support for real-time finance and make it accessible and affordable for anyone to use.
