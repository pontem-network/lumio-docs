# Optimism Superlumio

#### A Gateway to the Optimism Superchain

SuperLumio marks the initial phase of the Lumio Layer 2 (L2) on the Optimism Superchain, launched as a pure Ethereum Virtual Machine (EVM) fork with the support of Conduit technology. This platform is designed to serve as a testnet-in-production, akin to Kusama for Polkadot, allowing for active engagement, TVL growth, and project launches. The foundation of SuperLumio on the EVM paves the way for future releases to introduce a cross-VM heterogeneous block space, expanding its capabilities.\
\
In anticipation of future developments, SuperLumio's roadmap includes the integration of both Move VM and EVM, evolving into a comprehensive Lumio platform as part of the L3 plan. This will eventually merge into a unified platform, enhancing the ecosystem's functionality.&#x20;

Currently, SuperLumio employs a centralized sequencer for transaction processing (like any other OP L2s), with plans to adopt a decentralized model. This transition towards a shared sequencer across the Optimism chains is a crucial step towards achieving greater security and transparency within the ecosystem.

Importantly, SuperLumio has been deployed on the Ethereum mainnet, operating with real assets, which sets it apart from traditional testnets. Users and developers engaging with SuperLumio should be aware of its real-stakes environment.

## Use the SuperLumio

### Metamask

[Download & Install Metamask](https://metamask.io/)

Visit the [Lumio](https://lumio.io) website and simply click the "Connect to Mainnet" button, or proceed with the following instructions for alternative methods.

To add SuperLumio L2 as a custom network to MetaMask:

1. Open the MetaMask browser extension.
2. Click the network selection dropdown button at the top of the extension.
3. Select **Add network**.
4. Choose **Add a network manually**.
5. In the **Add a network manually** dialog, enter the following information:
   1. **Network Name:** SuperLumio
   2. **RPC Endpoint**: `https://mainnet.lumio.io`
   3. **Chain ID:** 8866
   4. **Currency Symbol:** ETH
   5. **Block Explorer:** `https://explorer.lumio.io`

<figure><img src=".gitbook/assets/Снимок экрана 2024-02-28 в 04.00.49.png" alt=""><figcaption></figcaption></figure>

### Other wallets

You can do the same with other EVM based wallets.

Additionally, support for the Pontem wallet is on the horizon, further enhancing accessibility and user experience right from the start.

## Bridge

The bridging process can take anywhere from 1 minute to 30 minutes. Please plan accordingly.

SuperLumio enables users to deposit ETH and other tokens, such as USDC, USDT, and more, from the Ethereum L1 mainnet. This can be accomplished through the native L1 to L2 bridge, which is accessible via the following links, including those from our partners:

* [Lumio Bridge](https://superbridge.lumio.io) - This bridge is maintained by Lumio. It's important to note that while the bridge supports deposits of ETH and other tokens from the Ethereum L1 mainnet, withdrawals are not yet available through the user interface. We are diligently working on implementing this feature and expect it to be available shortly.&#x20;

Over time, additional non-native bridges, such as LayerZero or Wormhole, may be integrated, enabling the deposit of both wrapped and native assets.

## :droplet: Dashboard

Our dashboard is currently operating in silent mode, meticulously recording all user actions on the L2, including deposits and transfers. With the upcoming launch of DApps, such as Narswap, we will soon expand our monitoring to cover swaps, liquidity provisions, and more.

Visit [Dashboard](https://dashboard.lumio.io/)

## Network Information

|                 |                           |
| --------------- | ------------------------- |
| Network Name    | SuperLumio                |
| RPC Endpoint    | https://mainnet.lumio.io  |
| Chain ID        | 8866                      |
| Currency Symbol | ETH                       |
| Block Explorer  | https://explorer.lumio.io |
| Bridge          | https://bridge.lumio.io   |
| Block Time      | 2 seconds                 |
| L1              | Ethereum Mainnet          |

## Contracts

#### L1

The contracts deployed on the Ethereum Mainnet are:

| Contract Name                     | Deployment Addresses                       |
| --------------------------------- | ------------------------------------------ |
| SystemConfigProxy                 | 0xFb252d6199AEfeE6938a1c57213AAd96ecD2650c |
| L2OutputOracleProxy               | 0xffB004874CbBF8692B5f397B602f4B8a630aeD59 |
| OptimismPortalProxy               | 0x9C93982cb4861311179aE216d1B7fD61232DE1f0 |
| OptimismMintableERC20FactoryProxy | 0xccc6Fc5B866D34a7A4C40455a3cCfaa0cbFc145B |
| L1StandardBridgeProxy             | 0xdB5C6b73CB1c5875995a42D64C250BF8BC69a8bc |
| L1CrossDomainMessengerProxy       | 0x6c10d7e5750b21729Eb863Cf89E5b48850E6d97D |
| L1ERC721BridgeProxy               | 0x9bF59F099d4306B52C7624c90B6d5FD75ab8513b |

#### L2

The deployment addresses for L2 contracts are consistent across the entire Optimism stack. You can find these addresses as constants in the Optimism [repository](https://github.com/ethereum-optimism/optimism/blob/c87a469d7d679e8a4efbace56c3646b925bcc009/packages/core-utils/src/optimism/constants.ts#L11).

## Fees

The fee model is akin to Optimism's, based on the Data Availability (DA) costs of transactions and execution expenses. For more details on L2 fees, please refer to our further [documentation](https://docs.optimism.io/stack/transactions/fees).&#x20;

With the recent update to [span batches](https://x.com/optimism/status/1760711365168353442?s=46\&t=IPOCXW0FiDbuT5rNrxqOLA), fees have become relatively more affordable. Moreover, the impending integration of ProtoDankSharding promises to further reduce costs once activated on SuperLumio

