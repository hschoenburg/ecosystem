# State of the Cosmos

This document attempts to define what it would mean for the Cosmos Network to succeed in the long-term, analyses the current state of affairs, and in accordance with the difference between the desired & current states, enumerates a list of "strategic prongs" which must be executed in order to facilitate the eventual success of the "internet of blockchains".

This document is a working draft & suggested revisions or additions are most welcome.

This document tries to collect many ideas into a single structured framework. The genealogy of ideas is always tricky to ascertain and these ideas have no single owner or origin - most are the results of discussions between a variety of people & companies.

## Definitions

- *Tendermint* (or *Tendermint Core*) is the consensus engine [here](https://github.com/tendermint/tendermint).
- The *Cosmos SDK* is the Golang SDK [here](https://github.com/cosmos/cosmos-sdk).
- *Gaia* is the specific blockchain [here](https://github.com/cosmos/gaia).
- *IBC* is the inter-blockchain protocol [here](https://github.com/cosmos/ics).
- *Zones* are blockchains which support the IBC protocol (*Hubs* are also zones).
- The *Cosmos Network* is the set of zones accessible from Gaia through the IBC protocol.
  These zones are not necessarily directly connected - they might be many hops away - but they speak "canonical IBC", connect to other public zones, and together constitute a network of interconnected chains.

## Motivating rationale

### What does a successful Cosmos network look like?

A successful Cosmos network would consist of hundreds to thousands of blockchains, operating on a few common, peer-reviewed consensus algorithms (or various configurations and implementations of the same consensus algorithm), using well-analysed and battle-tested proof-of-stake Sybil resistance mechanisms for cryptoeconomic incentivisation of validating nodes, connected by a flexible interchain communication protocol allowing users of the Cosmos network to seamlessly interact with decentralised applications with functionality composed across many separate, specialised chains.

Existing chains in the Cosmos Network can gradually scale vertically over time with performance & maintenance improvements to the common underlying consensus & state machine software, and quickly scale horizontally when necessary by launching new chains, specialising parts of their application to run separately, and interfacing between them using the interchain communication protocol and flexible interchain proof-of-stake collateralisation layers built on top.

New entrants can easily spin up a chain, recruit a validator set, connect themselves to the network, and benefit from the litany of existing applications & assets which become immediately accessible. Users of existing chains on the network can elect to experiment with new chains & protocols, while keeping their existing assets and carefully protecting themselves from too much risk.

Users can interface with many chains through well-designed, ergonomic, safety-conscious user-facing software. This user-facing software can be accessed through a wide variety of frontend interfaces, but uses common core libraries for safety-critical tasks such as transaction composition, signing, and key management, allowing different devices & frontends to pool resources for secure engineering & auditing of key cryptographic logic.

Eventually, the 'Cosmos Network' becomes background infrastructural substrate, almost invisible to the end users because the functionality has been taken for granted - just as you don't need to bother asking if your laptop supports TCP/IP, eventually, should the network succeed, users won't bother asking if your new blockchain supports IBC. But, even then, the network will need to continue upgrading to handle higher throughput and adapting the latest innovations in distributed systems & cryptography research in order to continue to provide a secure infrastructural backend layer for the decentralised web.

### Necessary prongs

What will it take for the Cosmos Network to succeed - or more specifically, to get
from where we are now to the successful end state defined above? This document breaks
down that question into a set of "Mission prongs" - necessary strategic components,
which must be executed by some organisation (or organisations) in order to realise
the success of the Cosmos Network.

#### Consensus engine design & development

The Cosmos Network will need one or several BFT consensus engines for use by the zones.

With respect to the current primary candidate, Tendermint, this prong will consist of:

- Research deployment (of new distributed systems research, e.g. pipelining, HotStuff, Flexible BFT)
- Greater configurability as a general consensus engine (choose between algorithms)
- Performance engineering (improved database & network performance)
- Interface (ABCI) engineering (state machine concurrency)
- Multiple implementations in separate languages (ideally wire-compatible)
- Implementation review, auditing, and formal verification
- Integration with secure hardware for consensus signing
- Secure proof-of-stake & light client algorithm design (must be considered in unison)

#### State machine toolkit design & development

The Cosmos Network will need at least one and likely several state machine toolkits for use in building zones.

This prong will consist of, for any or many frameworks:

- Facilitation of vertical scaling
  - Performance engineering
  - Database engineering
  - Concurrency in transaction execution
- Developer experience
  - Interface design (module abstractions, object-capabilities)
  - Bindings to useful libraries (e.g. different databases, cryptography libraries)
- Interface (ABCI) engineering (in conjunction with Tendermint)
- Module development (of common modules for use by many zones)
- Module curation & integration (of modules developed across the Cosmos Network)
- Multiple implementations of equally capable toolkits in separate languages
- Implementation review, auditing, and verification
- Integration with secure hardware for end-user signing (ideally in a standardised fashion)

#### Interchain communication design & development

The Cosmos Network will need a secure, performant, standardised interchain communication protocol for arbitrary cross-chain message passing and transfers of state, assets, data, and code between zones.

This prong will consist of:

- Research deployment (of relevant cryptography & distributed systems research, e.g. ZKP light clients)
- Protocol design (of the core IBC standard)
- Protocol stewardship & governance (steering committee, ecosystem working group)
- Safety & liveness analysis of complex multi-chain topologies
- Multiple implementations of the standard in separate languages
- Implementation review, auditing, and verification

#### Zone developer relations & communication

The Cosmos Network will require well-designed, low barrier-to-entry, well-documented instructions and tutorials for building, launching, and operating zones.

This prong will consist of:

- Developer experience design for the core infrastructure software
- Example zone tutorials
- Help & support in launching zones
- Hackathons & demonstrations
- Software integrations with useful libraries
- Validator recruiting assistance
- Reproducible secure software development practices

#### Zone development

The Cosmos network will need a multitude of zones fulfilling different purposes and constructed with different user-bases in mind but connected to each other over IBC for seamless interoperation.

This prong will consist of a wide variety of zones:

- End-user vertical DApp zones (e.g. Terra)
- Platform / smart contract zones (e.g. Agoric, CosmWasm)
- Support zones (e.g. peg-zones)
- More examples
  - Private payments
  - Oracle market
  - Subscription automation
  - DAOs
  - Name services
  - Social media
  - Mix-net public-key infrastructure
  - Decentralised exchange
- Many we probably can't even conceive of yet.

#### Zone operation

The Cosmos Network will need facilities, companies, and resources for operating zones in a sustainable, secure manner over time.

This prong will consist of:

- Organisations or protocols to facilitate launching zones
- Secure, sustainable validators operating zones
- Validators, companies, or products relaying IBC packets
- Zone maintenance & upgrades
- Scaling zones over time in line with user demand

#### End-user application infrastructure

The Cosmos Network will need core, common, well-audited infrastructure for single-chain and multi-chain applications built on top of zone backends.

This prong will consist of:

- Libraries for transaction authoring & signing
- Libraries for state management & authentication
- Libraries for various cryptographic operations which must occur on the edge
- Secure light client implementations for various platforms
- Libraries for interaction with IBC, including multi-chain user flows

#### End-user application development

The Cosmos Network will need applications (what else are all these blockchains for?!) that provide real, long-term utility to users of the Cosmos Network outside of cryptocurrency speculation or technical experimentation.

This prong will consist of:

- Applications running on specific zones
  - Single-chain wallets
  - Single-chain explorers
  - Single-chain Dapps
- Applications running across multiple zones
  - Multi-chain wallets
  - Multi-chain explorers
  - Multi-chain Dapps

#### End-user relations & communication

The Cosmos Network will need marketing & communication of applications built on various zones (or composed of parts spread across many zones) to their target end users, and sustainable operation of those applications.

This prong will consist of:

- Communication & marketing of end-user applications to potential users
- Communication of advantages of the decentralised web
- Communication of caveats and limitations of the decentralised web
- Communication of instructions & guidelines for secure key management & blockchain interaction
- Application operations
- Application end-user support

#### Industrial / consortium / private-chain connections

The Cosmos Network will benefit from connections to partially or fully private chains or consortium-operated chains run by existing businesses or industries.

This prong will consist of:

- Integration of private or consortium-controlled chains into the Cosmos Network over IBC
- Business development with existing companies
- Integration of Cosmos software stack into existing consortium toolkits (e.g. Hyperledger)

#### Existing network & asset bridging

The Cosmos Network will need bridges to existing assets & networks to bring existing users onto the Cosmos, increase the value of participating in the network, and allow existing assets & applications to benefit from the improved core technologies of new zones.

This prong will consist of:

- Bridges to state & assets of existing networks
  - Bitcoin
  - Ethereum
  - Ethereum Dapps
  - Zcash
  - Tezos
  - Handshake

#### Proof-of-concept demonstration

The Cosmos Network will need "poster child" zones or products to demonstrate the functionality, utility, and interoperability of the Cosmos Network in the most compelling fashion: by example.

This prong will consist of:

- Specific zone or zones which are particularly associated with the "Cosmos Network" brand
- Demonstrating all these backend software technical improvements
- Common brand names for the technology stack & network

## Revenue models

How might companies which pursue these open-source development efforts make money?

### Atom appreciation

Some companies hold a fraction of the ATOM supply. If these companies continues to develop, upgrade, and bring usage to the Gaia blockchain, these ATOM tokens may appreciate in value.

This could provide both one-time sums (if ATOMs are sold in bulk) and recurring revenue (from selling staking proceeds over time).

### Contracts with the Interchain Foundation

Companies could solicit continued funding from the Interchain Foundation. This would need to be used for furtherance of projects in line with the Foundation's mandate under Swiss law. Most of the development work outlined in this document likely falls under that mandate.

This would likely provide fixed-term grants negotiated in advance.

### Development grants from on-chain public good funding sources

Companies could solicit funding from on-chain sources, such as Gaia's community pool, or other such funding sources which emerge on the Cosmos Network over time (perhaps including contributions from multiple chains over IBC).

This could provide either one-time grants or recurring revenue, depending on the kind of funding (e.g. currently community pool grants are one-time, and currently the Zcash Dev Fund is recurring revenue).

### Contracting

Companies could pursue contracts for software development & support work with zone operators and other entities who want development assistance for their projects on the Cosmos Network.

This would likely provide recurring revenue, sourced from multiple projects.
