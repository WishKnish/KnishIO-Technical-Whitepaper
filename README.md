<div style="text-align:center">
  <img src="https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/KnishIO-Logo.png" alt="Knish.IO: Post-Blockchain Platform" />
</div>
<div style="text-align:center">info@wishknish.com | https://wishknish.com</div>

# Technical Whitepaper v6.0

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

A key feature of XMSS is the reliance on one-time signatures via Winternitz One-Time Signatures Plus (WOTS+), which is leveraged by Knish.IO to ensure that all keys used to sign transactions are regenerated after every use, and that no key is ever used twice. This mechanism helps protect wallet holders from transactions spoofed by adversaries, and process only those signed by legitimate wallet holders.

Below is a diagram of the XMSS tree construction:

![XMSS Tree][xmss]

Furthermore, because encryption keys are similarly recycled, decrypting a thread of metadata or messages becomes increasingly difficult for a bad actor.

Additionally, many of the algorithms in use within the ledger are designed to be changed and upgraded over time as the need arises. After all, every cryptographic algorithm has a limited shelf life, so it is important to be adaptable to a changing cybersecurity landscape. The set of algorithms used (encryption, wallet character set, hashing algorithm, etc.) can be determined when negotiating an authorization key with a Knish.IO server.

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

Instead of forcing nodes to compete for who gets to validate a block of transactions by performing what is essentially “busy-work,” Knish.IO takes a very different approach - a "pay-it-forward" approach that is both asynchronous and Byzantine fault tolerant, while ensuring that more molecules receive validation than are created - meaning that it is prepared to handle a sudden surge of traffic gracefully, and without degradation of security.

---

## Critical Factor 4: User-Friendliness & Transparency

> “The main advantage of blockchain technology is supposed to be that it's more secure, but new technologies are generally hard for people to trust, and this paradox can't really be avoided.” - Vitalik Buterin

At the end of the day, if an amazing new technology is too abstract for the average consumer to use, it will not be adopted by the average consumer. That’s not to say it needs to be understood from top to bottom - after all, most automobile owners do not have a very deep understanding of the inner workings of a combustion engine or transmission, and yet can drive their cars just fine.

VentureBeat has postulated in mid-2021 that 80% of tech could be built outside IT by 2024, thanks to low-code tools [12] - a trend that is still largely being ignored by the blockchain community.

It is therefore our mission to bring mass adoption to the public by wrapping complex concepts into a user-friendly, easily-digestible experience - much like Microsoft Windows’ innovative Program Manager GUI did for desktop computing in the era of command-line MS DOS usage.

We see the following as critical sources of friction slowing or stopping consumer adoption:

1. **Storage of secret keys.** Forcing users to rely on software wallets, hardware wallets, paper wallets, cold storage, and other options for keeping a secret key is a lot to ask of consumers, especially when all they want to do is buy a cup of coffee with the tokens in their wallet. By leveraging biometric signatures and other modern passwordless mechanisms in lieu of a secret key, users can skip the overwhelming storage options, and rely purely on device sensors and (optionally) two-factor authentication to derive their signature each time they need to authorize an operation.

2. **Gas.** The concept of having to first purchase a supply of tokens before being able to transact on a ledger is inherently damaging to consumer uptake. Gas is used by Ethereum and many other distributed ledgers to subsidize verification by validators, but in the case of Knish.IO, validation is performed on random molecules by the entity bonding a new molecule into the ledger, essentially paying it forward, and removing the need for gas.

3. **Address naming convention.** A typical Ethereum address looks like this: 0xec824C1aF7304727eC92c71FfFEeDc0d6C38Eb0D. Imagine trying to tell a friend where to send a payment. Unless you do a lot of copying and pasting, or rely on a QR-code / NFC scanning solution, it will be very difficult indeed. Knish.IO introduces the concept of “slugs” - alphanumeric reference strings that are defined by the user, to give their Knish.IO bundle address a friendly, memorable name.

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

To this end, we introduce the concept of **cells**, **molecules**, and **atoms**.

- **Atoms** are sub-transactions that only perform a single, monodirectional action, such as removing X tokens from one wallet, adding Y tokens to another wallet, or contributing secure metadata to a virtual schema.
- **Molecules** are bundles of atoms which are either accepted or rejected all at once, and bond to (reference) a number of previous transactions to help facilitate Knish.IO’s federated consensus model.
- **Cells** are sharded sub-ledgers within the decentralized DAG environment, each serving one specific application, and defining rules for the behavior of every molecule within it.

- Taken together, the collection of cells, molecules, and atoms can be described as an **organism**.

By leveraging cells, molecules, and atoms, Knish.IO is capable of a network-bound scalability and transaction settlement within 5 seconds, regardless of the transactional volume. In fact, as the network grows, we fully expect this interval to shrink further.

![Knish.IO Organism Diagram][organism]

---

# Model: Molecule

Transactions issued on Knish.IO are composed of a number of micro-transactions (atoms). In order to make sense of where the information is coming from and where it’s going, atoms are packaged into a bundle called a “molecule”.

When new molecules are being recorded to the ledger, the atoms that compose them are either accepted or rejected all at once, never separately.

![Knish.IO Molecule Diagram][molecule]

Molecules form **bonds** with other molecules to help secure the ledger in an asynchronous fashion. Each molecule MUST bond with other molecules before it can be accepted into the ledger. This is performed using the **tip selection algorithm** and **molecular bonding algorithm** described further herein.

The higher the percentage of valid molecular bonds (direct or indirect) after performing the tip selection algorithm a specific number of times, the more confidence the ledger has regarding a molecule’s validity.

Because nodes bond incoming molecules in an asynchronous fashion, consensus is achieved by observing *intersections* between multiple nodes’ states, thus maintaining byzantine fault tolerance even in the case of conflicts between two sets of nodes.

## Concept: Molecular Cascades

