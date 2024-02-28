# Deploy on EVM (Foundry)

Foundry is an exceptionally fast, portable, and modular toolkit designed for Ethereum application development, and it's written in Rust – a choice we highly appreciate!

Requirements:

* [Rust](https://www.rust-lang.org/tools/install)

If Rust is not already installed on your local system, simply follow the provided link to get started. Now, let's proceed with installing Foundry:

```sh
curl -L https://foundry.paradigm.xyz | bash
```

Start by establishing a new project folder on your system. After this folder is set up, proceed to initialize it with Forge:

```
forge init
```

The command will populate the directory with various files, including an example contract, deployment scripts, and tests.

We will need OpenZeppelin for our ERC20 development:

```
forge install OpenZeppelin/openzeppelin-contracts
```

Finally, let's create the contract. Add a new file into the `src/` directory and name it `Token.sol`. Use the following code for this file:

```solidity
//SPDX-License-Identifier: Unlicense
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract Token is ERC20 {
    uint constant _initial_supply = 100000000 * (10**18);
    constructor() ERC20("MyToken", "TOKEN") {
        _mint(msg.sender, _initial_supply);
    }
}

```

Now, let's proceed with building the project:

```
forge build
```

The command mentioned above will download the Solc compiler and build the contracts.

To deploy our Token, let's create a new file named `Token.s.sol` in the `script/` directory. Then, insert the following code into this file:

```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.20;

import {Token} from "../src/Token.sol";
import {Script, console2} from "forge-std/Script.sol";

contract TokenScript is Script {
    function run() public {
        vm.startBroadcast();

        Token token = new Token();

        console2.log("Token deployed at: ", address(token));

        vm.stopBroadcast();
    }
}

```

We're almost there. Now, we need to execute a script to deploy everything:

{% code overflow="wrap" %}
```
forge script script/Token.s.sol --private-key=<PRIVATE_KEY> --rpc-url https://testnet.lumio.io --broadcast
```
{% endcode %}

Remember to replace the placeholder for the private key with your actual private key.

Upon successful deployment, you will receive a message confirming that the contract has been deployed successfully. To simulate the execution before broadcasting the transaction, simply remove the `--broadcast` flag from the command above.

You will see the following message:

```
Token deployed at:  <ADDRESS>
```

Copy the address and go to [block explorer](../xlumio-block-explorer.md), that's all! Now you can continue develop your contract/project on the EVM part of the L2.
