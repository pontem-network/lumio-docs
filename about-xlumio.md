# About Lumio

Lumio is an innovative optimistic rollup (Layer 2) solution designed to offer increased transaction processing speeds, enhanced redundancy for uptime, and synchronous connections, enabling smoother liquidity flow. It is tailored to be both developer- and liquidity-friendly, exhibiting agnosticism towards execution and settlement layers.

### Ethereum

The name "Lumio" is derived from the notion of speed and agility, akin to the quick and fast aspects of light. It represents how this Layer 2 solution supercharges Ethereum by being built on top of it. Lumio enables developers to simultaneously use familiar tools, such as the Solidity stack, for their decentralized applications (DApps), while also allowing them to construct new, enhanced components with the Move stack. This Move stack is designed to be faster and more secure, specifically tailored for the development of financial applications, thereby giving traditional development an extra boost in efficiency and security.

### V0

The current iteration of Lumio utilizes Ethereum as its settlement layer, while simultaneously supporting both the Ethereum Virtual Machine (EVM) and the Aptos Move Virtual Machine (VM). This dual support simplifies the development experience: developers can deploy their EVM or Move VM codebases in just a few lines, with a bit more effort required to enable Cross-VM calls.

In the future, Lumio could be expanded to support multiple settlement layers. For instance, for data availability purposes, it might integrate with platforms like Aptos or Celestia.

### Agnostic

The long-term vision for this Layer 2 solution is to be both execution and settlement layer agnostic. This means it aims to support a variety of Virtual Machines (VMs) for developers and to utilize different Layer 1 and Layer 2 platforms for settlement and data layers. This could include Ethereum, Aptos, Optimism, among others. The ultimate goal is to interconnect liquidity across these chains, enhance transaction speeds (depending on the VM used), and reduce transaction costs.

As this vision is a long-term plan, and we are currently in the V0 stage, we encourage you to consult our whitepaper for a more comprehensive understanding of how this system is intended to function in the future.

### Optimism & Superchain

Lumio leverages the best of what OP Stack by Optimism offers, particularly its Rust implementation:

* [Magi](https://github.com/a16z/magi) serves as the node, originally developed by [a16z](https://a16z.com/) and further enhanced with our contributions.
* [Reth](https://github.com/paradigmxyz/reth) is used as the execution layer. We use our own fork, which will be published later.
* Integration of [Move VM](https://github.com/aptos-labs/aptos-core/tree/main/aptos-move/aptos-vm) into Reth, with the capability to compile it to MIPS, demonstrating its potential use in fault dispute games.
* The Ethereum Virtual Machine (EVM) is included as part of Reth.
* The rest follows the default [OP](https://github.com/ethereum-optimism/optimism) components like the batcher, proposer, etc.

While the Rust implementation may still be in its nascent stages, we are confident that it represents the future of the OP stack. It promises high performance and facilitates the integration of new components, such as the Move VM.

Looking ahead, the Layer 2 could be connected to the Optimism Superchain and other Layer 2s within the ecosystem, as we strive to align with the OP architecture and maximize compatibility.

### Whitepaper

The current whitepaper is somewhat outdated. We no longer utilize LLVM, and it is unlikely that we will in the future. Additionally, while we currently use the OP stack for optimal performance, we plan to transition to our own stack. This new stack, inspired by the OP stack, will be tailored to ensure compatibility with Lumio.

{% file src=".gitbook/assets/Lumio L2 Whitepaper.pdf" %}



