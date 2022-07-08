<div style="text-align:center">

![Knish.IO: Post-Blockchain Platform][logo]

</div>

<div style="text-align:center">

[info@wishknish.com](mailto:info@wishknish.com) | [https://wishknish.com](https://wishknish.com)\
Authored by [Eugene Teplitsky](https://github.com/EugeneTeplitsky)

</div>

---

# Technical Whitepaper v6.1

## Abstract

Distributed-ledger-based solutions for large-scale application deployment, transaction settlement, and user governance offer significant benefits in the areas of transparency, security, and cost-effectiveness. However, five major barriers to broad adoption remain (Critical Factors):

1. scalability and performance,
2. future-resistant security,
3. resource requirements and environmental impact,
4. user-friendliness and transparency, and
5. decentralization and resilience

Current leading solutions for building decentralized applications (dApps) leverage one of several consensus algorithms, including the computationally expensive Proof-of-Work (PoW), the much less transparent and potentially insecure Delegated Proof of Stake (DPoS), and the oligarchic Proof of Stake (PoS) where wealth equals influence. Each of these popular consensus algorithms sacrifices one or more Critical Factor in order to function. The purpose of this whitepaper is to demonstrate the Knish.IO distributed ledger technology, and its solution for effectively maintaining all five Critical Factors simultaneously while delivering state of the art deployments for dApps.

---

## Introduction

Since the Satoshi Nakamoto whitepaper, blockchain architecture (as one possible application of DLT - distributed ledger technology) has found initial trial applications in many industries, including banking, e-commerce, transportation, supply chain management, communication, and more. New applications are being imagined daily, and there seems to be no limit to the transformative reach of decentralization. However, before any single DLT solution can truly take hold, and position itself as a viable option for the long term, it must overcome the challenge of delivering five Critical Factors without which their influence will be limited to die-hard fans, early adopters, and blockchain enthusiasts.

WishKnish proposes a novel DLT solution that attempts to address all five Critical Factors:

---

## Critical Factor 1: Scalability & Performance

> “Scaling is the key problem to solve in terms of any blockchain-related tech.
> Those who solve it first, will have a massive advantage.”- Mike Novogratz

The ability of a DLT to scale can be described as either a function of its consensus algorithm (so-called “consensus-bound” ledgers, such as Bitcoin, EOS, Ethereum, and many others) or as a function of its network size (so-called “network-bound” ledgers, which includes Knish.IO, IOTA, and other DAGs). It is important to understand that all consensus-bound DLTs will become slower as their network size grows, and be forced to explore performance solutions, such as [5] “sharding”, which sacrifice decentralization in favor of performance. In contrast, network-bound DLTs thrive in an expanding network environment and, in fact, require this expansion in order to function performantly and securely.

An illustrative example [1] of this phenomenon is the recent advent and popularity of the CryptoKitties game on the Ethereum blockchain, and the resulting network congestion that affected the usability of the ledger for thousands of users.

In the case of Knish.IO, a directed acyclic graph (DAG) data structure is employed to fulfill the scalability requirement. [2] In mathematics and computer science, a DAG is a finite directed graph with no directed cycles. That is, it consists of finitely many vertices and edges, with each edge directed from one vertex to another, such that there is no way to start at any vertex v and follow a consistently-directed sequence of edges that eventually loops back to v again. Equivalently, a DAG is a directed graph that has a topological ordering, a sequence of vertices such that every edge is directed from earlier to later in the sequence.

![Directed Acyclic Graph][dag]

With a DAG, each incoming transaction references multiple specifically chosen transactions that came before it, and performing a verification procedure on each, to ensure that it has a valid signature.

---

## Critical Factor 2: Platform Security & Future-Resistance

> “As organisms evolve through changes in their DNA, blockchain protocols evolve through changes in their code. And like biological organisms, the most adaptive blockchains will be the ones that survive and thrive.”- Fred Ehrsam, Coinbase

The term “future-resistance” implies the hardiness of a project’s security algorithms in the face of a changing technological landscape. Because modern DLTs in general are bleeding-edge technologies today, it is critical for distributed ledger projects such as Knish.IO to look far ahead in terms of possible security challenges on and beyond the horizon.

Quantum computing is a concept that has the potential to truly throw a wrench into the works of most encryption mechanisms in use today [8], and therefore Knish.IO takes special precaution by its choice of quantum-resistant XMSS [6] (eXtended Merkle Signature Scheme) mechanism as a baseline algorithm for securing its molecular structure in a post-quantum world. XMSS has been recommended by NIST as a post-quantum alternative for stateful hash-based signatures [9].

A key feature of XMSS is the reliance on one-time signatures via Winternitz One-Time Signatures Plus (WOTS+), which is leveraged by Knish.IO to ensure that all keys used to sign transactions are regenerated after every use, and that no key is ever used twice. This mechanism helps protect Wallet holders from transactions spoofed by adversaries, and process only those signed by legitimate Wallet holders.

Below is a diagram of the XMSS tree construction:

![XMSS Tree][xmss]

Furthermore, because encryption keys are similarly recycled, decrypting a thread of metadata or messages becomes increasingly difficult for a bad actor.

Additionally, many of the algorithms in use within the ledger are designed to be changed and upgraded over time as the need arises. After all, every cryptographic algorithm has a limited shelf life, so it is important to be adaptable to a changing cybersecurity landscape. The set of algorithms used (encryption, Wallet character set, hashing algorithm, etc.) can be determined when negotiating an authorization key with a Knish.IO server.

---

## Critical Factor 3: Resource Requirements & Environmental Impact

> “The sooner we find ways to make cryptocurrency mining energy use 'greener', the better it would be for us and for blockchain, a technology that could potentially transform every industry in the world.”- Dom Galeon, Futurism.com

Legacy DLTs such as Bitcoin require an inordinate amount of energy in order to function due to the way their consensus algorithms are constructed.

Let’s get a sense of just how much environmental impact we have to contend with [7]:

| Description                                                                              | Value    |
|------------------------------------------------------------------------------------------|----------|
| Bitcoin's current estimated annual electricity consumption*                              | 152 TWh  |
| Country closest to Bitcoin in terms of electricity consumption                           | Malaysia |
| Electricity consumed per transaction                                                     | 1647 KWh |
| Number of days an average U.S. household can be powered by a single Bitcoin transaction  | 56       |
| * Number of years ALL of U.S. households can be powered by a year's worth of Bitcoin use | 6.5      |

<small>(* computed by dividing 152 TWh of total use by 1647 KWh per transaction to get an average number of annualized transactions, multiplying by 56 days of use for a single home, then dividing by 122,354,219 - the number of households in the U.S. [11] - and finally dividing by 365)</small>

The reason for this massive energy drain is that the process of confirming new blocks being added to the ledger is an ever-escalating arms race of computing power under the Proof of Work consensus algorithm.

Instead of forcing nodes to compete for who gets to validate a block of transactions by performing what is essentially “busy-work,” Knish.IO takes a very different approach - a "pay-it-forward" approach that is both asynchronous and Byzantine fault tolerant, while ensuring that more Molecules receive validation than are created - meaning that it is prepared to handle a sudden surge of traffic gracefully, and without degradation of security.

---

## Critical Factor 4: User-Friendliness & Transparency

> “The main advantage of blockchain technology is supposed to be that it's more secure, but new technologies are generally hard for people to trust, and this paradox can't really be avoided.” - Vitalik Buterin

At the end of the day, if an amazing new technology is too abstract for the average consumer to use, it will not be adopted by the average consumer. That’s not to say it needs to be understood from top to bottom - after all, most automobile owners do not have a very deep understanding of the inner workings of a combustion engine or transmission, and yet can drive their cars just fine.

VentureBeat has postulated in mid-2021 that 80% of tech could be built outside IT by 2024, thanks to low-code tools [12] - a trend that is still largely being ignored by the blockchain community.

It is therefore our mission to bring mass adoption to the public by wrapping complex concepts into a user-friendly, easily-digestible experience - much like Microsoft Windows’ innovative Program Manager GUI did for desktop computing in the era of command-line MS DOS usage.

We see the following as critical sources of friction slowing or stopping consumer adoption:

1. **Storage of secret keys.** Forcing users to rely on software wallets, hardware wallets, paper wallets, cold storage, and other options for keeping a secret key is a lot to ask of consumers, especially when all they want to do is buy a cup of coffee with the tokens in their wallet. By leveraging biometric signatures and other modern passwordless mechanisms in lieu of a secret key, users can skip the overwhelming storage options, and rely purely on device sensors and (optionally) two-factor authentication to derive their signature each time they need to authorize an operation.


2. **Gas.** The concept of having to first purchase a supply of tokens before being able to transact on a ledger is inherently damaging to consumer uptake. Gas is used by Ethereum and many other distributed ledgers to subsidize verification by validators, but in the case of Knish.IO, validation is performed on random Molecules by the entity bonding a new Molecule into the ledger, essentially paying it forward, and removing the need for gas.


3. **Address naming convention.** A typical Ethereum address looks like this: 0xec824C1aF7304727eC92c71FfFEeDc0d6C38Eb0D. Imagine trying to tell a friend where to send a payment. Unless you do a lot of copying and pasting, or rely on a QR-code / NFC scanning solution, it will be very difficult indeed. Knish.IO introduces the concept of “slugs” - alphanumeric reference strings that are defined by the user, to give their Knish.IO Wallet Bundle address a friendly, memorable name.


4. **Node administration and governance.** If you are adventurous enough to deploy your own node, users can expect potentially intimidating command line deployment, configuration via direct file editing, and a general lack of flexibility in how the node is utilized. Conversely, one way of administering Knish.IO nodes is via KnishOS - a user-friendly GUI designed for node administration, digital asset / NFT management, and distributed ledger governance, as well as for e-commerce and general content management, turning a passive node into a potential online community and a source of revenue.

![Create Token Screenshot][create]

5. **Hardware requirements.** Legacy blockchain platforms - especially those geared towards inefficient consensus mechanisms - have spawned a shift in hardware optimization to take full advantage of mining and obtain more hashing power. Expensive, power-hungry ASICs, mining-optimized GPUs, or in some cases, even more exotic requirements - such as tryte-based logic chips - to take full advantage of the software. This limitation also impacts the ability to utilize cloud computing environments to deploy distributed ledger infrastructure, as most providers do not allow for mining due to their sustainability efforts. Knish.IO is designed for inexpensive, easy to deploy, environmentally sustainable infrastructure that does not rely on mining. For this reason, Knish.IO is one of the few distributed ledgers equally capable of operating on both a high-powered supercomputing cloud and a $35 Raspberry Pi single-board computer.

---

## Critical Factor 5: Decentralization & Resilience

> We must be able to measure blockchain decentralization before we can improve it. - Balaji S. Srinivasan, Former CTO of Coinbase

Distributed systems much achieve consensus on the "truth" of the ledger in order to function, and the greater the number of validators able to independently verify the authenticity of data, the more resilient that ledger becomes to tampering.

One empirical measurement of decentralization is the Nakamoto Coefficient [10]. It is a number indicating the minimum number of entities in a ledger subsystem that need to collude (or be affected by bad actors) in order to compromise the system:

![Nakamoto Coefficient Algorithm][nakamoto]

Based on the competitive nature of the most popular consensus algorithms (Proof of Work and Proof of Stake), it is natural for "winners" to be determined by the amount of hashrate or stakeable token assets they are able to contribute. This, in turn, is dictated by wealth: the more liquid capital an entity possesses, the more mining equipment or stakeable tokens they are able to acquire, the greater the amount of control over the consensus process. Over time, this type of system will degrade towards centralization of control, resulting in a measurable decline of the Nakamoto Coefficient.

Knish.IO's noncompetitive consensus mechanism is designed to ensure that every stakeholder has an equal amount of influence over the ledger, by organizing into so-called "Anchors", or dApp-specific load-balancing hierarchies of nodes that serve as the primary entry point for that specific dApp's transactions.

![Knish.IO Peering Infrastructure][infrastructure]

Each respective anchor is incentivized to behave correctly not via winning mining or staking rewards collected through gas, but via business continuity: if an anchor is not consistent with the rest of its peers' state, its reputation will decline algorithmically until it is no longer able to broadcast transactions to its peers.

---

# Interfacing with Knish.IO Nodes

The process of developing Knish.IO integrations with new and existing applications is simple and extensible, through the use of open-source software development kits (SDKs) in several popular languages, allowing developers to focus on the user experience and rapidly deploying their dApp.

Currently available Knish.IO SDKs:

1. [JavaScript](https://github.com/WishKnish/KnishIO-Client-JS)
2. [PHP](https://github.com/WishKnish/KnishIO-Client-PHP)
3. [Kotlin/Java](https://github.com/WishKnish/KnishIO-Client-Kotlin)
4. [Python](https://github.com/WishKnish/KnishIO-Client-Python)
5. [C++](https://github.com/WishKnish/KnishIO-Client-CPP)

Knish.IO node servers themselves are administered via:

1. [Artisan](https://laravel.com/docs/9.x/artisan)-based command line tools
2. Industry-standard GraphQL-based APIs
3. KnishOS - a user-friendly GUI designed for node administration and distributed governance

They are designed to operate in a lightweight, cloud or self-hosted environment - simple hardware (potentially as lightweight as a Raspberry Pi) running PHP-compatible code, with a flexible selection of relational database engines, make it easy to deploy (and maintain).

![Knish.IO Architecture Diagram][architecture]

---

# The Knish.IO Organism: Atoms, Molecules, and Cells

Given the inefficiencies inherent in current-generation blockchain technologies, Knish.IO builds on their early successes by following a molecular model for describing its transactional qualities. As an efficient model frequently demonstrated in nature and science, it also serves as a concise summary of the functionality of each component within the model and allows for flexibility in visualizing the complex, multidimensional nature of the ledger which stores transactions, events, and metadata described by edge clients.

To this end, we introduce the concept of **Cells**, **Molecules**, and **Atoms**.

- **Atoms** are sub-transactions that only perform a single, monodirectional action, such as removing X Tokens from one Wallet, adding Y Tokens to another Wallet, or contributing secure metadata to a virtual schema.


- **Molecules** are collections of Atoms which are either accepted or rejected all at once, and bond to (reference) a number of previous transactions to help facilitate Knish.IO’s federated consensus model.


- **Cells** are sharded sub-ledgers within the decentralized DAG environment, each serving one specific application, and defining rules for the behavior of every Molecule within it.

Taken together, the collection of Cells, Molecules, and Atoms can be described as an **Organism**.

By leveraging Cells, Molecules, and Atoms, Knish.IO is capable of a network-bound scalability and transaction settlement within 5 seconds, regardless of the transactional volume. In fact, as the network grows, we fully expect this interval to shrink further.

![Knish.IO Organism Diagram][organism]

---

# Model: Molecule

Transactions issued on Knish.IO are composed of a number of micro-transactions (Atoms). In order to make sense of where the information is coming from and where it’s going, Atoms are packaged into a grouping called a “Molecule”.

When new Molecules are being recorded to the ledger, the Atoms that compose them are either accepted or rejected all at once, never separately.

![Knish.IO Molecule Diagram][molecule]

Molecules form **bonds** with other Molecules to help secure the ledger in an asynchronous fashion. Each Molecule MUST bond with other Molecules before it can be accepted into the ledger. This is performed using the **tip selection algorithm** and **molecular bonding algorithm** described further herein.

The higher the percentage of valid molecular bonds (direct or indirect) after performing the tip selection algorithm a specific number of times, the more confidence the ledger has regarding a Molecule’s validity.

Because nodes bond incoming Molecules in an asynchronous fashion, consensus is achieved by observing *intersections* between multiple nodes’ states, thus maintaining byzantine fault tolerance even in the case of conflicts between two sets of nodes.

## Concept: Molecular Cascades

The set of all Molecules that have established bonds to a particular Molecule *M* directly is referred to as a **cascade**. 

The maximum number of cascades from *M*<sub>i</sub> up to a tip Molecule represents its “depth”, *d*<sub>i</sub>. 

The minimum number of cascades down from *M*<sub>i</sub> to *M*<sub>origin</sub> represents its “height”, *h*<sub>i</sub>.

For *V*-isotope Molecules, a “local height” may also be determined by counting the minimum number of cascades down from *M*<sub>i</sub> to the Token creation Molecule, *M*<sub>creation</sub>.

![Knish.IO Cascade Diagram][cascade]

Cascades are used to verify the integrity of the ledger and reference neighboring Molecules that are referenced by or are referencing the given Molecule.

---

# Model: Atom

A Molecule contains at least one Atom. Each Atom comes in one of several single-purpose isotopes, allowing the Atom to be tuned to a particular use case. These isotopes describe the “vocabulary” of the Knish.IO protocol.

Supported atomic isotopes, as of the writing of this document, are:

- **Value** (*V*) - moves fungible scalar value, non-fungible unit objects, or partially fungible batches of scalar value from one Wallet to another. *V*-isotope Atoms always come in triples: the first Atom removes Tokens from the source Wallet; the second adds Tokens to the destination Wallet; and the third places the remaining Tokens into a new Wallet that will replace the first.


- **Buffer** (*B*) - identical functionality to *V*, but operating on *Buffers* rather than *Wallets*, typically used for peer-to-peer decentralized exchange and Token staking scenarios.


- **Metadata** (*M*) - assigns structured metadata (key:value pairs) to some arbitrary Meta Asset instance referenced by a class and unique identifier.


- **Creation** (*C*) - declares the creation of a new virtual asset, which can take the form of a Token, a Wallet, or a Meta Asset class.


- **Fusion** (*F*) - fuses a full set of non-fungible Token units covering each possible zone assignment, into a single non-fungible unit containing a merged set of metadata from its component units. The component units are irreversibly transformed through this process.


- **Rules** (*R*) - used to describe granular policies (read, write, self-destruct, and logging) associated with some Meta Asset, as well as automation workflows and callbacks.


- **Peering** (*P*) - used for initiating Peer Invites, coordinating handshakes between Peers for the purpose of coordinating ledger states across diverse machines.


- **Identity Continuity** (*I*) - (also called “ContinuID”) used for establishing a chain of personal custody between multiple Molecules. Each transaction signed with the `USER` Wallet requires that one *I* isotope is always present.


- **User Access** (*U*) - used for requesting and managing personal authorization tokens for accessing privileged ledger activities and data.


- **Token Request** (*T*) - used to request a specific type of Token from a federated node. If requirements are fulfilled, the node will sign and issue a *V*-isotope Molecule completing the transfer.


- **Append Request** (*A*) - used to request modifications of metadata from a federated node. If requirements are fulfilled, the node will sign and issue an *M*-isotope Molecule updating the requested metadata.

The first Atom in a Molecule is considered the “signing Atom” and is critical in the signing and validation process. For any Molecules that involve the movement of Tokens, the first Atom must be signed with the Wallet (or Buffer) from which Tokens are being withdrawn; For all other types of Molecules, the first Atom must be signed with the system-reserved `USER` Token Wallet.

*V*-isotope Molecules are always signed with the Token-bearing Wallet in the first *V*-isotope Atom:

![Knish.IO V-Isotope Molecule Diagram][vatom]

*M*-isotope Molecule are always signed with the `USER` Token Wallet designated in prior *I*-isotope:

![Knish.IO M-Isotope Molecule Diagram][matom]

*I*-isotope Atoms and the third *V*-isotope Atoms serve an identical purpose: to establish the next Wallet in the user’s custody. However, in the case of *V*-isotope Atoms, Token remainder balance is also shifted to the new Wallet.

---

# Model: Cell

Molecules are always associated with the Cell serving the specific decentralized application or dApp that originated the transaction, sharding the overall collection of data stored on the Knish.IO ledger around application-specific domains to ensure optimally scalable performance without sacrificing decentralization. Molecules and the process of executing their atomic payloads behave according to the parameters of their Cell, established by the custodial entity operating the dApp.

![Knish.IO Cell Diagram][cell]

Parameters that can be controlled at the Cell level include (but are not limited to):

- *Hashing Algorithm:* SHAKE256 (SHA3-based variable-length XOR function) [3]
- *Encryption Algorithm:* Elliptic Curve ED25509 [4]
- *Wallet Alphabet:* BASE64

---

# Model: Wallet Bundle, Wallet, Shadow Wallet, Buffer

## Wallet Bundle

A Wallet Bundle represents a Knish.IO user identity. It is the collection of all the user's Wallets, Shadow Wallets, Buffers, Molecules, Meta Assets, and reputation. True to its name, it is very much a "Bundle of Wallets".

When sending Tokens to a user, their Wallet Bundle may be used in lieu of a recipient Wallet address.

Wallet Bundles are identified by a unique 64-character identifier called a `bundleHash`, which is used interchangeably with a Wallet address for sending Tokens to a third party.

Every virtual object created on the ledger, including Tokens, Meta Assets, and even Molecules and their Atoms, is tied to the Wallet Bundle that created it, ensuring that reputation and continuity of identity is maintained throughout the objects' lifecycles.

Individuals may maintain more than one Wallet Bundle, to ensure that aspects of their digital life do not undesirably bleed over from one domain into another.

![User Identity via Wallet Bundles][identity]

## Wallet

Wallets are virtual buckets for storing assets (Tokens) and WOTS+ keys for signing Molecules or encryption keys for encrypting data, and may be employed in the more traditional sense (users sending and receiving cryptocurrency payments or NFTs), or in more exotic use-case-specific ways (for example, facilitating peer-to-peer hyper-secure communications via constantly-changing encryption keys).

While a WOTS+ private key can be used to sign any Molecule, repeat usages of a key will be rejected by the ledger because each use exposes exactly 50% of the key, allowing an attacker to compromise signed assets should key re-use be allowed. Because of this single-use nature of the private keys, it becomes necessary to regenerate a Wallet with a new private key after every transaction.

When a Wallet is regenerated, it can no longer sign Molecules using the same WOTS+ key. This is an effective countermeasure against a possible compromised Wallet (which is effectively unusable if it has regenerated), as well as against a possible attempt to perform a double-spend transaction (due to the asynchronous nature of the consensus algorithm combined with additional bonding requirements for multiple low-confidence Molecules drawing from the same Wallet Bundle).

![Knish.IO Bundle Diagram][bundle]

## Shadow Wallet

The process of Wallet regeneration produces a new Wallet, and eventually there may be dozens, if not hundreds of Wallets kept by any single user. This is why Wallet Bundles are used as an abstraction layer and route Tokens to the latest, pristine Wallet address.

However, if no such pristine Wallet is available to route Tokens into, a Shadow Wallet is created instead. Shadow Wallets are temporary Wallets with no keys (therefore no `position` or `wallet_address` fields defined), only a Wallet Bundle assignment.

Shadow Wallets can be used for deposit routing, however no transactions may be signed by them, and therefore any received Tokens may not be used until the Shadow Wallet is "claimed". The process of claiming a Shadow Wallet is equivalent to retroactively creating a Wallet for the given Token, which will automatically receive any accumulated balance from the Shadow Wallet.

![Claiming a Shadow Wallet][shadow]

## Buffer

Buffers are specialized Wallets used for coordinating automation allowances: fungible, non-fungible, or partially-fungible assets may be buffered for automated peer-to-peer exchange and staking use-cases, or shifted out of previously allocated Buffers back into their "normal" Wallets.

Unlike Wallets, Buffers cannot transfer Tokens to third-parties, other than via server-side automation, so while they can be used to sign transactions, they are limited to those that move Tokens out of a Buffer and into the same user's Wallet.

On the other hand, buffered assets can take advantage of rich server-side automation capabilities: for example, Knish.IO comes with a robust trade matching engine connecting buffered trades and fulfilling Token swaps.

![Knish.IO Decentralized Exchange Buffer Trade Matching][matching]

---

# Concept: ContinuID

Continuity of Identity (or ContinuID, for short) is a key principle of Knish.IO transactional integrity and data ownership. The simplest way to think about ContinuID is like a relay race: a team of runners passes a baton from one to the next to ensure they get to the finish line first.

In this example, the "team" is the Wallet Bundle, the "runners" are Wallets, and the baton is the designation of the next Wallet that must take over. Passing the baton to a racer from another team, or to a racer out of order, is strictly prohibited.

In practical applications, there are 2 primary ways ContinuID is utilized:

1. **Wallet Remainders:** To ensure that the integrity of Wallets remains secure after every transfer, the Tokens' owner designates the next Wallet in line to receive leftover Tokens as part of the Wallet regeneration process.


2. ***I*-Isotope Atoms:** For non-Token transactions involving the reserved `USER` Wallet, the next `USER` Wallet in line is designed by an *I*-isotope Atom at the end of the Molecule.

The goal is to pass the baton to the next Wallet, as defined by the user, and enforce this chain of custody. If any Molecule arrives signed by a Wallet which was not designated in the previous Molecule via one of the above mechanisms, the Molecule will be automatically rejected.

![Illustration of ContinuID Relay Race][continuid]

---

# Model: Token

Tokens are virtual representations of a particular asset or utility, and may represent fungible, non-fungible, and partially-fungible assets. Tokens may be traded, sold, or utilized as part of a digital ecosystem or application.

Tokens are stored in users’ Wallets. Each Wallet address can accommodate only a single type of Token, so a user holding multiple Tokens would have a Wallet address for each of them, each with its own position for signing Molecules.

## Fungibility

Fungibility is defined as the ability of an asset to be exchanged for other individual assets of the same type. Knish.IO Tokens have a `fungibility` property that defines their fungibility behavior, and falls into one of the following categories:

- **Fungible:** Money is fungible: a certain amount of pennies can be exchanged for the same amount of other pennies - it doesn't matter which specific pennies you receive, as long as the amount is equal. This is the "default" Token behavior, and is appropriate for commerce, loyalty points, Token-gated moderation, and other use-cases where some amount of Tokens is expended or earned.


- **Non-Fungible:** Non-fungible assets, on the other hand, are different from one individual unit to another. For example, a Lebron James basketball card is not the same as a Stephen Curry basketball card, even though they are both basketball cards. Various artwork NFTs have been a popular way of leveraging this type of Token, but there are many other uses for it in supply chain, e-voting, and more.


- **Stackable:** Knish.IO introduces a third fungibility property called "stackable" - also sometimes called "partially fungible". This refers to assets that exhibit properties of both fungible, and non-fungible assets. If I wanted to sell joint ownership in my Lebron James basketball card to 10 different people, I would issue 10 units of a "stack" representing the basketball card (which itself is non-fungible), but with 10 units (each of which is fungible). The same Token supply might also contain a stack for a Stephen Curry basketball card, too, and any others, without commingling their individual units.


- **3D Mesh (in development):** The ability to measure and manipulate Token "amounts" using mutable 3D Meshes is conveyed by the "mesh" fungibility mode. Mesh Tokens record 3D mesh coordinates in the form of metadata, and an integrated geometry engine helps prevent collisions and ensure that Tokens are split and transmitted fairly. This type of Token is appropriate for land rights and other geological / topographical use-cases.

## Supply

Whether a Token's supply can be replenished after its initial minting is determined by the `supply` property.

There are also two supply replenishment modes supported:

1. **Replenishable** Tokens can be re-issued as needed after creation, and there is no limit on the maximum supply amount.


2. **Non-Replenishable** Tokens cannot be re-issued, so the initial supply minted will represent the final maximum supply amount.

## Bindability

The ability of Tokens to get "stuck" to a Wallet is defined by the Token's `bindability` property, which contains a scalar value representing the number of times the Token may be transferred to another user by someone who is not the originator of the Token.

Every time a bindable Token is transferred, the length of the transfer chain is compared with the `bindability` value to determine whether the transfer is permitted.

For example, if Alice mints a Token with a `bindability` setting of `2`, she can transfer it to Bob (chain length: `0`), who transfers it to Charlie (chain length: `1`), who gives it to David (chain length: `2`), but now David cannot give it anyone else because the chain length will exceed the maximum allowed length.

This type of Token is appropriate for use in credentialing scenarios: for example, if Alice takes a college class and receives a credit in the form of a bindable Token with a maximum chain length of `0`, she will not be able to transfer the credit to Bob - he will need to take the class himself.

Voting is another scenario where bindable Tokens are essential: If Alice gets a "vote" Token with a maximum chain length of `1`, she can give it to her favorite candidate, and that's where it will permanently stay to be counted. If she gives her vote to someone else to vote on her behalf, they will not be able to: the Token will be bound to their Wallet permanently.

## Fusible Fragments and NFT Fusion

The ability for non-fungible Token units to be "fused" together into a single, brand new, Token unit is described by the `fragmentZones` property. This is a scalar value that describes the unique number of fragment zones associated with the Token.

Each individual non-fungible unit must be assigned a `fragmentZone` value where `0` < `fragmentZone` &le; `fragmentZones` of the parent Token.

When a user holds the full set of possible `fragmentZone` variants, they are able to fuse these distinct units into a single "fused unit" containing a combined set of metadata from its constituent units, via the *F* isotope.

NFT Fusion is appropriate for use with various mutable forms of digital collectibles, such as collectible creatures (where each `fragmentZone` setting represents a specific body part) and gaming NFTs (fuse ingredients together to craft an item, for example).

---

# Algorithm: Wallet Key Generation

Given the biometric secret *S*, an integer `position`, and a string `token` argument, this algorithm derives a 4096 byte (2048 character) hexadecimal private key and 128 byte (64 character) hexadecimal Wallet address.

1. Convert `position` into hexadecimal notation
2. Add the converted hex `position` to *S*. The resulting hexadecimal string will be our “indexed key”, *K*<sub>index</sub>
4. Create a SHAKE256 sponge
5. Absorb *K*<sub>index</sub> into the sponge
6. If `token` is provided, absorb `token` into the sponge as well
7. Squeeze a 4096 byte (2048 character) hex value from the sponge and designate it as the "intermediate key" *K*<sub>int</sub>
8. Reset the sponge
9. Absorb *K*<sub>int</sub>
10. Squeeze a 4096 byte (2048 character) hex value from the sponge and designate it as the "private key" *K*<sub>k</sub> 

![Wallet Key Generation][walletkey]

---

# Algorithm: Wallet Address Generation

Once we have obtained the Wallet private key *K*<sub>k</sub>, we can use it to derive a Wallet address for this key.

1. Subdivide *K*<sub>k</sub> into 16 fragments of 256 bytes (128 characters) each
2. Create a SHAKE256 sponge for digest *D*<sub>k</sub>
3. Iterate across each fragment as *S*<sub>i</sub>
    - Create a SHAKE256 sponge for *S*<sub>i</sub>
    - Iterate 16 times:
        - Absorb *S*<sub>i</sub>
        - Squeeze a hashed 256 byte (128 character) hexadecimal string out of the sponge
        - Reset sponge
    - Absorb the hashed *S*<sub>i</sub> above into the digest sponge
4. Squeeze the digest sponge to retrieve a 4096 byte (2048 character) digest *D*<sub>k</sub>
5. Reset the digest sponge
6. Absorb *D*<sub>k</sub> into the sponge
7. Squeeze a 128 byte (64 character) string out of the sponge that will represent the Wallet address for this private key.

![Wallet Address Generation][address]

---

# Model: Meta Asset

Knish.IO provides for dynamic, virtual data structures called Meta Assets. Specific Meta Assets are identified via a combination of `metaType` and `metaId` properties, and can have an arbitrary amount of structured metas storing key/value pairs of properties, as contributed by *M*-Molecules.

Meta Assets can be used to store information about other core Knish.IO models as well, like Wallet Bundles, Wallets, Tokens, and more. Leveraging Meta Assets in a dApp allow for using the Knish.IO ledger in a very similar fashion to Google Firebase - as a true application development platform.

Below is an example Javascript SDK call to create a new `LicensePlate` record with identifier `ABC123`:

```javascript
const response = await client.createMeta( {
      metaType: 'LicensePlate',
      metaId: 'ABC123',
      meta: {
        make: 'Toyota',
        model: 'Prius',
        year: '2013'
      }
    } );
```

and here is how you might query the `LicensePlate` schema to get metadata for all license plates newer than the year 2010:

```javascript
const response = await client.queryMeta( {
      metaType: 'LicensePlate',
      filter: [
        {
          key: 'year',
          value: '2010',
          comparison: '>'
        }
      ]
    } );
```

## Concept: Custom Schemas

Knish.IO generally supports arbitrarily-structured metadata (no limitations on which metadata `key` values are used), but sometimes it may be advantageous to define a fixed schema to which data must conform (a specific list of `key` values and their respective structure).

There are 2 ways of accomplishing this:

1. **Define your own schema:** Custom schema structure may be provided during meta asset creation when setting `metaType` to "MetaType" and `metaId` to the name of the new meta asset class. The `meta` object will supply the schema structure. Subsequent creation of meta assets of the new meta asset class will have to adhere to the defined schema.


2. **Reference an external schema:** Knish.IO can be extended to support external schemas from [Schema.org](https://schema.org/), [GS1](https://gs1.org), [NIEM](https://www.niem.gov/), and others.

---

# Algorithm: Molecule Construction

When a client initiates a new transaction, it must construct and correctly sign a Molecule to represent that transaction and all of its relevant data, before sending it to a receiving node which will then cryptographically verify such data to ensure its validity, and (in certain cases) ensure that third-party observers are not able to violate the privacy of the participants.

This procedure involves the generation of a private key for the next available atomic position, the hashing of atomic data to generate a molecular hash, the creation of a WOTS+ signature for the Molecule, and finally, the creation of a new quantum-resistant Wallet to receive any leftover Tokens remaining, or to serve as the user's next Molecule's signatory.

1. Client obtains biometric secret
2. Client generates atomic structure to fulfill transaction and shift remaining balance
3. Client creates a molecular hash of the Atoms
4. Client creates OTS fragments for each Atom
5. Client broadcasts new Molecule to the node
6. Node verifies the Molecule's signature and hash
7. Node performs random walk to select bonds
8. Node verifies the primary bonds' signatures and hashes
9. Node verifies the atomic payloads of the new Molecule and its bonds
10. Node broadcasts bonded Molecule to peers

## Step 1: Client obtains biometric secret

Each Molecule must be approved by the sender, and to that end an external biometric solution may be utilized to transform the sender’s face, fingerprints, and/or voice print (or a combination of the above) into a unique keypair.

Alternatively, other forms of authentication may be used, including OAuth, NFC, smart cards, and other types of credentials.

The actual method of biometric collection depends on use case implementation, but the result is always the same: a 2048-symbol hexadecimal string.

This biometric secret, *S*, may then be used as a seed to generate an infinite number of one-time-use private keys for the new quantum-resistant Knish.IO Wallet. The public key becomes the Wallet address.
Each private key may only be used securely once, and neither  nor the Wallet private key needs to necessarily be stored in order to function correctly.

![Knish.IO Biometric UX][biometrics]

## Step 2: Client generates atomic structure

In this step we must generate all the necessary Atoms for Molecule *M* to fulfill the requirements of the transaction.

1. Build the primary Atom (lowest index in the Molecule). This normally represents a destructive transaction from the sender’s Wallet.
2. Build the secondary Atom (next index). This normally represents a constructive transaction to the recipient’s Wallet.
3. Build any additional Atoms necessary to fulfill the requirements of the transaction (for example, utilizing the sender’s Wallet to fund multiple recipients with one transaction, or delivering message metadata to the recipient).
4. The last *V* isotope Atom would reference a newly-created remainder Wallet, which may receive any excess Tokens not spent in the first Atom.

You will end up with a series of Atoms like this (*V* isotopes shown in example), capped off with an *I* isotope to establish chain of custody:

![Knish.IO V and I Atom Arrangement][atoms]

## Step 3: Client creates a molecular hash of the Atoms

Now that the Atoms are ready, the Knish.IO SDK will hash them together to produce a molecular hash. This is later used to ensure that each Atom in fact belongs to the Molecule and no data or instructions have been added, removed, or otherwise tampered with along the way.

1. Arrange each Atom *A*<sub>1</sub>, ..., *A*<sub>i</sub> in *M* by order of their position. Denote position as *k*
2. Create a SHAKE256 sponge instance for *M*
3. Iterate across each Atom as *A*<sub>k</sub>
4. Absorb each of *A*<sub>k</sub>’s fields into the sponge in this specific order: `position`, total number of Atoms, `wallet_address`, `isotope`, `token` (if present), `value` (if present), and `created_at`
5. Squeeze *M*’s sponge to produce a 128 byte (64 character) hexadecimal string
6. Convert the string into Base 17 (numbers 0-9 and letters ‘a’ through ‘g’), which is denoted by molecular hash *H*<sub>m</sub>
7. Assign *H*<sub>m</sub> to *M*’s `molecular_hash` field
8. Iterate across each Atom as *A*<sub>k</sub>
9. Assign *H*<sub>m</sub> to *A*<sub>k</sub>’s `molecular_hash` field

## Step 4: Client creates OTS fragments for each Atom

In order to verify that this Molecule was in fact issued by the owner of the originating Wallet, we need to prepare a correct `ots_fragment` field.

The **Wallet Key Generation Algorithm** helps us derive the private key *K*<sub>k</sub> given the first Atom's `token` and `position`. We will need it here.

1. The Base-17 `molecular_hash` field must be enumerated as an array of integer values between -8 and 8, which we'll call *H*<sub>m</sub>:
```
Base-17:   0   1   2   3   4   5   6   7   8   9   A   B   C   D   E   F   G
Integer:  -8  -7  -6  -5  -4  -3  -2  -1   0   1   2   3   4   5   6   7   8
```
2. Normalize *H*<sub>m</sub> to ensure that the total sum of all symbols is exactly zero. This ensures that exactly 50% of the WOTS+ key is leaked with each usage, ensuring predictable key safety:
    - The sum of all symbols within Hm shall be presented by &sum;<sub>m</sub>
    - While &sum;<sub>m</sub> != 0 iterate across that set’s integers as *H*<sub>m</sub>[*i*]:
        - If &sum;<sub>m</sub> >= 0 and *I*<sub>m</sub> > -8, let *H*<sub>m</sub>[*i*] = *H*<sub>m</sub>[*i*] - 1
        - If &sum;<sub>m</sub> < 0 and *I*<sub>m</sub> < 8, let *H*<sub>m</sub>[*i*] = *H*<sub>m</sub>[*i*] + 1
        - If &sum;<sub>m</sub> == 0, stop the iteration
4. Subdivide *K*<sub>k</sub> into 32 segments of 128 bytes (64 characters) each
5. Create a SHAKE256 sponge
6. Create empty string *O*
7. Iterate across each segment of *K*<sub>k</sub> as *K*<sub>i</sub>
    - Iterate a number of times equal to 8 - *H*<sub>m</sub>[*i*]
    - Absorb *K*<sub>i</sub> into the sponge
    - Squeeze out a 128 byte (64 character) string and append it to *O*
8. *O* should now be a 4096 byte (2048 character) string
9. Divide *O* into a number of string chunks equal to the number of Atoms in the Molecule, arranged in order of `position`
10. Write the ots chunk into each Atom's respective `ots_fragment` field

## Step 5: Client broadcasts new Molecule to the node

Knish.IO nodes rely on a GraphQL-based API to work with client appliations, so a GraphQL mutation would typically need to be sent to the node with the signed Molecule, as per the following mutation structure:
```
mutation MoleculeMutation($molecule: MoleculeInput!) {
  ProposeMolecule(
    molecule: $molecule,
  ) {
    molecularHash,
    cellId,
    bundle,
    status,
    createdAt,
    receivedAt,
    processedAt,
    broadcastedAt
  }
}
```
There is no recommended GraphQL client. This choice is up to the individual projects and integrators. Most Knish.IO SDKs supply an out-of-the-box GraphQL client for you to use.

Knish.IO SDKs perform a number of validations on Molecules prior to broadcast, however, if you are foregoing an SDK, and building an implementation from scratch, it may be advantageous to verify the `ots_fragment` and `molecular_hash` prior to sending a mutation, using the same verification algorithms as the node, below.

## Step 6: Node verifies the Molecule's hash and signature

A node will receive a GraphQL MoleculeInput object containing the Molecule itself, its Atoms, and any relevant meta that may be conveyed by the transaction.

To verify the validity of the Molecule, the node needs to transform the collection of `ots_fragment`s and the `molecular_hash` into a string that will perfectly match the `wallet_address` on the primary Atom.

1. Run the *Molecular Hash Algorithm* (step 3 above) and compare the result with the `molecular_hash` field on the Atoms. If it matches, the atomic payload is intact.
2. Arrange all Atoms in order of ascending `position`, and concatenate their `ots_fragment` fields into a single string, *O*
3. The Base-17 `molecular_hash` field must be enumerated as an array of integer values between -8 and 8, which we'll call *H*<sub>m</sub>:
```
Base-17:   0   1   2   3   4   5   6   7   8   9   A   B   C   D   E   F   G
Integer:  -8  -7  -6  -5  -4  -3  -2  -1   0   1   2   3   4   5   6   7   8
```
4. Subdivide *O* into 32 segments of 128 bytes (64 characters) each
5. Create a SHAKE256 sponge
6. Create empty string *D*
7. Iterate across each segment of *O* as *O*<sub>i</sub>
    - Iterate a number of times equal to 8 + *H*<sub>m</sub>[*i*]
        - Absorb *O*<sub>i</sub> into the sponge
    - Squeeze a 128 byte (64 character) string and append it to *D*
    - Reset the sponge
8. Absorb *D* into the sponge
9. Squeeze a 4096 byte (2048 character) digest *D*<sub>k</sub>
10. Reset the sponge
11. Absorb *D*<sub>k</sub> into the sponge
12. Squeeze a 128 byte (64 character) string out of the sponge
13. The string will match the primary Atom's `wallet_address` if all is well

## Step 7: Node performs random walk to select bonds

Once a Molecule's payload and signature have been verified, the node must choose a number of prior Molecules in the local ledger to bond this Molecule with, while performing additional checks on the bond targets.

The process of bonding Molecules in Knish.IO behaves differently depending on the primary atomic isotope involved in the proposed Molecule:

- *V* and *B* Molecules may ONLY bond with Molecules associated with the same Token
- *C* Molecules may ONLY bond with other *C* Molecules, or a root Molecule
- *M* Molecules may ONLY bond with *M* or *C* Molecules describing the same `metaType` and `metaId`, or a root Molecule
- *P* Molecules may ONLY bond with the *P* Molecule representing the peer to which we are bonding, or a root Molecule
- *R* Molecules may ONLY bond with *R*, *M*, or *C* Molecules describing the same `metaType` and `metaId`, or a root Molecule
- The first Molecule on the ledger does not need to bond, as there is nothing to bond with, and is considered the global origin

A proposed Molecule *M* must bond with a variable number of tip Molecules in order to be accepted by Knish.IO, depending on several factors described herein.

The first two tips - {*M*<sub>1</sub>, *M*<sub>2</sub>} - are referred to as the “primary bond candidates”. All subsequent tips - {*M*<sub>3</sub>, ... , *M*<sub>t</sub>}- are referred to as “secondary bond candidates”. There may be no repeats across either set.

Each member of the set {*M*, *M*<sub>1</sub>, *M*<sub>2</sub>} MUST originate from a unique Wallet Bundle (no repeat owners).

Conversely, each member of {*M*<sub>3</sub>, ..., *M*<sub>t</sub>} MUST originate from the same Wallet Bundle(s) referenced in {M1, M2}, and are treated as an extension of the primary set when validating correctness. This helps ensure that when multiple tips are being issued in rapid succession by the same identity, *M* is able to validate them as single unit and secure the cell against possible double-spend attacks.

A **Markov Chain Random Walk** (Weighted Monte Carlo Random Walk) procedure must be repeated until the two primary bond candidates are selected:

1. Select the chronologically nearest root Molecule *M*<sub>root</sub>. This is a highly trustworthy Molecule which meets ALL of the following criteria:
    - *M*<sub>root</sub> is NOT originating from the same Wallet Bundle as *M* any previously selected primary bonds
    - *M*<sub>root</sub> does NOT have a `status` of "rejected"
    - Isotope-specific bonding requirements (above) are maintained
    - *M*<sub>root</sub> has a `confidence` of 95% or higher
    - If no acceptable *M*<sub>root</sub> is found above, choose *M*<sub>origin</sub> as *M*<sub>root</sub>
2. Choose a Molecule *M*<sub>c</sub> out of *M*<sub>root</sub>'s cascade to "walk" to.
    - If a total of *p* > 1 Molecules are present in the cascade, then the probability of selecting a *M*<sub>c</sub>, with a `confidence` of *I*<sub>c</sub>, is equal to ![Markov Chain Random Walk Probability][mcrw]
    - This produces a range of probabilities depending on the relative `confidence` of *M*<sub>c</sub> compared with other Molecules in the cascade, and ensures that even less-prominent Molecules have a chance of being selected for analysis.
    - If *M*<sub>c</sub> has the same Wallet Bundle as *M* or any primary bond candidates thus far, it is ignored (can't walk over your own Molecules).
    - If *p* == 1, walk to the sole available *M*<sub>c</sub>.
3. Repeat step 2 with *M*<sub>root</sub> = *M*<sub>c</sub> until *p* == 0 or no further valid walks are possible due to the above constraints.
4. Perform a throttle check on the selected *M*<sub>c</sub> to ensure that the same Wallet Bundle isn't generating too many new Molecules:
    - Probability of spontaneous rejection can be represented by comparing *N*<sub>c</sub> = countOverTime ( *M*<sub>c</sub>, 5 seconds ) to an upper limit of 100 Molecules per 5 seconds:
    
    ![Rejection Probability][rejection]

    - Should rejection occur at this stage, the random walk process must be restarted to choose a different tip.
    - Function countOverTime ( *M*, *t* ) returns the number of Molecules submitted by Wallet Bundle of Molecule *M* within the specified number of seconds *t* of *M*.
5. Choose this final *M*<sub>c</sub> as the selected tip for analysis.

At this point, the set of primary bond candidates will have either {*M*<sub>1</sub>} or {*M*<sub>1</sub>, *M*<sub>2</sub>}. 

We must now check if secondary bond candidates are required to help protect the cell from possible double-spend attacks. The number of secondary bond candidates required is defined by the pseudocode below:

![Secondary Bond Equation][secondary]

The *GetTips* function above returns a collection of all tip Molecules originating from the same Wallet Bundle as the supplied set of Molecules, exclusive of the arguments themselves.

The full set of bond candidates, {*M*<sub>1</sub>, *M*<sub>2</sub>, ..., *M*<sub>t</sub>}, needs to be checked for validity and finalized.

## Step 8: Node verifies the primary bonds' hashes and signatures

For each of the primary bond candidates {*M*<sub>1</sub>, *M*<sub>2</sub>} that have a `status` of "received" - Molecules that were verified by other nodes and sent to the current Knish.IO node as a peer - we need to make sure they were properly signed, and double-check the peer's work.

Simply repeat Step 6 for each of the bond candidates. If the verification algorithm in Step 6 returns false, reject the bond candidate and re-run the bond selection algorithm.

## Step 9: Node verifies the Molecules' atomic payloads

The Molecule *M* and all of its bonds {*M*<sub>1</sub>, ..., *M*<sub>t</sub>} needs to be verified for integrity according to its type, using the verifying node’s currently available local data as reference. The verification process may group multiple unverified Molecules together to ensure that possible double-spend attacks are much harder to execute:

**For *V* and *B* Molecules:**

1. Collect all primary Atoms in {*M*, *M*<sub>1</sub>, ..., *M*<sub>t</sub>} featuring the same Token *T* and Wallet Bundle *B*, and combine their aggregate value as *V*<sub>total</sub>. 
2. Check to ensure that GetWalletTokenBalance( *B*, *T* ) >= *V*<sub>total</sub>, meaning there is enough Tokens to cover not just *M*, but any secondary bond candidate as well. If there is not, reject *M*.

**For *M* Molecules:**

1. Check to ensure that recipient object *O* (`meta_type` and `meta_id` fields supply the polymorphic reference) has no privilege restrictions for *B* to manipulate its metadata. If a restriction is found, reject *M*.
2. In case *M* is a revocation request, check to ensure that the revoked metadata actually exists to be revoked. If not, reject *M*.

**For *C* Molecules:**

1. Check to ensure that *B* has no privilege restrictions to create the type of asset requested. If a restriction is found, reject *M*.

**For *P* Molecules:**

Atomic payload check not needed.

**For *R* Molecules:**

1. The `meta_type` and `meta_id` fields supply the polymorphic reference to the target being reported. Check to make sure this asset has not been previously reported by *B*. If it has been, reject *M*.

## Step 10: Node broadcasts the verified Molecule to its peers

After successfully completing the previous steps, the node can safely add bonds between *M* and primary bond candidates {*M*<sub>1</sub>, *M*<sub>2</sub>} (no actual bonds are formed to secondary candidates) and broadcast *M* and its bonds to peer nodes. 

Normally all Molecules are broadcast to all peers, with the exception of those intended for P2P messaging - in which case, they will only get broadcast to the specific peer which matches the Wallet Bundle the message is addressed to.

See **Peering Algorithm**

## Rejection ##

Any Molecule *M* upon which the local integrity check is aborted for any reason must be properly marked as such with a ‘rejected’ `status`, and the process must recurse through any Molecule(s) that are bonded to *M* to invalidate any sub-DAGs forming beyond this Molecule.  On abort, the set of secondary bond candidates is cleared, and the tip selection algorithm begins anew to choose a replacement candidate Molecule.

---

# Algorithm: Peering

Knish.IO uses a hybrid peering algorithm that combines the use of *P* Molecules to announce node presence, and local peer reputation tables for a transparent, secure, and efficient process for discovering, adding, and maintaining lists of peer nodes without exposing the topology of the distributed mesh network formed by them.

Because issuance of a *P* Molecule is required to initiate peering, it becomes exponentially more difficult to mount a successful Sybil attack, especially when biometric authentication is involved - each node is tied to a specific biometric secret that is difficult to forge and maintains a global reputation.

Each node may have up to 100 peers, though starting at 50, each broadcast by the node will cause the slowest / least reliable peers to be dropped without replacement.

![Knish.IO Peering Algorithm][peering]

## Discovering Peers

The first peer a node connects to must be ‘bootstrapped’ - manually or automatically added in the course of an interaction.

For added trust, visiting any **WishKnish Storefront** or other *‘Powered by Knish.IO’* deployment in a web browser allows any user to validate the authenticity of the node by clicking the Knish.IO logo. The resulting page will provide reputational information about this node, as well as instructions for manually bootstrapping it, if so desired.

Should the user choose to interact with this node by partaking in a transaction, they will become the user’s node’s first peer automatically, without any action needed by the user.

Bootstrapping causes a new node *N* to issue a *P* Molecule to the prospective peer node, *N*<sub>peer</sub>. *N*<sub>peer</sub> receives *P*, verifies it (as per the verification algorithms described previously), and broadcasts to their existing peers {*N*<sub>a</sub>, ..., *N*<sub>z</sub>}. The peers, upon receiving *P*, verify it as well - however, they do NOT re-broadcast it any further - the topology of the local mesh surrounding this particular set of nodes is only known to them.

The new node, *N*, is now present in *N*<sub>peer</sub>’s list of peers with an “accepted” status and will receive any new Molecules successfully bonded by *N*<sub>peer</sub>.

Thereafter, nodes can be added either automatically (broadcast from *N*<sub>peer</sub> and other peers of *N*) or continue to be manually added by *N*, depending on need.

Full nodes will not broadcast to nodes operating in *Lite Mode* (more on this below), so the bootstrap process works differently: if a new Lite Mode node is bootstrapping another Lite Mode node, the new node will receive a random peer from the second node’s peers table. If the new Lite Mode node is instead bootstrapping a full node, that full node is added to the new node’s peers table.

The Lite Mode node’s peers table is used to send out active requests for consensus, rather than passively receiving new Molecules. 

## Broadcasting to Peers

When a Molecule *M* has been successfully bonded with no issues, it is ready to be broadcasted to other peers.

The broadcast process is repeated for each active peer present the local node’s peers table. Each peer receives a GraphQL API message to its node address, and proceeds to the broadcast receipt procedure below.

The response returned is checked for status (whether the peer has accepted *M* or not), and measured for latency.

*P* Molecules that are received from a peer are NOT re-broadcast to other peers even if they are valid to avoid exposing global mesh topology to potential attackers.

## Automatic Peer Cleanup

Depending on the number of peers a node has, there is a random chance that each new broadcast will cause the slowest / least reliable peer to be removed or replaced.

The specific rules are as follows, with the number of peers denoted as *p*:

1. For *p* < 25: 10% chance that a random peer address will be selected from all locally known *P* Molecules, and contacted for a handshake; If the response speed is faster than the slowest available peer, the new peer will take its place in the peers table.
2. For 25 <= *p* < 50: 25% chance that a random peer address will be selected from all locally known *P* Molecules, and contacted for a handshake; If the response speed is faster than the slowest available peer, the new peer will take its place in the peers table.
3. For 50 <= *p* < 100: 5% chance that the slowest peer in the table will be dropped without replacement.
4. For *p* >= 100: peering requests will be rejected and no new peers may be added at this point.

In general, if a peer fails to respond within a reasonable time, its `retries` field is incremented after each consecutive failure, and after 5 failed broadcasts, the peer is marked as rejected.

---

# Receiving Broadcasts

When a peer broadcasts a new Molecule, Knish.IO ensures that the peer is not attempting to pollute the ledger with dummy Molecules or form a parasite chain by completing the following steps prior to accepting the new Molecule and attempting to bond it into the ledger:

## Step 1: Throttle check

The purpose of this procedure is to ensure that peer *P* sending Molecule *M*<sub>rec</sub> isn’t spamming us by looking at the number of recently received Molecules from *P*, as provided by the `received_molecules` collection.

This set of Molecules shall be represented as ![Set of Received Molecules][mrec].

Probability of spontaneous rejection of the broadcast shall be represented by comparing *N*<sub>peer</sub> = countOverTime ( *M*<sub>rec</sub>, 5 seconds ) to an upper limit of 30 Molecules per 5 seconds: ![Probability of Spontaneous Rejection][mrejection]

Should rejection occur, *M*<sub>new</sub> will be added to the `rejected_molecules` collection.

## Step 2: Peer integrity check

This step is designed to prevent repeated attempts at submitting spam Molecules by peer *P*, and need only be attempted if Step 1 fails.

We will consider the number of recently rejected transactions from *P*, as provided by the `rejected_molecules` collection.

This set of Molecules shall be represented as ![Set of Rejected Molecules][mrej].

If *N*<sub>peer</sub> = countOverTime ( *M*<sub>rej</sub>, 60 seconds ) > 5, the `status` of *P* shall be set to "pending" and no further Molecules from *P* will be processed until the status is lifted automatically in 3600 seconds.

## Step 3: Duplicate check

Now that we are almost ready to process *M*<sub>new</sub> as a proposed Molecule, we must do one final check - making sure that *M*<sub>new</sub> isn’t already in our ledger (perhaps received from another peer).

This simply involves checking for the presence of *M*<sub>new</sub>’s `molecular_hash` field in the local ledger. If it is found, reply to *P* with a “duplicate” `status`, informing the peer that you already have this Molecule recorded.

---

# Concept: Lite Mode

Knish.IO nodes operating in “lite mode” forego the receipt and storage of other nodes’ Molecules in favor of querying peers to verify balance availability for other Wallets.

Lite nodes are able to generate only a limited subset of molecular isotopes (*V*, *B*, *M*), and do not perform tip selection or bonding algorithms on externally generated Molecules, as they do not receive peer broadcasts.

This mode is designed for mobile peer-to-peer exchange of data / Tokens as well as any applications that do not require storing the entire ledger.

Lite nodes store Wallet balances, but only for the purpose of display. Peers are always queried periodically and prior to any transaction to ensure that the balance of the owner’s Wallet(s) remains accurate.

When considering conflicting responses from multiple peers, the frequency of occurrence of each variation determines the probability of choosing that variation.

![Lite Mode Node Diagram][lite]

---

# Algorithm: Osmosis

Knish.IO nodes maintain a local copy of the ledger, but because each node deployment has its own unique disk space constraints, it is unrealistic to expect every node to store the entirety of the ledger. Therefore, a flexible pruning mechanism is introduced to keep the size of the ledger within desired limits.

When the size of the ledger reaches the maximum allowed amount, *M*<sub>origin</sub> begins *osmosing* the oldest Molecules. This process relies on the existing relational database of the node to maintain current model states, and creating snapshots of Wallet balances and metadata computed up to the moment of osmosis.

Only molecular and atomic data is destroyed in the process. All other models remain intact.

The process works as follows

1. Start at *M*<sub>origin</sub>.
2. Select *M*<sub>origin</sub>’s cascade as ![Set of Origin Cascades for Osmosis][osmosis]
3. Iterate over each *M*<sub>c</sub> in *C*<sub>origin</sub>
    - For *V*, *B* Molecules: create/update a Wallet snapshot reflecting the balance after this Molecule’s bonding
    - For *M* Molecules: create/update a Meta snapshot reflecting the object metadata after this Molecule’s bonding
    - For all other types: no snapshotting needed
4. Select the cascade of *M*<sub>c</sub> as *C*<sub>Mc</sub>
5. Move the bonds of each Molecule in *C*<sub>Mc</sub> from *M*<sub>c</sub> to *M*<sub>origin</sub>
6. Delete Mc
7. Continue until each Molecule in *C*<sub>origin</sub> has been deleted
8. Restart the process as many times as needed until the size of the ledger shrinks to the maximum desired file size 

At the bare minimum, each node is expected to retain the past 24 hours worth of molecular activity.

Individual deployments (such as KnishOS) may offer nodes additional options for purchasing / expanding their storage capacity via cloud disk integrations. 

---

# Concept: Rules, Policies, and Allowances

Knish.IO provides for several mechanisms for automating ledger behavior without human intervention:

## Rules

Rules are a set of logical constraints that is distributed throughout a ledger and performs defined actions (callbacks) based on either internal states or by retrieving data from external “oracles”. Unlike a computer program, which runs on a single PC or server, Rules operate in a distributed environment.

Rules are described using a structured instruction set format injected via the `metas` field of an *R* Atom, and applied to a specific `metaType` and `metaId` combination. Most Knish.IO models may be automated in such fashion.

Below is an example of a JavaScript SDK method to create an *R*-isotope Molecule that will trigger automated creation of a message when the temperature for a shipping container reaches an unsafe threshold:

```javascript
const metaType = 'ShippingContainer';
const metaId = 'foo123';
const rule = {
  condition: [ {
    key: 'temperature',
    value: 40,
    comparison: '>='
  } ],
  callback: [ {
    action: 'meta',
    metaType: 'Message',
    metaId: 'bar456',
    meta: {
      to: 'yuriy',
      subject: '%MetaId% has reached an unsafe temperature!',
      body: 'Please check %MetaType% %MetaId% - it\'s temperature' +
            'has just reached an unsafe level ( >= 40 degrees ).'
    }
  } ]
};
client.createRule( metaType, metaId, [ rule ] );
```

Molecules that result from server-side Rule execution are not broadcasted to other nodes - each of them will execute their own local version of the same, based on agreed-upon distributed Rule metadata.

KnishOS also provides a more specialized UX for managing Rules to fulfill the needs of Achievement-based gamification and incentivization.

![Edit Achievement Screenshot][achievement]

## Policies

Policies are a specialized set of properties contributed via *R*-isotopes that govern data access and privileges for specific meta assets. Policies are applied on a per-meta-key basis, allowing granular control over privileged data across the Knish.IO ledger.

There are four types of policies available:

1. **Read Policy:** determines which Wallet Bundles are able to retrieve metadata via `queryMeta` methods. Default behavior is for all Wallet Bundles to have unrestricted read access.


2. **Write Policy:** determines which Wallet Bundles are able to contribute new metadata via `createMeta` methods. Default behavior is for only the original meta asset creator to have write access.


3. **Destruct Policy:** determines how long a metadata field remains on the ledger before it "self-destructs" by causing its contents to be replaced by irreversible hashes.


4. **Logging Policy:** determines whether or not attempts to access this metadata field should be logged by the nodes, forming a full audit trail.

## Allowances

Allowances are Token quantities designated by their owner to allow for manipulation by the Knish.IO ledger without the owner's explicit signature on every resulting transaction. Allowances are expressed through the use of Buffers - a special subset of Wallets that users may shift Tokens into using *V-B-V*-Molecules.

Every time a new *V-B-V*-Molecule introduces new Token supply into the buffer, the ledger is able to automatically match the incoming buffer with a previously-created, unexpended buffer that meets the new offer's pricing requirements.

When that happens, a pair of local *B-V-B*-Molecules is created by every node that processes the incoming buffer, shifting the whole or partial balance of both the new buffer and the matched buffer into the participating users' Wallets, thereby satisfying at least one of the trades fully.

---

# Relational Design

This section describes the proposed relational database structure that nodes may maintain to keep track of the ledger state.

## Relational Design: Molecule

| Field Name                        | Field Type             | Description                                                                         |
|-----------------------------------|------------------------|-------------------------------------------------------------------------------------|
| `molecular_hash`                  | string(64)             | A hash of this Molecule’s Atoms, used to verify their integrity                     |
| `first_continu_id_molecular_hash` | string(64)             | Molecular hash of the first Molecule in the current Molecule's ContinuID chain      |
| `cell_id`                         | string(36), null       | Unique identifier for the dApp's cell (which dApp is responsible for this Molecule) |
| `peer_slug`                       | string(16)             | Unique identifier of the peer from which the Molecule was first received            |
| `counterparty`                    | string(64)             | A hashed combination of the user's identifier and the cell slug, used for branching |
| `bundle_hash`                     | string(64)             | Identifier for the Wallet Bundle responsible for this Molecule                      |
| `height`                          | unsigned int           | A measurement of how far this Molecule is from the start of its chain               |
| `confidence`                      | unsigned int           | An algorithmically determined confidence value that this transaction can be trusted |
| `status`                          | enum                   | One of: 'rejected', 'pending', 'accepted', 'broadcasted', 'received', or 'local'    |
| `created_at`                      | timestamp              | Creation timestamp                                                                  |
| `processed_at`                    | timestamp              | Processing / validation timestamp                                                   |
| `broadcasted_at`                  | timestamp              | Broadcast timestamp                                                                 |
| `confirmed_at`                    | timestamp              | Peer confirmation timestamp                                                         |
| `atoms`                           | relation(has-many)     | Collection of Atoms in this Molecule                                                |
| `bonds`                           | relation(many-to-many) | Collection of bonded Molecules                                                      |

## Relational Design: Bond

| Field Name       | Field Type | Description                                  |
|------------------|------------|----------------------------------------------|
| `molecular_hash` | string(64) | Unique identifier for the Molecule           |
| `bond_hash`      | string(64) | Unique identifier for the reference Molecule |
| `created_at`     | timestamp  | Creation timestamp                           |

## Relational Design: Atom

| Field Name       | Field Type          | Description                                                                 |
|------------------|---------------------|-----------------------------------------------------------------------------|
| `molecular_hash` | string(64)          | Unique identifier for the Molecule to which this Atom belongs               |
| `position`       | string(64), null    | Salt used to generate a private key for the originating Wallet.             |
| `wallet_address` | string(64), null    | Public key of the affected Wallet                                           |
| `isotope`        | string(1)           | Defines the behavior of this Atom. Can be set to any supported isotope name |
| `token_slug`     | string(16)          | Unique identifier of the Token used by the Wallet in this Atom              |
| `batch_id`       | string(64), null    | Unique identifier of the batch (or "stack") used to group stackable Tokens  |
| `value`          | double(65,18), null | Used to describe scalar amounts of value for transfer purposes              |
| `meta_type`      | string(36), null    | Polymorphic class name of schema receiving provided metadata                |
| `meta_id`        | string(256), null   | Polymorphic identifier of the class instance receiving provided metadata    |
| `metas_json`     | longtext, null      | A JSON structured store for metadata being conveyed by this Molecule        |
| `index`          | unsigned int        | Describers the order of the Atom inside its Molecule                        |
| `ots_fragment`   | string(2048), null  | Contains a fragment of the sender Wallet’s OTS                              |
| `created_at`     | timestamp, null     | Timestamp of creation                                                       | 
| `executed_at`    | timestamp, null     | Timestamp of execution by current node                                      | 

## Relational Design: Cell

| Field Name            | Field Type         | Description                                                      |
|-----------------------|--------------------|------------------------------------------------------------------|
| `cell_slug`           | string(36)         | Unique identifier (GUID or slug)                                 |
| `title`               | string(128)        | A friendly human-readable title for this cell                    |
| `query_count_24h`     | unsigned int       | Number of queries generated by this dApp in the past 24 hours    |
| `mutation_count_24h`  | unsigned int       | Number of mutations received from this dApp in the past 24 hours |
| `rejection_count_24h` | unsigned int       | Number of rejected Molecules from this dApp in the past 24 hours |
| `token_count`         | unsigned int       | Number of unique Token slugs minted by this dApp                 |
| `rule_count`          | unsigned int       | Number of active rules operating on behalf of this dApp          |
| `status`              | enum               | One of: 'stopped', 'paused', 'started', 'archived'               |
| `created_at`          | timestamp, null    | Timestamp of creation                                            |
| `updated_at`          | timestamp, null    | Timestamp of last activity                                       |
| `molecules`           | relation(has-many) | Collection of Molecules in this cell                             |
| `tokens`              | relation(has-many) | Collection of Tokens in this cell                                | 

## Relational Design: Token

| Field Name    | Field Type          | Description                                                           |
|---------------|---------------------|-----------------------------------------------------------------------|
| `token_slug`  | string(36)          | Unique identifier (GUID or slug) - typically used as a ticker symbol  |
| `title`       | string(64)          | A friendly human-readable title for this Token                        |
| `fungibility` | enum                | One of: 'fungible', 'nonfungible', 'stackable', 'mesh'                |
| `supply`      | enum                | One of: 'replenishable', 'limited'                                    |
| `bindability` | unsigned int        | Maximum length of a transfer chain for this Token                     |
| `amount`      | double(65,18), null | Maximum supply of the Token, if applicable                            |
| `decimals`    | unsigned int, null  | How many decimal places a fungible Token is subdivided, if applicable |
| `icon`        | string(1000), null  | Used to store binary image data for the icon / symbol of this Token   |
| `created_at`  | timestamp           | Timestamp of creation                                                 |
| `molecules`   | relation            | Collection of Molecules involving this Token                          |
| `wallets`     | relation(has-many)  | Collection of Wallets containing a balance in this Token              | 

## Relational Design: Wallet Bundle

| Field Name    | Field Type | Description                                    |
|---------------|------------|------------------------------------------------|
| `bundle_hash` | string(64) | Unique identifier for a Knish.IO user identity |
| `created_at`  | timestamp  | Creation timestamp                             |


## Relational Design: Peer

| Field Name              | Field Type             | Description                                                                         |
|-------------------------|------------------------|-------------------------------------------------------------------------------------|
| `host`                  | string(255)            | The unique hostname or IP address of the peer                                       |
| `peer_slug`             | string(36)             | Unique identifier (GUID or slug)                                                    |
| `peer_type`             | enum                   | One of: 'sender', or 'recipient'                                                    |
| `title`                 | string(64), null       | A friendly human-readable title for this peer                                       |
| `molecular_hash`        | string(64), null       | Unique identifier for P-isotope Molecule formalizing this peering relationship      |
| `access_token`          | longtext, null         | Authorization token used by the peer to send broadcasts                             |
| `access_token_hash`     | string(255), null      | Unique hash of the peer authorization token                                         |
| `cell_slugs`            | longtext, null         | A JSON structured store containing whitelist of cell slugs shared with this peer    |
| `status`                | enum                   | One of: 'guest', 'rejected', 'pending', 'accepted'                                  | 
| `sync_status`           | enum                   | One of: 'pending', 'processing', 'stopped', or 'finished'                           |
| `sync_algorithm`        | string(255)            | Determines the algorithm used for synchronizing Molecules                           |
| `receive_count_24h`     | unsigned int           | Number of received broadcasts from this peer over a 24 hour period                  |
| `send_count_24h`        | unsigned int           | Number of sent broadcasts to this peer over a 24 hour period                        |
| `rejection_count_24h`   | unsigned int           | Number of rejected broadcasts from this peer over a 24 hour period                  |
| `connection_count_24h`  | unsigned int           | Number of sync connections from this peer over a 24 hour period                     |
| `wait_count_24h`        | unsigned int           | Number of times the peer was throttled over a 24 hour period                        |
| `created_at`            | timestamp              | Timestamp of creation                                                               |
| `broadcasted_molecules` | relation(many-to-many) | Collection of Molecules that were successfully broadcast to this peer               |
| `received_molecules`    | relation(many-to-many) | Collection of Molecules that were successfully received from this peer              |
| `rejected_molecules`    | relation(many-to-many) | Collection of Molecules received from the peer that were rejected due to invalidity |

## Relational Design: Peer Molecules

| Field Name       | Field Type      | Description                                         |
|------------------|-----------------|-----------------------------------------------------|
| `peer_slug`      | string(36)      | Unique peer identifier (GUID or slug)               |
| `peer_type`      | enum            | One of: 'sender', or 'recipient'                    |
| `molecular_hash` | string(64)      | Unique identifier of the Molecule we are describing |
| `status`         | enum            | One of: 'rejected', 'pending', 'accepted'           | 
| `created_at`     | timestamp, null | Creation timestamp                                  |
| `confirmed_at`   | timestamp, null | Peer confirmation timestamp                         |

## Relational Design: Rules

| Field Name       | Field Type        | Description                                                         |
|------------------|-------------------|---------------------------------------------------------------------|
| `molecular_hash` | string(64)        | Unique identifier for the Molecule contributing the rule            |
| `position`       | string(64), null  | The position of the Wallet signing for the rule                     |
| `meta_type`      | string(36)        | Polymorphic class name for the meta asset we are tracking           |
| `meta_id`        | string(255), null | Polymorphic instance identifier for the affected meta asset         |
| `conditions`     | longtext          | JSON structured store for conditions that are applied to this rule  |
| `callbacks`      | longtext          | JSON structured store for callbacks that are triggered by this rule |
| `created_at`     | timestamp         | Creation timestamp                                                  |

## Relational Design: Authorization Tokens

| Field Name     | Field Type       | Description                                                                    |
|----------------|------------------|--------------------------------------------------------------------------------|
| `cell_slug`    | string(36)       | Unique identifier (GUID or slug) of the dApp asking for API privileges         |
| `bundle_hash`  | string(64), null | The unique Bundle identifier for the user requesting API privileges            |
| `peer_slug`    | string(36), null | Used for authorizing peer communication with a specific peer                   |
| `position`     | string(64), null | The position of the Wallet used to request authorization                       |
| `expiration`   | unsigned int     | How long the authorization lasts                                               |
| `status`       | enum             | One of: 'pending', 'active', 'disabled'                                        |
| `token`        | string(64)       | The actual authorization token string                                          |
| `type`         | enum             | What type of authorization we are giving. One of: 'bundle', 'guest', or 'peer' |
| `abilities`    | text             | JSON structured store for the abilities / rights granted by this authorization |
| `encrypt`      | unsigned int     | Whether or not end-to-end encryption is to be used                             |
| `position`     | string(64), null | The position of the Wallet used for end-to-end encryption                      |
| `pubkey`       | string(64), null | The public key of the Wallet used for end-to-end encryption                    |
| `created_at`   | timestamp, null  | Creation timestamp                                                             |
| `last_used_at` | timestamp, null  | Last use timestamp                                                             |
| `updated_at`   | timestamp, null  | Update timestamp                                                               |

# Sources Cited

1. CryptoKitties craze slows down transactions on Ethereum, BBC article https://www.bbc.com/news/technology-42237162
2. Directed Acyclic Graph, Wikipedia article https://en.wikipedia.org/wiki/Directed_acyclic_graph
3. SHA-3 Standard: Permutation-Based Hash and Extendable-Output Functions https://www.nist.gov/publications/sha-3-standard-permutation-based-hash-and-extendable-output-functions
4. Digital Signature Standard (DSS) https://csrc.nist.gov/publications/detail/fips/186/5/draft
5. Ethereum Sharding FAQ https://github.com/ethereum/wiki/wiki/Sharding-FAQs
6. XMSS – A Practical Forward Secure Signature Scheme based on Minimal Security Assumptions https://eprint.iacr.org/2011/484.pdf
7. Bitcoin Energy Consumption Index https://digiconomist.net/bitcoin-energy-consumption
8. Post-Quantum Cryptography https://en.wikipedia.org/wiki/Post-quantum_cryptography 
9. Recommendation for Stateful Hash-Based Signature Schemes https://csrc.nist.gov/publications/detail/sp/800-208/final
10. Quantifying Decentralization https://news.earn.com/quantifying-decentralization-e39db233c28e
11. U.S. Census Bureau Quick Facts https://www.census.gov/quickfacts/fact/table/US/HSD410220
12. 80% of tech could be built outside IT by 2024, thanks to low-code tools https://venturebeat.com/2021/06/14/80-of-tech-could-be-built-outside-it-by-2024-thanks-to-low-code-tools/

&copy; 2016-2022, WishKnish Corp. All rights reserved.

[dag]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/dag.png?raw=true "Directed Acyclic Graph"
[xmss]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/xmss_tree.png?raw=true "XMSS Tree"
[create]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/create-token.png?raw=true "Create Token Screenshot"
[organism]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/organism.png?raw=true "Knish.IO Organism Diagram"
[molecule]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/molecule.png?raw=true "Knish.IO Molecule Diagram"
[cascade]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/cascade.png?raw=true "Knish.IO Cascade Diagram"
[atoms]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/atoms.png?raw=true "Knish.IO V and I Atom Arrangement"
[cell]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/cell.png?raw=true "Knish.IO Cell Diagram"
[bundle]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/bundle.png?raw=true "Knish.IO Bundle Diagram"
[biometrics]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/biometrics.jpg?raw=true "Knish.IO Biometric UX"
[vatom]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/vatom.png?raw=true "Knish.IO V-Isotope Molecule Diagram"
[matom]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/matom.png?raw=true "Knish.IO M-Isotope Molecule Diagram"
[walletkey]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/walletkey.png?raw=true "Wallet Key Generation"
[address]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/address.png?raw=true "Wallet Address Generation"
[mcrw]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/equation-mcrw.png?raw=true "Markov Chain Random Walk Probability"
[rejection]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/equation-mcrw.png?raw=true "Rejection Probability"
[secondary]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/equation-secondary.png?raw=true "Secondary Bond Equation"
[peering]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/peering.png?raw=true "Knish.IO Peering Algorithm"
[mrec]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/equation-mrec.png?raw=true "Set of Received Molecules"
[mrejection]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/equation-peer-rejection.png?raw=true "Probability of Spontaneous Rejection"
[mrej]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/equation-mrej.png?raw=true "Set of Rejected Molecules"
[lite]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/litenode.png?raw=true "Lite Mode Node Diagram"
[osmosis]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/equation-osmosis.png?raw=true "Set of Origin Cascades for Osmosis"
[achievement]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/edit-achievement.jpg?raw=true "Edit Achievement Screenshot"
[architecture]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/architecture.png?raw=true "Knish.IO Architecture Diagram"
[nakamoto]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/nakamoto.png?raw=true "Nakamoto Coefficient Algorithm"
[infrastructure]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/infrastructure.png?raw=true "Knish.IO Peering Infrastructure"
[matching]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/matching.png?raw=true "Knish.IO Decentralized Exchange Buffer Trade Matching"
[identity]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/identity.png?raw=true "User Identity via Wallet Bundles"
[shadow]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/shadow.png?raw=true "Claiming a Shadow Wallet"
[logo]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/master/KnishIO-Logo.png "Knish.IO: Post-Blockchain Platform"
[continuid]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/continuid.png "Illustration of ContinuID Relay Race"
