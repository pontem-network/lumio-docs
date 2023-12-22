# CLI

You can also interact with the L2 using CLI tools for both Move VM and EVM.

* For the Move VM, the Aptos CLI is supported.
* For the EVM, any compatible CLI tool can be used.

### Move VM

[Download & install](https://aptos.dev/tools/aptos-cli/install-cli/) the Aptos CLI.  Ensure to adhere to the instructions for a proper installation of the CLI.

During the `init` command, configure the following RPC and faucet URLs:

* RPC: `https://mvm.testnet.lumio.io/v1`
* Faucet: `https://faucet.testnet.lumio.io`&#x20;

Additionally, these URLs can be used as parameters in the CLI with the `--url` or `--faucet-url` options.

### EVM

Any EVM-compatible CLI or tool can be utilized for this purpose. Commonly, we use the `cast` CLI from [Foundry](https://book.getfoundry.sh/cast/).

To use `cast`, simply include the RPC URL as a parameter `--rpc-url`. For example:

```jsx
cast <command> ... --rpc-url https://testnet.lumio.io
```

\
\
