Dice Rolling Module

 Overview

This module provides functionality for rolling dice and keeping track of the roll history on the Aptos blockchain. It includes different versions of dice rolling functions, demonstrating the use of randomness and state management.

 Modules and Functions

DiceRollHistory

This is a key-structured data type used to keep track of dice rolls.

- Fields:
  - rolls: A vector of u64 values representing the history of dice rolls.

 Functions

rolling_v0

```rust
public entry fun rolling_v0(_account: signer)
```

- Description:** Generates a random number between 0 and 6 (exclusive). This function does not modify or access any state and is only a demonstration of randomness usage.
- Linting:** Unsafe randomness is allowed in this function.
  
 roll

```rust
entry fun roll(account: signer) acquires DiceRollHistory
```

- Description: Rolls a dice and updates the history of rolls for the given account. If `DiceRollHistory` does not exist for the account, it is initialized. The roll result is appended to the `rolls` vector.
- State Management: This function acquires and manages the state of DiceRollHistory for the account.

 roll_v2

```rust
entry fun roll_v2(_account: signer) #[randomness(max_gas=56789)]
```

- Description: Generates a random number between 0 and 6 (exclusive). This function demonstrates the usage of randomness with a specified gas limit. It does not modify or access any state.

Usage

1. Initialize the Module:
   Deploy this module to the Aptos blockchain.

2. Rolling Dice:
   - To roll a dice and update the roll history for an account, use the roll function. 
     ```rust
     module_owner::dice::roll(account);
     ```
   - For demonstration or testing purposes, you can use rolling_v0 or roll_v2 to generate random dice rolls without modifying state.
     ```rust
     module_owner::dice::rolling_v0(account);
     module_owner::dice::roll_v2(account);
     ```

   Check Roll History:
   Use Aptos query functions to check the state of DiceRollHistory for an account to view the roll history.

Notes

- Randomness: 
  - The rolling_v0 and roll_v2 functions are primarily for demonstration. The roll function is intended for actual dice rolling and state management.
  - roll_v2 includes a specific gas limit for randomness operations, which can help manage transaction costs.

- State Management: 
  - The roll function acquires and manages the state of DiceRollHistory. Ensure that your transaction includes appropriate permissions for state acquisition and modification.

License

This module is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

Feel free to modify this README as needed to fit additional requirements or details specific to your project!
