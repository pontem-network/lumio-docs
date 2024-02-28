# Virtual Machines

The current L2 V0 supports two virtual machines: the Move VM and the Ethereum Virtual Machine (EVM). Both operate in isolated modes, without shared memory or resources. However, they can communicate through a messaging system similar to how calls are executed between different chains using solutions like LayerZero. This communication occurs within a single transaction and on the same chain.

Such a setup allows developers to perform calls between VMs using callback approaches, facilitating the movement of liquidity (assets) between the two Virtual Machines.

### Execution

As the two VMs presented have fundamentally different concepts, they require isolation in their execution layers. The Move VM focuses on safety, employing a unique resources model and supporting parallel execution, while the EVM, as the pioneer of smart contracts, has a different approach.

At the current stage, the primary VM supported is the EVM. Move VM transactions are effectively encapsulated within EVM transaction calldata. This encapsulation is where the integration occurs. In the future, the Ethereum RPC will be adapted to the extent possible, allowing for the exclusive use of EVM-compatible wallets like MetaMask.

We won't delve into intricate details here, but it's important to note that account mappings also occur in this process. For example, when you deposit ETH on your account in L2, it automatically reflects your balance in both the EVM and Move execution layers.

The Move VM's design for parallel execution means that transactions specific to it can be processed simultaneously. For more details, you can refer to the [Block-STM](https://medium.com/aptoslabs/block-stm-how-we-execute-over-160k-transactions-per-second-on-the-aptos-blockchain-3b003657e4ba) algorithm proposed by Aptos. In summary, transactions are reordered several times to find the optimal parallel execution path. Transactions affecting the same resources are executed sequentially, while those that can be processed in parallel within the Move VM are done so. However, transactions on the EVM remain sequential. Additionally, any Cross-VM messaging affecting the EVM must also be executed sequentially.

While the sequential processing of EVM-related transactions might slow down the overall execution, it represents a balance between adoption and performance. For example, with the future launch of the Optimism Supercomputer, the EVM could potentially be shifted to another rollup.

**Important:** Currently, in L2, both Move VM and Solidity transactions are processed sequentially. This is for simplicity during the early stages. However, by the time of the mainnet launch, Move VM transactions are expected to be run in parallel.

TODO: Create graphics illustrating the two VMs and transaction flows.

\


