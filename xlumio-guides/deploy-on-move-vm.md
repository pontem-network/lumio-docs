# Deploy on Move VM

Download the Aptos CLI and follow the installation instructions as described in the [section](../use-the-xlumio-testnet/cli.md).

For an optimized development experience, consider using the IntelliJ plugin developed by Pontem.

To create a new Aptos project, use your IDE. Typically, selecting the Move project type will automatically generate a new project for you.

In the project directory, run the following command:

```sh
aptos move init --name l2_coin
```

Feel free to replace `l2_coin` with any name you prefer.

You'll need the Aptos CLI. Initialize your account as described in the relevant section:

```sh
aptos init
```

When prompted for the network, choose `custom`. For the RPC and faucet, use the following URLs:

```sh
RPC endpoint: https://mvm.testnet.lumio.io/v1
Faucet: https://faucet.testnet.lumio.io
```

You can opt to use a newly generated private key or, alternatively, copy your private key from an existing account.

The `init` command will create a new account, deposit funds from the faucet, and display the address of the newly created account.

Navigate to the newly created `Move.toml` file and define the new account as follows:

```toml
[addresses]
l2_coin = "your address"
```

Replace `your address` with the address you created.

Next, create a new module in the `sources/` folder named `coin.move`:

```rust
module l2_coin::coin {
    use std::string::utf8;
    use std::signer;
    use aptos_framework::coin;

    // Coin Type.
    struct MyCoin {}

    // Initialize function.
    public entry fun initialize(account: &signer) {
        let (burn_cap, freeze_cap, mint_cap) = coin::initialize<MyCoin>(
            account,
            utf8(b"Coin Name"),
            utf8(b"SYMBOL"),
            6, // Decimals
            true, // Limited supply
        );

        coin::destroy_freeze_cap(freeze_cap);
        coin::destroy_burn_cap(burn_cap);

        // Mint 100 million coins.
        let minted_coins = coin::mint(100000000000000, &mint_cap);

        // Deposit coins into the minter's account.
        coin::register<MyCoin>(account);
        coin::deposit(signer::address_of(account), minted_coins);

        coin::destroy_mint_cap(mint_cap);
    }
}
```

This module, when deployed, will create a new coin type `MyCoin` and deposit 100 million coins into the creator's account.

Now, let's move on to publishing our module.

```sh
aptos move publish
```

You should see a status message `"vm_status": "success"`, indicating that the module was deployed correctly.

Next, let’s initiate the minting of your new coin by running the `initialize` function:

```sh
aptos move run --function-id <your address>::l2_coin::initialize
```

Make sure to replace `<your address>` with your actual address before executing the call.

Upon successful completion of this call, you will see a success status along with a transaction ID. You can verify the result in the explorer.

To confirm that your coin has been deployed, access the API and substitute the URL with your address:

```sh
aptos move run --function-id <your address>::coin::initialize
```

Search for the `<your address>::l2_coin::MyCoin` type associated with your account.

Alternatively, you can import your account into a wallet like Pontem, Petra, etc., using the private key found in the `.aptos/config.yml` directory. If your coin doesn’t automatically appear in the wallet, you can manually import it using its path:

```sh
<your address>::l2_coin::MyCoin
```
