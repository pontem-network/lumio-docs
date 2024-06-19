# Sequencer

The main difference between the OP sequencer and the Lumio sequencer is as follows:

* The Lumio sequencer supports multiple execution layers, or VMs.
* Unlike traditional sequencers that solve when generating a block, the Lumio sequencer executes transactions as soon as they are submitted to an execution layer for optimal performance.
* This approach prevents the sequencer from becoming a bottleneck in orchestrating all the VMs, as they all operate in parallel independently.

However, the Lumio sequencer still commits deposit transactions, provides transaction confirmations, works closely with the batcher and proposer, and organizes cross-VM calls.

## VMs <a href="#vms" id="vms"></a>

The supported virtual machines include Solana VM, Aptos Move VM, and EVM. Each VM operates as a module that can be connected to the sequencer without necessitating hard forks.During our optimization of the Move VM, we eliminated various elements such as P2P, blocks, and consensus, and optimized the mempool, among other improvements. We believe that additional optimizations and parallel processing for other virtual machines like EVM and Solana will achieve higher performance, with the goal of pushing towards hardware limits. For instance, BlockSTM implemented for EVM.Each VM runs in parallel, meaning they do not obstruct each other. Transactions are executed immediately, with each VM maintaining its own mempool and state.

<figure><img src="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FPBlZgx8D3RID7xEdotf8%2Fuploads%2FPOQvTROAGpAgmkQ0cRFo%2FUntitled%20Diagram.drawio%20(11).svg?alt=media&#x26;token=75266850-7f4f-4e39-9253-5fa4a6fb5809" alt=""><figcaption></figcaption></figure>

When the batcher submits transactions to Data Availability (DA), it generates a mega block containing transactions from all VMs. Since this operation occurs off-chain, it does not slow down other processes. Additionally, due to the potential high volume of transactions that DA may not be able to process quickly, we propose implementing a replication nodes solution.
