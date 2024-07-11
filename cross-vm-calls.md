# Cross VM Calls

Each VM operates independently, and messaging between them is facilitated by the sequencer. At a high level, each VM has its own contract, which serves a similar function. These contracts emit an "event" containing the call data and the sender's information, which is then executed on the target VM.

For Solana VM, a program is deployed; for Move VM, a module is included in the standard framework; and for EVM, a smart contract is used. All are deployed on the chain. Essentially, a developer only needs to query a specific function to send a message to another virtual machine, similar to how it's done in LayerZero, but within the same execution environment.

Example of a loan/trade from EVM to Move VM:

1. Loan USDC for ETH on AAVE.
2. Transfer USDC to Move VM.
3. Sell USDC for ETH on Liquidswap.
4. Return ETH to close the loan.

<figure><img src=".gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

If we simplify the logic, it can be represented as follows:

<figure><img src=".gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

Calls can essentially follow the same path back, allowing for the transfer of results or assets back to the initial contract.

Let's delve deeper into the implementation of cross-VM calls between Move VM and EVM:

1. **Move VM Implementation**:
   1. Implemented as a native function to streamline the serialization process.
   2. As part of default framework.
   3. Data is passed as objects, and serialization/deserialization is managed.

At a high level, both contracts, implemented on each VM, serve a similar purpose. They emit an "event" containing the call data and the sender's information, which is then executed on the target VM.

```java
/// EVM Communication Module
/// This module enables the execution of smart contracts within the EVM-compatible layer of the Layer 2 (L2) infrastructure.
/// Designed as a key component of our L2 solution, this module facilitates seamless interaction with the EVM ecosystem.
/// It acts as a bridge, allowing users and other smart contracts to initiate and execute smart contract functions
/// that reside on the EVM side of the L2 platform. This integration ensures compatibility and extends
/// the functionality of L2 solutions within the diverse Ethereum ecosystem.
module framework::evm {
    /// Facilitates the execution of a function in an EVM contract from within the current VM environment.
    /// This native function signals the VM to initiate a call to a specified contract in the EVM layer.
    /// It's an integral part of cross-VM communication, enabling interoperability between different blockchain protocols.
    ///
    ///  * `account`: The sender's account, which will be used for authorization and executing the call on the EVM side.
    ///  * `to`: The target EVM contract's address to which the call is directed.
    ///  * `fn_abi`: The ABI signature of the function to be called in the EVM contract, for example, `transfer(address,u256)`.
    ///  * `calldata`: The arguments to be passed to the function. This can be a single primitive type or multiple parameters packed in an object.
    native fun evm<T>(account: &signer, to: address, fn_abi: vector<u8>, calldata: &T);
}
```

2. **EVM implementation**

In the EVM part of the genesis block and deployed on the address, similar functionalities are achieved, but with a focus on utilizing events for efficient cross-VM communication.

```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.13;

import {IMoveVM} from "src/interfaces/IMoveVM.sol";

/// @title MoveVM
/// @notice This contract implements the cross-VM messaging protocol within the Ethereum Virtual Machine (EVM) environment.
contract MoveVM is IMoveVM {
    /// @notice Executes a call to a specified virtual machine (Move VM), targeting a specific module and function.
    ///         The `msg.sender` is used as the initiator of the call.
    ///         Emits a communication event to facilitate interaction between EVM and MoveVM.
    /// @dev This function facilitates interaction between Solidity contracts and modules deployed in a Move VM.
    ///      It encodes the call data for compatibility with Move VM standards and handles the complexities
    ///      of cross-VM communications.
    /// @param _moduleAddress The hexadecimal address of the module in the Move VM to which the call is directed.
    ///                       Example: `0x1` for a core module in Move VM.
    /// @param _moduleId The identifier of the module within the Move VM. For instance, `coin` for a module handling
    ///                  cryptocurrency operations.
    /// @param _functionId The identifier of the function within the specified module to be called, e.g. `transfer`.
    /// @param _callData ABI-encoded data to be passed to the function. This data should be formatted according
    ///                  to the requirements of the target function and should only include supported primitive types.
    /// @param _generics A list of fully qualified paths of any generics involved in the function call.
    ///                  Use the format `module_path::module_name::GenericType` for single generics.
    ///                  For multiple generics, separate them with commas and detail nested generics where necessary.
    function call(
        bytes calldata _moduleAddress,
        bytes calldata _moduleId,
        bytes calldata _functionId,
        bytes calldata _callData,
        bytes calldata _generics
    ) external {
        emit Call(msg.sender, _moduleAddress, _moduleId, _functionId, _callData, _generics);
    }
}
```

## Concurrency Note

Multiple calls can be queued sequentially; however, execution on the target VM commences only after the current runtime completes. This process isn't fully synchronous, but enhancing this aspect is a priority for future updates. Calls are executed in a sequencer, one after another, following the order in which they were initiated.
