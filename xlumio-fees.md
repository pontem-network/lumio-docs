# Fees

The network fees are not yet finalized and will be subject to change after successful testing. For the EVM, the fees might align with those used in OP. However, for the Move VM, the fee structure will likely differ.

In the V0 stage, transaction fees are paid in ETH.

The transaction fee on L2 comprises two components: an execution fee and a storage fee. This is because virtually every transaction must be posted to the settlement layer, enabling the recovery of transaction history and verification of L2 transactions. The fees also depend on the load of the settlement layer, meaning they can fluctuate, sometimes being lower or higher. For more details, refer to the OP [documentation](https://community.optimism.io/docs/developers/build/transaction-fees/).

Furthermore, as Pontem L2 is settlement-agnostic, in V0 transactions will initially be settled on Ethereum. However, future plans involve using Aptos and other protocols to store transaction data, potentially reducing transaction costs significantly. This approach also allows for a fallback to Ethereum if the primary settlement layer encounters issues.
