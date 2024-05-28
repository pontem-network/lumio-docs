# VMs Differences

### EVM

The Ethereum Virtual Machine (EVM) implementation in Lumio closely resembles the standard Ethereum mainnet and other networks.

However, there are some differences that you should be aware of. For detailed information, visit the [Optimism (OP) portal](https://stack.optimism.io/docs/releases/bedrock/differences/), where these differences are thoroughly explained. Most of these variations are implemented to maintain compatibility with standard EVM protocols, which can be slightly different in the context of L2, as L2 is not a Layer 1 (L1) protocol and often requires specific workarounds.

An important aspect to note is that the default deployment of L2 includes a Cross VM contract in the genesis block, which is not typically found in the standard OP stack L2.

Considering the presence of two virtual machines and the mapping between accounts, it's crucial to understand that direct access from an EVM account to a Move VM account using a private key is not possible. Instead, connecting accounts across these VMs can only be achieved through the use of smart contracts.

## SVM

### Move VM

The Move VM in our system is implemented using the standard [Aptos framework](https://github.com/aptos-labs/aptos-core/tree/main/aptos-move/framework), albeit with some modifications that we detail in this section. Essentially, it’s a fork of the Aptos Move VM, adhering to the same design principles. The majority of the changes were implemented to enable the compilation of the Move VM into MIPS, as required by Cannon for generating fault proofs in the future, which we have successfully accomplished.

#### ZK Primitives

The ZK primitives have been removed from the Move VM, primarily because most of them operate using threads, and integrating them currently requires additional effort.

The specific modules that have been removed include:

```jsx
ristretto255_bulletproofs
ristretto255
bls12381
crypto_algebra
```

#### Framework

In our L2, the native coin within the Move VM is ETH, and we plan to enable gas payments in various types of coins in the future. Currently, the coin representing ETH in the Move VM is `0x1::native_coin::NativeCoin`. This implementation is similar to the native coin concept in the Aptos framework. However, this abstraction has been chosen for simplicity and to facilitate future adaptability.

We have also removed contracts related to staking or governance initially implemented in the framework. These may be reintroduced after reworking, but at this stage, as the L2 sequencer is singular and a shared sequencer is not yet operational, they have been omitted.

The list of removed modules includes:

```jsx
aptos-framework/sources/aptos_governance.move
aptos-framework/sources/configs/staking_config.move
aptos-framework/sources/delegation_pool.move
aptos-framework/sources/governance_proposal.move
aptos-framework/sources/stake.move
aptos-framework/sources/staking_contract.move
aptos-framework/sources/staking_proxy.move
aptos-framework/sources/vesting.move
aptos-framework/sources/voting.move
```

Additionally, some logic has been modified, such as aspects related to gas, block production (especially concerning validator checks), and genesis. A comprehensive list of these changes will be detailed later.

**Important:** The use of `0x1::aptos_coin::AptosCoin` in your transactions or API calls is still possible, as it is proxied at the VM level.

### Cross VM calls

Both VMs support calls to one another. This capability is implemented through a) a smart contract deployed to the EVM at the genesis of L2, and b) the `vms` module, which is part of the framework deployed in the Move VM.

For more detailed information on these calls, please refer to the specific section dedicated to them. This brief mention is to clarify the implementation we have in place.

\
