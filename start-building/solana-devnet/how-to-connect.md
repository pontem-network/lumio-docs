# How to connect

A Devnet is available, running on its own Ethereum L1 and equipped with Solana VM, Move VM, and EVM on board.&#x20;

## Solana VM

RPC endpoint + faucet:

```
https://svm.devnet.lumio.io
```

Use with Solana CLI:

```
solana config set --url https://svm.devnet.lumio.io
```

## Move VM

RPC endpoint for Aptos CLI:

```
https://mvm.devnet.lumio.io
```

Faucet endpoint:

```
https://faucet.devnet.lumio.io
```

## EVM

RPC endpoint:

```
https://l2.devnet.lumio.io
```

## Universal RPC

Cross-chain calls will enable a universal RPC, allowing the use of Metamask or Phantom to execute a Move VM transaction. This universal RPC will operate by utilizing cross-VM call functionality, where call data needs to be serialized into a byte format recognized by the specific VM targeted for the call. Using the cross-VM calls module on the initial chain, the call is then executed on another chain.
