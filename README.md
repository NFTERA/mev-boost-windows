![mev-boost](https://user-images.githubusercontent.com/116939/179831878-dc6a0f76-94f4-46cc-bafd-18a3a4b58ea4.png)

#

[![Goreport status](https://goreportcard.com/badge/github.com/flashbots/mev-boost)](https://goreportcard.com/report/github.com/flashbots/mev-boost)
[![Test status](https://github.com/flashbots/mev-boost/workflows/Tests/badge.svg)](https://github.com/flashbots/mev-boost/actions?query=workflow%3A%22Tests%22)

## What is MEV-Boost?

[ORIGINAL](https://github.com/flashbots/mev-boost) | [BINARIES](https://github.com/NFTERA/mev-boost-windows/releases)

`mev-boost` is open source middleware run by validators to access a competitive block-building market. MEV-Boost was built by Flashbots as an implementation of [proposer-builder separation (PBS)](https://ethresear.ch/t/proposer-block-builder-separation-friendly-fee-market-designs/9725) for proof-of-stake (PoS) Ethereum.

With MEV-Boost, validators can access blocks from a marketplace of builders. Builders produce blocks containing transaction orderflow and a fee for the block proposing validator. Separating the role of proposers from block builders promotes greater competition, decentralization, and censorship-resistance for Ethereum.

## How does MEV-Boost work?


PoS node operators must run three pieces of software: a validator client, consensus client, and an execution client. MEV-boost is a sidecar for the Consensus Client, a separate piece of open source software, which queries and outsources block-building to a network of builders. Block builders prepare full blocks, optimizing for MEV extraction and fair distribution of rewards. They then submit their blocks to relays.

Relays aggregate blocks from **multiple** builders in order to select the block with the highest fees. One instance of MEV-boost can be configured by a validator to connect to **multiple** relays. The Consensus Layer client of a validator proposes the most profitable block received from MEV-boost to the Ethereum network for attestation and block inclusion.

![mev-boost service integration overview](https://raw.githubusercontent.com/flashbots/mev-boost/main/docs/mev-boost-integration-overview.png)

## Who can run MEV-Boost?

MEV-Boost is a piece of software that any PoS Ethereum node operator (including solo validators) can run as part of their Beacon Client software. It is compatible with any Ethereum consensus client. Support and installation instructions for each client can be found [here](#installing).


---

See also:

* [boost.flashbots.net](https://boost.flashbots.net)
* [mev-boost Docker images](https://hub.docker.com/r/flashbots/mev-boost)
* [wiki](https://github.com/flashbots/mev-boost/wiki) & [troubleshooting guide](https://github.com/flashbots/mev-boost/wiki/Troubleshooting)
* [mev-boost relay source code](https://github.com/flashbots/mev-boost-relay)
* Specs:
  * [Builder API](https://ethereum.github.io/builder-specs)
  * [Flashbots Relay API](https://flashbots.notion.site/Relay-API-Spec-5fb0819366954962bc02e81cb33840f5)


# Table of Contents

- [Background](#background)
- [Installing](#installing)
- [Usage](#usage)
- [The Plan](#the-plan)
- [API](#api)
- [Maintainers](#maintainers)
- [Contributing](#contributing)
- [Security](#security)
- [License](#license)

# Background

MEV is a centralizing force on Ethereum. Unattended, the competition for MEV opportunities leads to consensus security instability and permissioned communication infrastructure between traders and block producers. This erodes neutrality, transparency, decentralization, and permissionlessness.

Proposer/block-builder separation (PBS) was initially proposed by Ethereum researchers as a response to the risk that MEV poses to decentralization of consensus networks. They have suggested that uncontrolled MEV extraction promotes economies of scale which are centralizing in nature, and complicate decentralized pooling.

Flashbots is a research and development organization working on mitigating the negative externalities of MEV. Flashbots started as a builder specializing in MEV extraction in proof-of-work Ethereum to democratize access to MEV and make the most profitable blocks available to all miners. >90% of miners are outsourcing some of their block construction to Flashbots today.

In the future, [proposer/builder separation](https://ethresear.ch/t/two-slot-proposer-builder-separation/10980) will be enshrined in the Ethereum protocol itself to further harden its trust model.

Read more in [Why run mev-boost?](https://writings.flashbots.net/writings/why-run-mevboost/) and in the [Frequently Asked Questions](https://github.com/flashbots/mev-boost/wiki/Frequently-Asked-Questions).

# Installing

`mev-boost` can run in any machine, as long as it is reachable by the beacon client. The default port is 18550. The most common setup is to install it in the same machine as the beacon client.


## Binaries

Each release includes binaries from Linux, Windows and macOS (portable build, for amd and arm). You can find the latest release at
https://github.com/NFTERA/mev-boost-windows/releases


# Maintainers

- [@NFTERA](https://github.com/NFTERA)
- [@lcalasso27](https://github.com/lcalasso27)
- [@laneveyga313](https://github.com/laneveyga313)

# Contributing

[Flashbots](https://flashbots.net) is a research and development collective working on mitigating the negative externalities of decentralized economies. We contribute with the larger free software community to illuminate the dark forest.

You are welcome here <3.

- If you have a question, feedback or a bug report for this project, please [open a new Issue](https://github.com/NFTERA/mev-boost-windows/issues).
- If you would like to contribute with code, check the [CONTRIBUTING file](CONTRIBUTING.md) for further info about the development environment.
- We just ask you to be nice. Read our [code of conduct](CODE_OF_CONDUCT.md).

# Security

If you find a security vulnerability on this project or any other initiative related to Flashbots, please let us know sending an email to security@flashbots.net.

## Audits

- [20220620](docs/audit-20220620.md), by [lotusbumi](https://github.com/lotusbumi).

# License

The code in this project is free software under the [MIT License](LICENSE).

Logo by [@lekevicius](https://twitter.com/lekevicius) on CC0 license.

---

Made with ☀️ by the ⚡🤖 collective.