The set of all molecules that have established bonds to a particular molecule *M* directly is referred to as a **cascade**. 

The maximum number of cascades from *M*<sub>i</sub> up to a tip molecule represents its “depth”, *d*<sub>i</sub>. 

The minimum number of cascades down from *M*<sub>i</sub> to *M*<sub>origin</sub> represents its “height”, *h*<sub>i</sub>.

For *V* molecules, a “local height” may also be determined by counting the minimum number of cascades down from *M*<sub>i</sub> to the token creation molecule, *M*<sub>creation</sub>.

![Knish.IO Cascade Diagram][cascade]

Cascades are used to verify the integrity of the ledger and reference neighboring molecules that are referenced by or are referencing the given molecule.

---

# Model: Atom

A molecule contains at least one atom. Each atom comes in one of several single-purpose isotopes, allowing the atom to be tuned to a particular use case. These isotopes describe the “vocabulary” of the Knish.IO protocol.

Supported atomic isotopes, as of the writing of this document, are:

- **Value** (*V*) - moves fungible scalar value, non-fungible unit objects, or partially fungible batches of scalar value from one wallet to another. V-atoms always come in triples: the first atom removes tokens from the source wallet; the second adds tokens to the destination wallet; and the third places the remaining tokens into a new wallet that will replace the first.
- **Buffer** (*B*) - identical functionality to *V*, but operating on *allowance buffers* rather than *wallets*, typically used for peer-to-peer decentralized exchange and token staking scenarios.
- **Metadata** (*M*) - assigns structured metadata (key:value pairs) to some arbitrary Meta Asset instance referenced by a class and unique identifier.
- **Creation** (*C*) - declares the creation of a new virtual asset, which can take the form of a Token, a Wallet, or a Meta Asset class.
- **Rules** (*R*) - used to describe granular policies (read, write, self-destruct, and logging) associated with some Meta Asset, as well as automation workflows and callbacks.
- **Peering** (*P*) - used for initiating peer invite, coordinating handshakes between peers for the purpose of coordinating ledger states across diverse machines.
- **Identity Continuity** (*I*) - (also called “ContinuID”) used for establishing a chain of personal custody between multiple molecules. Each transaction signed with the USER wallet requires that one I isotope is always present.
- **User Access** (*U*) - used for requesting and managing personal access tokens for accessing privileged ledger activities and data.
- **Token Request** (*T*) - used to request a specific type of Token from a federated node. If requirements are fulfilled, the node will sign and issue a V-isotope molecule completing the transfer.
- **Append Request** (*A*) - used to request modifications of metadata from a federated node. If requirements are fulfilled, the node will sign and issue a M-isotope molecule updating the requested metadata.

The first atom in a molecule is considered the “signing atom” and is critical in the signing and validation process. For any molecules that involve the movement of tokens, the first atom must be signed with the wallet (or buffer) from which tokens are being withdrawn; For all other types of modules, the first atom must be signed with the system-reserved USER token wallet.

*V*-isotope molecules are always signed with wallet-bearing token in the first *V*-isotope atom:

![Knish.IO V-Isotope Molecule Diagram][vatom]

*M*-isotope molecule are always signed with USER-token wallet designated in prior *I*-isotope:

![Knish.IO M-Isotope Molecule Diagram][matom]

*I*-isotope atoms and the third *V*-isotope atoms serve an identical purpose: to establish the next wallet in the user’s custody. However, in the case of *V*-isotope atoms, token remainder balance is also shifted to the new wallet.

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

A Wallet Bundle represents a Knish.IO user identity. It is the collection of all the user's wallets, shadow wallets, buffers, molecules, reputation, and metadata. True to its name, it is very much a "bundle of wallets".

When sending tokens to a user, their wallet bundle may be used in lieu of a recipient wallet address.

Wallet bundles are identified by a unique 64-character identifier called a `bundleHash`, which is used interchangeably with a wallet address for sending tokens to a third party.

Every virtual object created on the ledger, including tokens, meta assets, and even molecules and their atoms, is tied to the wallet bundle that created it, ensuring that reputation and continuity of identity is maintained throughout the objects' lifecycles.

Individuals may maintain more than one wallet bundle, to ensure that aspects of their digital life do not undesirably bleed over from one domain into another.

![User Identity via Wallet Bundles][identity]

## Wallet

Wallets are virtual buckets for storing assets (tokens) and WOTS+ keys for signing molecules or encryption keys for encrypting data, and may be employed in the more traditional sense (users sending and receiving cryptocurrency payments or NFTs), or in more exotic use-case-specific ways (for example, facilitating peer-to-peer hyper-secure communications via constantly-changing encryption keys).

While a WOTS+ private key can be used to sign any molecule, repeat usages of a key will be rejected by the ledger because each use exposes exactly 50% of the key, allowing an attacker to compromise signed assets should key re-use be allowed. Because of this single-use nature of the private keys, it becomes necessary to regenerate a wallet with a new private key after every transaction.

When a wallet is regenerated, it can no longer sign molecules using the same WOTS+ key. This is an effective countermeasure against a possible compromised wallet (which is effectively unusable if it has regenerated), as well as against a possible attempt to perform a double-spend transaction (due to the asynchronous nature of the consensus algorithm combined with additional bonding requirements for multiple low-confidence molecules drawing from the same wallet bundle).

![Knish.IO Bundle Diagram][bundle]

## Shadow Wallet

The process of wallet regeneration produces a new wallet, and eventually there may be dozens, if not hundreds of wallets kept by any single user. This is why wallet bundles are used as an abstraction layer and route tokens to the latest, pristine wallet address.

However, if no such pristine wallet is available to route tokens into, a shadow wallet is created instead. Shadow wallets are temporary wallets with no keys (therefore no `position` or `wallet_address` fields defined), only a wallet bundle assignment.

