# Optimism Testnet

This is the Lumio testnet deployed on the Ethereum Sepolia testnet. In the near future, it will be upgraded with a new architecture derived from the implementation of MultiVM.

The main difference is that this is the first implementation of EVM and Move VM within the same execution environment. It is considered legacy compared to the devnet, which is represented as Lumio v2.&#x20;

The reason for migrating to a new architecture, which also allows the addition of SVM into the L2, is highlighted:

> At that juncture, our resolution was to integrate the EVM and Move VM, aiming for minimal modifications to either, thereby enabling deployment on both platforms without necessitating any changes. This concept piqued our interest, leading us to harness the capabilities of Reth as our foundation. Through this innovative approach, we crafted what is now known as Lumio V1, a unique solution that marries the best of both worlds.
>
> Yet, this integration posed several challenges, especially when prioritizing performance enhancements. The Move VM, as utilized in Aptos, exhibits exceptional efficiency, outshining other virtual machine solutions with benchmarks showing 30-60k transactions per second (TPS). Our recent tests affirm this impressive performance. On the contrary, Ethereum nodes fail to approach these figures, and the melding of Reth with the Move VM does not support achieving such rapid execution rates. The significant time and resources invested in merging these two technologies could arguably be better spent on more innovative projects. Our goal is to offer an incredibly fast solution, a target that becomes elusive within the constraints of the current framework. Also, contemplating the future integration of more execution runtimes, like the Solana VM, poses a significant challenge. Merging these different environments while striving to boost performance will be a complex task if ever possible.
>
> In today's modular world, the ideal scenario is for modules to easily interconnect without requiring extensive modifications. Theoretically, numerous distinct execution environments can coexist on the same layer, and integrating them shouldn't demand significant effort—merely orchestration. This vision emphasizes simplicity and efficiency in creating a cohesive system, where the heavy lifting is done through smart orchestration rather than extensive customization or redevelopment.

We plan to phase out the current testnet shortly and replace it with the devnet, which provides a shared execution environment. If you have used the testnet, your account address will be remembered and will be eligible for future initiatives.
