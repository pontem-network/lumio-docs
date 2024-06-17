# Use Testnet

Lumio L2, now live on the Ethereum Sepolia Testnet, invites users and developers to start their journey.

**Important:** The L2 is designed to be compatible with both EVM RPC and Move VM RPC. This means it allows the use of EVM RPC for Move VM calls. However, at this stage, to interact with both supported VMs, users will need to use the Pontem Wallet as a unified solution, or two separate wallets (such as Petra and Metamask). These wallets must be connected to the appropriate RPCs to fully experience the integration of the two VMs.

### Pontem Wallet

**Both EVM & Move VM**

[Download & Install Pontem Wallet](https://chromewebstore.google.com/detail/pontem-aptos-wallet/phkbamefinggmakgklpkljjmgibohnba)

This method of connection has been available since the release of **Pontem Wallet v2.5.4**. Be prepared to update the extension manually or wait for Chrome to update it automatically.

If you need to update wallet manually see the [following instruction](https://support.cloudhq.net/how-to-manually-update-chrome-extensions/).

**Unlock EVM features**

First of all, let's unlock EVM features in the Pontem Wallet.&#x20;

1. Click on 'Create Wallet'.
2. Select 'Ethereum' as your wallet type.
3. Proceed by following the on-screen instructions.

**Connect**&#x20;

1. Open the Pontem Wallet.
2. Select **“Settings”**.
3. Choose **“Network Mode”**.
4. From the list of supported networks, select **“Lumio L2”**.
5. Your wallet will switch to the **“Lumio L2”** network. To return to the Aptos mainnet, simply go back to the same menu and select **“Mainnet”**.

<div align="center" data-full-width="false">

<figure><img src="../../../.gitbook/assets/Снимок экрана 2023-12-18 в 16.22.35.png" alt="" width="360"><figcaption></figcaption></figure>

</div>

**Only Move VM**

This method allows you to connect to Lumio L2 using earlier versions of the **Pontem Wallet**.

1. Open the Pontem Wallet.
2. Access the menu by clicking the 4-dot button in the top right corner.
3. Select **“Expand View”**.
4. Reopen the menu.
5. Choose **“Settings”**.
6. Navigate to **“Networks”**.
7. Select **“Custom”**.
8. Update the fields as follows:
   * **Network Name**: Lumio L2
   * **Network Short Name:** Lumio L2
   * **ChainId:** 2
   * **API URL**: `https://mvm.testnet.lumio.io/v1`
   * **Indexer URL**:  `https://indexer.testnet.lumio.io/v1/graphql`
   * **Explorer URL for account:** `https://explorer.testnet.lumio.io/address/`
   * **Explorer URL for transaction**: `https://explorer.testnet.lumio.io/tx/`&#x20;
   * **Explorer GET params:** `?`
9. Click the “Save” button.
10. Return to the “Settings” menu and switch the network in **“Network Mode”** to “Lumio L2”.

**Important:** Note: In this mode, it is essential to manually request funds from the faucet. See [Faucet](faucet.md).

***

### Other wallets

#### Metamask

In this mode, only the EVM part will be supported.

[Download & Install Metamask](https://metamask.io/)

To add Lumio L2 as a custom network to MetaMask:

1. Open the MetaMask browser extension.
2. Click the network selection dropdown button at the top of the extension.
3. Select **Add network**.
4. Choose **Add a network manually**.
5. In the **Add a network manually** dialog, enter the following information:
   * **Network Name:** Lumio L2 Testnet
   * **RPC Endpoint**: `https://testnet.lumio.io`
   * **Chain ID:** 9990
   * **Currency Symbol:** ETH
   * **Block Explorer:** `https://explorer.testnet.lumio.io`

<figure><img src="../../../.gitbook/assets/Снимок экрана 2023-12-18 в 16.29.15.png" alt=""><figcaption></figcaption></figure>

#### Petra

In this mode, only the Move VM part will be supported.

[Download & Install Petra](https://chromewebstore.google.com/detail/petra-aptos-wallet/ejjladinnckdgjemekebdpeokbikhfci)

**Important:** The Petra wallet is highly efficient, particularly for operations involving Decentralized Applications (DApps). However, for transferring funds to another account, the Pontem wallet is the recommended choice due to its optimized features for such transactions.

1. Open the Petra wallet.
2. Access Settings from the bottom menu.
3. Select “Network”.
4. Click the “Add” button at the bottom.
5. Enter the following parameters:
   * **Name**: Lumio L2
   * **Node URL**: `https://mvm.testnet.lumio.io/v1`
   * **Faucet URL:** `https://faucet.testnet.lumio.io`
   * Click on “Add Network”.
6. Finally, select “Lumio L2” from the list of networks.

<figure><img src="../../../.gitbook/assets/Снимок экрана 2023-12-18 в 16.34.20.png" alt="" width="375"><figcaption></figcaption></figure>