Shadow wallets can be used for deposit routing, however no transactions may be signed by them, and therefore any received tokens may not be used until the shadow wallet is "claimed". The process of claiming a shadow wallet is equivalent to retroactively creating a wallet for the given token, which will automatically receive any collected balance from the shadow wallet.

![Claiming a Shadow Wallet][shadow]

## Buffer

Buffers are specialized wallets used for coordinating automation allowances: fungible, non-fungible, or partially-fungible assets may be buffered for automated peer-to-peer exchange and staking use-cases, or shifted out of previously allocated buffers back into their "normal" wallets.

Unlike wallets, buffers cannot transfer tokens to third-parties, other than via server-side automation, so while they can be used to sign transactions, they are limited to those that move tokens out of a buffer and into the same user's wallet.

On the other hand, buffered assets can take advantage of rich server-side automation capabilities: for example, Knish.IO comes with a robust trade matching engine connecting buffered trades and fulfilling token swaps.

![Knish.IO Decentralized Exchange Buffer Trade Matching][matching]

---

# Model: Token

Tokens are virtual representations of a particular asset or utility, and may represent fungible, non-fungible, and partially-fungible assets. Tokens may be traded, sold, or utilized as part of a digital ecosystem or application.

Tokens are stored in users’ wallets. Each wallet address can accommodate only a single type of token, so a user holding multiple tokens would have a wallet address for each of them, each with its own position for signing molecules.

There are presently three fungibility modes supported:

1. **Fungible** tokens rely on the `balance` field of a wallet to track how much balance remains. This is the "default" behavior.
2. **Non-fungible tokens** rely on `token_units` to describe unique nonfungible units of the token using structured metadata.
3. **Partially-fungible ("stackable") tokens** use a combination of `balance`, `batch_id`, and metadata attached to the wallet and/or token to fulfill their use case.

There are also two replenishment modes supported:

1. **Replenishable** tokens can be re-issued as needed after creation, and there is no limit on the maximum supply amount.
2. **Non-Replenishable** tokens cannot be re-issued, so the initial supply minted will represent the final maximum supply amount.

---

# Algorithm: Wallet Key Generation

Given the biometric secret *S*, an integer `position`, and a string `token` argument, this algorithm derives a 4096 byte (2048 character) hexadecimal private key and 128 byte (64 character) hexadecimal wallet address.

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

Once we have obtained the wallet private key *K*<sub>k</sub>, we can use it to derive a wallet address for this key.

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
7. Squeeze a 128 byte (64 character) string out of the sponge that will represent the wallet address for this private key.

![Wallet Address Generation][address]

---

# Model: Meta Asset

Knish.IO provides for dynamic, virtual data structures called Meta Assets. Specific Meta Assets are identified via a combination of `metaType` and `metaId` properties, and can have an arbitrary amount of structured metas storing key/value pairs of properties, as contributed by *M*-molecules.

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

## Custom Schemas

Knish.IO generally supports arbitrarily-structured metadata (no limitations on which metadata `key` values are used), but sometimes it may be advantageous to define a fixed schema to which data must conform (a specific list of `key` values and their respective structure).

There are 2 ways of accomplishing this:

