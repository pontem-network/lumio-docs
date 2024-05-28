# Deploy on SVM

### Config

* Solana CLI required.

Configure RPC URL:

```bash
solana config set --url [<https://svm.devnet.lumio.io>](<https://svm.devnet.lumio.io/>)
```

If you need a new key:

```bash
solana-keygen new -o ./keypair.json
```

### Faucet

Get some SOL:

```bash
solana airdrop 1
```

## Create Token

```bash
# Install 
cargo install spl-token-cli

# Create token
spl-token create-token
```

After you got token address:

```bash
# Check supply
spl-token supply <address>

# Create an account to hold balance
spl-token create-account <address>

# Check balance
spl-token balance <address>

# Mint some
spl-token mint <address> <amount>

# Check supply again
spl-token supply <address>
```

## Create a program

Be sure CLI is configured and account funded.

Create a new project:

```bash
cargo init hello_world --lib
cd hello_world
```

Add deps:

```bash
cargo add solana-program
```

Open `Cargo.toml` and add the following:

```toml
[lib]
name = "hello_world"
crate-type = ["cdylib", "lib"]
```

Replace src/lib.rs with the following code:

```rust
use solana_program::{
    account_info::AccountInfo,
    entrypoint,
    entrypoint::ProgramResult,
    pubkey::Pubkey,
    msg,
};

// declare and export the program's entrypoint
entrypoint!(process_instruction);
 
// program entrypoint's implementation
pub fn process_instruction(
    program_id: &Pubkey,
    accounts: &[AccountInfo],
    instruction_data: &[u8]
) -> ProgramResult {
    // log a message to the blockchain
    msg!("Hello, world!");
 
    // gracefully exit the program
    Ok(())
}

```

Build:

```bash
cargo build-bpf
```

Deploy:

```bash
solana program deploy ./target/deploy/hello_world.so
```
