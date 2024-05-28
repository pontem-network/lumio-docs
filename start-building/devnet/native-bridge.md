# Native Bridge

The bridge is scheduled to launch in early summer. The native bridge will operate similarly to other L2 native bridges:

1. 1.Send a transaction containing SOL, an SPL token, or an NFT to a Solana Program.
2. 2.Provide a recipient address.
3. 3.Specify the VM for the deposit.
4. 4.The smart contract emits an event.
5. 5.A sequencer picks up the event and proposes a new deposit transaction to the VM node.
6. 6.The balance appears on the provided address.

<figure><img src="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FPBlZgx8D3RID7xEdotf8%2Fuploads%2Fxvyh5zsQyKU7wU9V32Ph%2FUntitled%20Diagram.drawio%20(4).svg?alt=media&#x26;token=4b91561b-b3a8-4459-a83f-c805d25714f1" alt=""><figcaption></figcaption></figure>

### Withdrawals <a href="#withdrawals" id="withdrawals"></a>

Withdrawals are expected to experience a delay of 3-7 days with Optimism and approximately 7-24 hours with risc0. Initially, before rollup challenging is enabled, there will be a fixed delay of 7 days from the initiation of a withdrawal.