1. **Define your own schema:** Custom schema structure may be provided during meta asset creation when setting `metaType` to "MetaType" and `metaId` to the name of the new meta asset class. The `meta` object will supply the schema structure. Subsequent creation of meta assets of the new meta asset class will have to adhere to the defined schema.
2. **Reference an external schema:** Knish.IO can be extended to support external schemas from [Schema.org](https://schema.org/), [GS1](https://gs1.org), [NIEM](https://www.niem.gov/), and others.

---

# Algorithm: Molecule Construction

When a client initiates a new transaction, it must construct and correctly sign a molecule to represent that transaction and all of its relevant data, before sending it to a receiving node which will then cryptographically verify such data to ensure its validity, and (in certain cases) ensure that third-party observers are not able to violate the privacy of the participants.

This procedure involves the generation of a private key for the next available atomic position, the hashing of atomic data to generate a molecular hash, the creation of a WOTS+ signature for the molecule, and finally, the creation of a new quantum-resistant wallet to receive any leftover tokens remaining, or to serve as the user's next molecule's signatory.

1. Client obtains biometric secret
2. Client generates atomic structure to fulfill transaction and shift remaining balance
3. Client creates a molecular hash of the atoms
4. Client creates OTS fragments for each atom
5. Client broadcasts new molecule to the node
6. Node verifies the molecule's signature and hash
7. Node performs random walk to select bonds
8. Node verifies the primary bonds' signatures and hashes
9. Node verifies the atomic payloads of the new molecule and its bonds
10. Node broadcasts bonded molecule to peers

## Step 1: Client obtains biometric secret

Each molecule must be approved by the sender, and to that end an external biometric solution may be utilized to transform the sender’s face, fingerprints, and/or voice print (or a combination of any of the above) into a unique keypair.

Alternatively, other forms of authentication may be used, including OAuth, NFC, smart cards, and other types of credentials.

The actual method of biometric collection depends on use case implementation, but the result is always the same: a 2048-symbol hexadecimal string.

This biometric secret, *S*, may then be used as a seed to generate an infinite number of one-time-use private keys for the new quantum-resistant Knish.IO wallet. The public key becomes the wallet address.
Each private key may only be used securely once, and neither  nor the wallet private key needs to necessarily be stored in order to function correctly.

![Knish.IO Biometric UX][biometrics]

## Step 2: Client generates atomic structure

In this step we must generate all the necessary atoms for molecule *M* to fulfill the requirements of the transaction.

1. Build the primary atom (lowest index in the molecule). This normally represents a destructive transaction from the sender’s wallet.
2. Build the secondary atom (next index). This normally represents a constructive transaction to the recipient’s wallet.
3. Build any additional atoms necessary to fulfill the requirements of the transaction (for example, utilizing the sender’s wallet to fund multiple recipients with one transaction, or delivering message metadata to the recipient).
4. The last *V* isotope atom would reference a newly-created remainder wallet, which may receive any excess tokens not spent in the first atom.

You will end up with a series of atoms like this (*V* isotopes shown in example), capped off with an *I* isotope to establish chain of custody:

![Knish.IO V and I Atom Arrangement][atoms]

## Step 3: Client creates a molecular hash of the atoms

Now that the atoms are ready, the Knish.IO SDK will hash them together to produce a molecular hash. This is later used to ensure that each atom in fact belongs to the molecule and no data or instructions have been added, removed, or otherwise tampered with along the way.

1. Arrange each atom *A*<sub>1</sub>, ..., *A*<sub>i</sub> in *M* by order of their position. Denote position as *k*
2. Create a SHAKE256 sponge instance for *M*
3. Iterate across each atom as *A*<sub>k</sub>
4. Absorb each of *A*<sub>k</sub>’s fields into the sponge in this specific order: `position`, total number of atoms, `wallet_address`, `isotope`, `token` (if present), `value` (if present), and `created_at`
5. Squeeze *M*’s sponge to produce a 128 byte (64 character) hexadecimal string
6. Convert the string into Base 17 (numbers 0-9 and letters ‘a’ through ‘g’), which is denoted by molecular hash *H*<sub>m</sub>
7. Assign *H*<sub>m</sub> to *M*’s `molecular_hash` field
8. Iterate across each atom as *A*<sub>k</sub>
9. Assign *H*<sub>m</sub> to *A*<sub>k</sub>’s `molecular_hash` field

## Step 4: Client creates OTS fragments for each atom

In order to verify that this molecule was in fact issued by the owner of the originating wallet, we need to prepare a correct `ots_fragment` field.

The **Wallet Key Generation Algorithm** helps us derive the private key *K*<sub>k</sub> given the first atom's `token` and `position`. We will need it here.

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
9. Divide *O* into a number of string chunks equal to the number of atoms in the molecule, arranged in order of `position`
10. Write the ots chunk into each atom's respective `ots_fragment` field

## Step 5: Client broadcasts new molecule to the node

Knish.IO nodes rely on a GraphQL-based API to work with client appliations, so a GraphQL mutation would typically need to be sent to the node with the signed molecule, as per the following mutation structure:
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

Knish.IO SDKs perform a number of validations on molecules prior to broadcast, however, if you are foregoing an SDK, and building an implementation from scratch, it may be advantageous to verify the `ots_fragment` and `molecular_hash` prior to sending a mutation, using the same verification algorithms as the node, below.

## Step 6: Node verifies the molecule's hash and signature

A node will receive a GraphQL MoleculeInput object containing the molecule itself, its atoms, and any relevant meta that may be conveyed by the transaction.

To verify the validity of the molecule, the node needs to transform the collection of `ots_fragment`s and the `molecular_hash` into a string that will perfectly match the `wallet_address` on the primary atom.

1. Run the *Molecular Hash Algorithm* (step 3 above) and compare the result with the `molecular_hash` field on the atoms. If it matches, the atomic payload is intact.
2. Arrange all atoms in order of ascending `position`, and concatenate their `ots_fragment` fields into a single string, *O*
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
13. The string will match the primary atom's `wallet_address` if all is well

## Step 7: Node performs random walk to select bonds

Once a molecule's payload and signature have been verified, the node must choose a number of prior molecules in the local ledger to bond this molecule with, while performing additional checks on the bond targets.

The process of bonding molecules in Knish.IO behaves differently depending on the primary atomic isotope involved in the proposed molecule:

- *V* and *B* molecules may ONLY bond with molecules associated with the same token
- *C* molecules may ONLY bond with other *C* molecules, or a root molecule
- *M* molecules may ONLY bond with *M* or *C* molecules describing the same `metaType` and `metaId`, or a root molecule
- *P* molecules may ONLY bond with the *P* molecule representing the peer to which we are bonding, or a root molecule
- *R* molecules may ONLY bond with *R*, *M*, or *C* molecules describing the same `metaType` and `metaId`, or a root molecule
- The first molecule on the ledger does not need to bond, as there is nothing to bond with, and is considered the global origin

A proposed molecule *M* must bond with a variable number of tip molecules in order to be accepted by Knish.IO, depending on several factors described herein.

The first two tips - {*M*<sub>1</sub>, *M*<sub>2</sub>} - are referred to as the “primary bond candidates”. All subsequent tips - {*M*<sub>3</sub>, ... , *M*<sub>t</sub>}- are referred to as “secondary bond candidates”. There may be no repeats across either set.

Each member of the set {*M*, *M*<sub>1</sub>, *M*<sub>2</sub>} MUST originate from a unique wallet bundle (no repeat owners).

Conversely, each member of {*M*<sub>3</sub>, ..., *M*<sub>t</sub>} MUST originate from the same wallet bundle(s) referenced in {M1, M2}, and are treated as an extension of the primary set when validating correctness. This helps ensure that when multiple tips are being issued in rapid succession by the same identity, *M* is able to validate them as single unit and secure the cell against possible double-spend attacks.

A **Markov Chain Random Walk** (Weighted Monte Carlo Random Walk) procedure must be repeated until the two primary bond candidates are selected:

1. Select the chronologically nearest root molecule *M*<sub>root</sub>. This is a highly trustworthy molecule which meets ALL of the following criteria:
    - *M*<sub>root</sub> is NOT originating from the same wallet bundle as *M* any previously selected primary bonds
    - *M*<sub>root</sub> does NOT have a `status` of "rejected"
    - Isotope-specific bonding requirements (above) are maintained
    - *M*<sub>root</sub> has a `confidence` of 95% or higher
    - If no acceptable *M*<sub>root</sub> is found above, choose *M*<sub>origin</sub> as *M*<sub>root</sub>
2. Choose a molecule *M*<sub>c</sub> out of *M*<sub>root</sub>'s cascade to "walk" to.
    - If a total of *p* > 1 molecules are present in the cascade, then the probability of selecting a *M*<sub>c</sub>, with a `confidence` of *I*<sub>c</sub>, is equal to: ![Markov Chain Random Walk Probability][mcrw]
    - This produces a range of probabilities depending on the relative `confidence` of *M*<sub>c</sub> compared with other molecules in the cascade, and ensures that even less-prominent molecules have a chance of being selected for analysis.
    - If *M*<sub>c</sub> has the same wallet bundle as *M* or any primary bond candidates thus far, it is ignored (can't walk over your own molecules).
    - If *p* == 1, walk to the sole available *M*<sub>c</sub>.
3. Repeat step 2 with *M*<sub>root</sub> = *M*<sub>c</sub> until *p* == 0 or no further valid walks are possible due to the above constraints.
4. Perform a throttle check on the selected *M*<sub>c</sub> to ensure that the same wallet bundle isn't generating too many new molecules:
    - Probability of spontaneous rejection can be represented by comparing *N*<sub>c</sub> = countOverTime ( *M*<sub>c</sub>, 5 seconds ) to an upper limit of 100 molecules per 5 seconds:
    
    ![Rejection Probability][rejection]

    - Should rejection occur at this stage, the random walk process must be restarted to choose a different tip.
    - Function countOverTime ( *M*, *t* ) returns the number of molecules submitted by wallet bundle of molecule *M* within the specified number of seconds *t* of *M*.
5. Choose this final *M*<sub>c</sub> as the selected tip for analysis.

At this point, the set of primary bond candidates will have either {*M*<sub>1</sub>} or {*M*<sub>1</sub>, *M*<sub>2</sub>}. 

We must now check if secondary bond candidates are required to help protect the cell from possible double-spend attacks. The number of secondary bond candidates required is defined by the pseudocode below:

![Secondary Bond Equation][secondary]

The *GetTips* function above returns a collection of all tip molecules originating from the same wallet bundle as the supplied set of molecules, exclusive of the arguments themselves.

The full set of bond candidates, {*M*<sub>1</sub>, *M*<sub>2</sub>, ..., *M*<sub>t</sub>}, needs to be checked for validity and finalized.

## Step 8: Node verifies the primary bonds' hashes and signatures

For each of the primary bond candidates {*M*<sub>1</sub>, *M*<sub>2</sub>} that have a `status` of "received" - molecules that were verified by other nodes and sent to the current Knish.IO node as a peer - we need to make sure they were properly signed, and double-check the peer's work.

Simply repeat Step 6 for each of the bond candidates. If the verification algorithm in Step 6 returns false, reject the bond candidate and re-run the bond selection algorithm.

## Step 9: Node verifies the molecules' atomic payloads

The molecule *M* and all of its bonds {*M*<sub>1</sub>, ..., *M*<sub>t</sub>} needs to be verified for integrity according to its type, using the verifying node’s currently available local data as reference. The verification process may group multiple unverified molecules together to ensure that possible double-spend attacks are much harder to execute:

**For *V* and *B* molecules:**

1. Collect all primary atoms in {*M*, *M*<sub>1</sub>, ..., *M*<sub>t</sub>} featuring the same token *T* and wallet bundle *B*, and combine their aggregate value as *V*<sub>total</sub>. 
2. Check to ensure that GetWalletTokenBalance( *B*, *T* ) >= *V*<sub>total</sub>, meaning there is enough tokens to cover not just *M*, but any secondary bond candidate as well. If there is not, reject *M*.

**For *M* molecules:**

1. Check to ensure that recipient object *O* (`meta_type` and `meta_id` fields supply the polymorphic reference) has no privilege restrictions for *B* to manipulate its metadata. If a restriction is found, reject *M*.
2. In case *M* is a revocation request, check to ensure that the revoked metadata actually exists to be revoked. If not, reject *M*.

**For *C* molecules:**

1. Check to ensure that *B* has no privilege restrictions to create the type of asset requested. If a restriction is found, reject *M*.

**For *P* molecules:**

Atomic payload check not needed.

**For *R* molecules:**

1. The `meta_type` and `meta_id` fields supply the polymorphic reference to the target being reported. Check to make sure this asset has not been previously reported by *B*. If it has been, reject *M*.

## Step 10: Node broadcasts the verified molecule to its peers

After successfully completing the previous steps, the node can safely add bonds between *M* and primary bond candidates {*M*<sub>1</sub>, *M*<sub>2</sub>} (no actual bonds are formed to secondary candidates) and broadcast *M* and its bonds to peer nodes. 

Normally all molecules are broadcast to all peers, with the exception of those intended for P2P messaging - in which case, they will only get broadcast to the specific peer which matches the wallet bundle the message is addressed to.

See **Peering Algorithm**

## Rejection ##

Any molecule *M* upon which the local integrity check is aborted for any reason must be properly marked as such with a ‘rejected’ `status`, and the process must recurse through any molecule(s) that are bonded to *M* to invalidate any sub-DAGs forming beyond this molecule.  On abort, the set of secondary bond candidates is cleared, and the tip selection algorithm begins anew to choose a replacement candidate molecule.

---

# Algorithm: Peering

Knish.IO uses a hybrid peering algorithm that combines the use of *P* molecules to announce node presence, and local peer reputation tables for a transparent, secure, and efficient process for discovering, adding, and maintaining lists of peer nodes without exposing the topology of the distributed mesh network formed by them.

Because issuance of a *P* molecule is required to initiate peering, it becomes exponentially more difficult to mount a successful Sybil attack, especially when biometric authentication is involved - each node is tied to a specific biometric secret that is difficult to forge and maintains a global reputation.

Each node may have up to 100 peers, though starting at 50, each broadcast by the node will cause the slowest / least reliable peers to be dropped without replacement.

![Knish.IO Peering Algorithm][peering]

## Discovering Peers

The first peer a node connects to must be ‘bootstrapped’ - manually or automatically added in the course of an interaction.

For added trust, visiting any **WishKnish Storefront** or other *‘Powered by Knish.IO’* deployment in a web browser allows any user to validate the authenticity of the node by clicking the Knish.IO logo. The resulting page will provide reputational information about this node, as well as instructions for manually bootstrapping it, if so desired.

Should the user choose to interact with this node by partaking in a transaction, they will become the user’s node’s first peer automatically, without any action needed by the user.

Bootstrapping causes a new node *N* to issue a *P* molecule to the prospective peer node, *N*<sub>peer</sub>. *N*<sub>peer</sub> receives *P*, verifies it (as per the verification algorithms described previously), and broadcasts to their existing peers {*N*<sub>a</sub>, ..., *N*<sub>z</sub>}. The peers, upon receiving *P*, verify it as well - however, they do NOT re-broadcast it any further - the topology of the local mesh surrounding this particular set of nodes is only known to them.

The new node, *N*, is now present in *N*<sub>peer</sub>’s list of peers with an “accepted” status and will receive any new molecules successfully bonded by *N*<sub>peer</sub>.

Thereafter, nodes can be added either automatically (broadcast from *N*<sub>peer</sub> and other peers of *N*) or continue to be manually added by *N*, depending on need.

Full nodes will not broadcast to nodes operating in *Lite Mode* (more on this below), so the bootstrap process works differently: if a new Lite Mode node is bootstrapping another Lite Mode node, the new node will receive a random peer from the second node’s peers table. If the new Lite Mode node is instead bootstrapping a full node, that full node is added to the new node’s peers table.

The Lite Mode node’s peers table is used to send out active requests for consensus, rather than passively receiving new molecules. 

## Broadcasting to Peers

When a molecule *M* has been successfully bonded with no issues, it is ready to be broadcasted to other peers.

The broadcast process is repeated for each active peer present the local node’s peers table. Each peer receives a GraphQL API message to its node address, and proceeds to the broadcast receipt procedure below.

The response returned is checked for status (whether the peer has accepted *M* or not), and measured for latency.

*P* molecules that are received from a peer are NOT re-broadcast to other peers even if they are valid to avoid exposing global mesh topology to potential attackers.

## Automatic Peer Cleanup

Depending on the number of peers a node has, there is a random chance that each new broadcast will cause the slowest / least reliable peer to be removed or replaced.

The specific rules are as follows, with the number of peers denoted as *p*:

1. For *p* < 25: 10% chance that a random peer address will be selected from all locally known *P* molecules, and contacted for a handshake; If the response speed is faster than the slowest available peer, the new peer will take its place in the peers table.
2. For 25 <= *p* < 50: 25% chance that a random peer address will be selected from all locally known *P* molecules, and contacted for a handshake; If the response speed is faster than the slowest available peer, the new peer will take its place in the peers table.
3. For 50 <= *p* < 100: 5% chance that the slowest peer in the table will be dropped without replacement.
4. For *p* >= 100: peering requests will be rejected and no new peers may be added at this point.

In general, if a peer fails to respond within a reasonable time, its `retries` field is incremented after each consecutive failure, and after 5 failed broadcasts, the peer is marked as rejected.

---

# Receiving Broadcasts

When a peer broadcasts a new molecule, Knish.IO ensures that the peer is not attempting to pollute the ledger with dummy molecules or form a parasite chain by completing the following steps prior to accepting the new molecule and attempting to bond it into the ledger:

## Step 1: Throttle check

The purpose of this procedure is to ensure that peer *P* sending molecule *M*<sub>rec</sub> isn’t spamming us by looking at the number of recently received molecules from *P*, as provided by the `received_molecules` collection.

This set of molecules shall be represented as ![Set of Received Molecules][mrec].

Probability of spontaneous rejection of the broadcast shall be represented by comparing *N*<sub>peer</sub> = countOverTime ( *M*<sub>rec</sub>, 5 seconds ) to an upper limit of 30 molecules per 5 seconds: ![Probability of Spontaneous Rejection][mrejection]

Should rejection occur, *M*<sub>new</sub> will be added to the `rejected_molecules` collection.

## Step 2: Peer integrity check

This step is designed to prevent repeated attempts at submitting spam molecules by peer *P*, and need only be attempted if Step 1 fails.

We will consider the number of recently rejected transactions from *P*, as provided by the `rejected_molecules` collection.

This set of molecules shall be represented as ![Set of Rejected Molecules][mrej].

If *N*<sub>peer</sub> = countOverTime ( *M*<sub>rej</sub>, 60 seconds ) > 5, the `status` of *P* shall be set to "pending" and no further molecules from *P* will be processed until the status is lifted automatically in 3600 seconds.

## Step 3: Duplicate check

Now that we are almost ready to process *M*<sub>new</sub> as a proposed molecule, we must do one final check - making sure that *M*<sub>new</sub> isn’t already in our ledger (perhaps received from another peer).

This simply involves checking for the presence of *M*<sub>new</sub>’s `molecular_hash` field in the local ledger. If it is found, reply to *P* with a “duplicate” `status`, informing the peer that you already have this molecule recorded.

---

# Concept: Lite Mode

Knish.IO nodes operating in “lite mode” forego the receipt and storage of other nodes’ molecules in favor of querying peers to verify balance availability for other wallets.

Lite nodes are able to generate only a limited subset of molecular isotopes (*V*, *B*, *M*), and do not perform tip selection or bonding algorithms on externally generated molecules, as they do not receive peer broadcasts.

This mode is designed for mobile peer-to-peer exchange of data / token as well as any applications that do not require storing the entire ledger.

Lite nodes store wallet balances, but only for the purpose of display. Peers are always queried periodically and prior to any transaction to ensure that the balance of the owner’s wallet(s) remains accurate.

When considering conflicting responses from multiple peers, the frequency of occurrence of each variation determines the probability of choosing that variation.

![Lite Mode Node Diagram][lite]

---

# Algorithm: Osmosis

Knish.IO nodes maintain a local copy of the ledger, but because each node deployment has its own unique disk space constraints, it is unrealistic to expect every node to store the entirety of the ledger. Therefore, a flexible pruning mechanism is introduced to keep the size of the ledger within desired limits.

When the size of the ledger reaches the maximum allowed amount, *M*<sub>origin</sub> begins *osmosing* the oldest molecules. This process relies on the existing relational database of the node to maintain current model states, and creating snapshots of wallet balances and metadata computed up to the moment of osmosis.

Only molecular and atomic data is destroyed in the process. All other models remain intact.

The process works as follows

1. Start at *M*<sub>origin</sub>.
2. Select *M*<sub>origin</sub>’s cascade as ![Set of Origin Cascades for Osmosis][osmosis]
3. Iterate over each *M*<sub>c</sub> in *C*<sub>origin</sub>
    - For *V*, *B* molecules: create/update a Wallet snapshot reflecting the balance after this molecule’s bonding
    - For *M* molecules: create/update a Meta snapshot reflecting the object metadata after this molecule’s bonding
    - For all other types: no snapshotting needed
4. Select the cascade of *M*<sub>c</sub> as *C*<sub>Mc</sub>
5. Move the bonds of each molecule in *C*<sub>Mc</sub> from *M*<sub>c</sub> to *M*<sub>origin</sub>
6. Delete Mc
7. Continue until each molecule in *C*<sub>origin</sub> has been deleted
8. Restart the process as many times as needed until the size of the ledger shrinks to the maximum desired file size 

At the bare minimum, each node is expected to retain the past 24 hours worth of molecular activity.

Individual deployments (such as KnishOS) may offer nodes additional options for purchasing / expanding their storage capacity via cloud disk integrations. 

---

# Concept: Rules, Policies, and Allowances

Knish.IO provides for several mechanisms for automating ledger behavior without human intervention:

## Rules

Rules are a set of logical constraints that is distributed throughout a ledger and performs defined actions (callbacks) based on either internal states or by retrieving data from external “oracles”. Unlike a computer program, which runs on a single PC or server, Rules operate in a distributed environment.

Rules are described using a structured instruction set format injected via the `metas` field of an *R* atom, and applied to a specific `metaType` and `metaId` combination. Most Knish.IO models may be automated in such fashion.

Below is an example of a JavaScript SDK method to create an *R*-isotope molecule that will trigger automated creation of a message when the temperature for a shipping container reaches an unsafe threshold:

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
client.crateRule( metaType, metaId, [ rule ] );
```

Molecules that result from server-side Rule execution are not broadcasted to other nodes - each of them will execute their own local version of the same, based on agreed-upon distributed Rule metadata.

KnishOS also provides a more specialized UX for managing Rules to fulfill the needs of Achievement-based gamification and incentivization.

![Edit Achievement Screenshot][achievement]

## Policies

Policies are a specialized set of properties contributed via *R* isotopes that govern data access and privileges 

---

# Relational Design

This section describes the proposed relational database structure that nodes may maintain to keep track of the ledger state.

## Relational Design: Molecule

| Field Name | Field Type | Description |
|------------|------------|-------------|
| `molecular_hash` | string(64) | A hash of this molecule’s atoms, used to verify their integrity |
| `cell_id` | string(36), null | Unique identifier for molecule’s cell; Matches the cell of the token referenced by the primary atom |
| `bundle` | string(64) | Identifier for the bundle grouping the wallets together |
| `status` | enum | Indicator of acceptance status: 'rejected', 'pending', 'accepted', 'broadcasted', 'received' |
| `created_at` | timestamp | Creation timestamp |
| `processed_at` | timestamp | Processing / validation timestamp |
| `broadcasted_at` | timestamp | Broadcast timestamp |
| `confirmed_at` | timestamp | Peer confirmation timestamp |
| `atoms` | relation(has-many) | Collection of atoms in this molecule |
| `bonds` | relation(many-to-many) | Collection of bonded molecules |

## Relational Design: Bond

| Field Name | Field Type | Description |
|------------|------------|-------------|
| `molecular_hash` | string(64) | Unique identifier for the molecule |
| `bond_hash` | string(64) | Unique identifier for the reference molecule |
| `created_at` | timestamp | Creation timestamp |

## Relational Design: Atom

| Field Name | Field Type | Description |
|------------|------------|-------------|
| `molecular_hash` | string(64) | Unique identifier for the molecule to which this atom belongs |
| `position` | unsigned integer | Position of this atom within its molecule, which is also used to generate the appropriate private key for the originating wallet. |
| `wallet_address` | string(64) | Address for the affected wallet |
| `isotope` | string(1) | Defines the behavior of this atom. Can be set to V, F, M, C, P, or R |
| `token` | string(128), null | For V, F, or C: Optionally hashed identifier for associated token; For P: Not needed |
| `value` | unsigned integer | For V atoms only, used to transmit amounts of value; Assumed to be negative for primary V atoms; otherwise, positive |
| `meta_type` | string(64), null | For M: The polymorphic type of the recipient of metadata |
| `meta_id` | string(128), null | For F: Optionally hashed identifier or the specific non-fungible unit being transacted with; For M, R: Optionally hashed identifier for the object receiving the metadata; For V, F, or C: Not needed; For P: Hash of the identifier for the wallet bundle used to authenticate the peering handshake |
| `meta` | json, null | For M: A JSON-formatted store for metadata being conveyed by this molecule |
| `ots_fragment` | string(2048) | Contains a fragment of the sender wallet’s OTS |
| `created_at` | timestamp | Current time of creation | 

## Relational Design: Cell

| Field Name | Field Type | Description |
|------------|------------|-------------|
| `slug` | string(36) | Unique identifier (GUID or slug) |
| `title` | string(128) | A friendly human-readable title for this cell |
| `consensus_algorithm` | string(36) | Identifier for the consensus algorithm to be used within this cell |
| `virtual_machine` | string(36) | Identifier for the virtual machine to be used within this cell |
| `hashing_algorithm` | string(36) | Identifier for the hashing algorithm to be used within this cell (eg: SHA3-512, KangarooTwelve, SHAKE256, BLAKE2, etc.) |
| `status` | enum | Indicator of cell status: 'stopped', 'paused', 'started', 'archived' |
| `created_at` | timestamp | Creation timestamp |
| `molecules` | relation(has-many) | Collection of molecules in this cell |
| `tokens` | relation(has-many) | Collection of tokens in this cell | 

## Relational Design: Meta

| Field Name | Field Type | Description |
|------------|------------|-------------|
| `molecular_hash` | string(64) | The molecule's identifier that has supplied this meta |
| `position` | unsigned integer | The position of the atom within the molecule that supplied this meta |
| `key` | string(64) | The index identifying the data record being stored |
| `value` | longtext | A flexible store for metadata stored by the given model |
| `target_type` | string(64) | Type of the object model to which this data is attached | 
| `target_id` | string(128) | Identifier for the object model to which this data is attached |
| `created_at` | timestamp | Creation timestamp |
| `revoked_at` | timestamp | Revocation timestamp |

## Relational Design: Token

| Field Name | Field Type | Description |
|------------|------------|-------------|
| `slug` | string(36) | Unique identifier |
| `title` | string(128) | A friendly human-readable title for this token |
| `supply_type` | enum | Determines the supply type: 'replenishable', 'limited' |
| `fungibility` | enum | Determines the fungibility style: 'fungible', 'non-fungible', 'mesh' |
| `supply` | unsigned integer, null | Maximum supply of the token, if applicable |
| `decimals` | unsigned integer, null | How many decimal places a fungible token is subdivided, if applicable |
| `status` | enum | Indicator of token status: 'stopped', 'paused', 'started', 'archived' |
| `created_at` | timestamp | Creation timestamp |
| `updated_at` | timestamp | Update timestamp |
| `molecules` | relation | Collection of molecules involving this token |
| `wallets` | relation(has-many) | Collection of wallets containing a balance in this token | 

## Relational Design: Peer

| Field Name | Field Type | Description |
|------------|------------|-------------|
| `address` | string(45) | IPv4 address. IPv6 address, or international SMS-ready telephone number of the peer |
| `molecular_hash` | string(64) | Unique identifier for molecule whose integrity level represents the integrity of this peer |
| `bundle` | string(64) | Wallet bundle of the peer owner, used for P2P messaging |
| `retries` | unsigned integer(1) | Number of consecutive times this peer failed to respond to a broadcast |
| `broadcasted_molecules` | relation(many-to-many) | Collection of molecules that were successfully broadcast to this peer |
| `received_molecules` | relation(many-to-many) | Collection of molecules that were successfully received from this peer |
| `rejected_molecules` | relation(many-to-many) | Collection of molecules received from the peer that were rejected due to invalidity |
| `status` | enum | Indicator of peer status: 'rejected', 'pending', 'accepted' | 

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

&copy; 2019, WishKnish Corp. All rights reserved.

[dag]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/dag.png?raw=true "Directed Acyclic Graph"
[xmss]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/xmss_tree.png?raw=true "XMSS Tree"
[create]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/create-token.png?raw=true "Create Token Screenshot"
[organism]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/organism.png?raw=true "Knish.IO Organism Diagram"
[molecule]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/molecule.png?raw=true "Knish.IO Molecule Diagram"
[cascade]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/cascade.png?raw=true "Knish.IO Cascade Diagram"
[atoms]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/atoms.png?raw=true "Knish.IO V and I Atom Arrangement"
[cell]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/cell.png?raw=true "Knish.IO Cell Diagram"
[bundle]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/bundle.png?raw=true "Knish.IO Bundle Diagram"
[biometrics]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/biometrics.jpg?raw=true "Knish.IO Biometric UX"
[vatom]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/vatom.png?raw=true "Knish.IO V-Isotope Molecule Diagram"
[matom]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/matom.png?raw=true "Knish.IO M-Isotope Molecule Diagram"
[walletkey]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/walletkey.png?raw=true "Wallet Key Generation"
[address]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/address.png?raw=true "Wallet Address Generation"
[mcrw]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/equation-mcrw.png?raw=true "Markov Chain Random Walk Probability"
[rejection]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/equation-mcrw.png?raw=true "Rejection Probability"
[secondary]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/equation-secondary.png?raw=true "Secondary Bond Equation"
[peering]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/peering.png?raw=true "Knish.IO Peering Algorithm"
[mrec]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/equation-mrec.png?raw=true "Set of Received Molecules"
[mrejection]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/equation-peer-rejection.png?raw=true "Probability of Spontaneous Rejection"
[mrej]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/equation-mrej.png?raw=true "Set of Rejected Molecules"
[lite]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/litenode.png?raw=true "Lite Mode Node Diagram"
[osmosis]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/equation-osmosis.png?raw=true "Set of Origin Cascades for Osmosis"
[achievement]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/edit-achievement.jpg?raw=true "Edit Achievement Screenshot"
[architecture]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/architecture.png?raw=true "Knish.IO Architecture Diagram"
[nakamoto]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/nakamoto.png?raw=true "Nakamoto Coefficient Algorithm"
[infrastructure]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/infrastructure.png?raw=true "Knish.IO Peering Infrastructure"
[matching]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/matching.png?raw=true "Knish.IO Decentralized Exchange Buffer Trade Matching"
[identity]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/identity.png?raw=true "User Identity via Wallet Bundles"
[shadow]: https://raw.githubusercontent.com/WishKnish/KnishIO-Technical-Whitepaper/eugene-teplitsky-dev/shadow.png?raw=true "Claiming a Shadow Wallet"
