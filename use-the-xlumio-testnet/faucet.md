# Faucet

### Move VM

#### Wallet

In case of wallet, just add the faucet link in the network settings like on the screenshot. It supported by most of the wallets.

Copy the faucet URL:

```
https://faucet.testnet.lumio.io
```

#### CLI

When using the CLI, provide the faucet link during the `aptos init` command:

```sh
https://faucet.testnet.lumio.io
```

Executing this command will automatically fund your account.

#### CURL

You can also use `curl` for the same purpose:

```sh
curl -X POST "https://faucet.testnet.lumio.io/mint?amount=1000000&address=43417434fd869edee76cca2a4d2301e528a1551b1d719b75c350c3c97d15b8b9"
```

### EVM

To request funds on the EVM, first create a new account in MetaMask or any other EVM-compatible wallet. Ensure that the wallet is connected to the Supercharger network. Once set up, you can use the public faucet to obtain funds.

[Visit EVM faucet](https://claim.lumio.network)

\
\
