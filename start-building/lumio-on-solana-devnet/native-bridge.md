# Native Bridge

## Use Bridge

To be able to use the native bridge you need to get [whitelisted](../get-whitelisted.md).

Native bridging is available on Solana devnet. The bridge deposits funds only to SVM for now and uses SVM addresses.

Program address:

```
GykTBqaRio7Aq99bD1sc94P6n73m8AtbphXoESvRzCmv
```

Currently, it's possible to bridge only using the Lumio CLI, so download it from our [GitHub](https://github.com/pontem-network/lumio-tools/releases/tag/testnet-v0.1).

After downloading, unpack the archive. The **lumio-cli** executable will appear. In your terminal, run the following in the directory with the CLI:

```
chmod +x ./lumio-cli
```

Now you can move the CLI to your binary path. Configure your Solana CLI to Devnet:

```
solana config set --url https://api.devnet.solana.com
```

Create an account if needed:

```
solana-keygen new -o ./keypair.json
```

Request some Devnet SOL:

```
solana airdrop 1
```

Now we are ready to bridge. Run the following command:

```
lumio-cli deposit-sol 100000000 
```

Switch your CLI back to the Lumio Devnet:

```
solana config set --url https://svm.devnet.lumio.io
```

Query the account:

```
solana account <ADDRESS>
```

It should show the deposited balance on your account.

## Architecture

The bridge is scheduled to launch in early summer. The native bridge will operate similarly to other L2 native bridges:

1. Send a transaction containing SOL, an SPL token, or an NFT to a Solana Program.
2. Provide a recipient address.
3. Specify the VM for the deposit.
4. The smart contract emits an event.
5. A sequencer picks up the event and proposes a new deposit transaction to the VM node.
6. The balance appears on the provided address.

<figure><img src="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FPBlZgx8D3RID7xEdotf8%2Fuploads%2Fxvyh5zsQyKU7wU9V32Ph%2FUntitled%20Diagram.drawio%20(4).svg?alt=media&#x26;token=4b91561b-b3a8-4459-a83f-c805d25714f1" alt=""><figcaption></figcaption></figure>

### Withdrawals <a href="#withdrawals" id="withdrawals"></a>

Withdrawals are expected to experience a delay of 3-7 days with Optimism and approximately 7-24 hours with risc0. Initially, before rollup challenging is enabled, there will be a fixed delay of 7 days from the initiation of a withdrawal.
