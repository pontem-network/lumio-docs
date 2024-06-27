# How to connect

To be able to use the faucet and native bridge on Solana, you need to get [whitelisted](../get-whitelisted.md).

A Devnet is available equipped with Solana VM, Move VM, and EVM on board.&#x20;

## Solana VM

RPC endpoint + faucet:

```
https://svm.devnet.lumio.io
```

Use with Solana CLI:

<pre><code><strong>solana config set --url https://svm.devnet.lumio.io
</strong></code></pre>

Create a new key if needed:

```
solana-keygen new -o ./keypair.json
```

Request faucet:

```
solana airdrop 1
```

{% hint style="warning" %}
If you see an error like this, it means your account needs to be whitelisted first:\
\
Error: airdrop request failed. This can happen when the rate limit is reached.
{% endhint %}

## Move VM

The Move VM will be available once the native bridge starts working with it, expected in June-July.

## EVM

The Ethereum VM support is coming soon.

## Universal RPC

Cross-chain calls will enable a universal RPC, allowing the use of Metamask or Phantom to execute a Move VM transaction. This universal RPC will operate by utilizing cross-VM call functionality, where call data needs to be serialized into a byte format recognized by the specific VM targeted for the call. Using the cross-VM calls module on the initial chain, the call is then executed on another chain.
