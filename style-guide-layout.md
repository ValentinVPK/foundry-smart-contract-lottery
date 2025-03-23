# Solidity Contract Layout Style Guide

The following is the recommended layout order for Solidity smart contracts:

## Contract Layout

1. **Pragma Statements**

   - Solidity version pragma
   - Experimental pragma statements

2. **Import Statements**

   - All imports in alphabetical order

3. **Interface, Library, and Contract Definitions**
   - Interfaces
   - Libraries
   - Contracts

## Within Contract/Library/Interface

1. **Type Declarations**

   - Structs
   - Enums
   - Custom types/typedefs

2. **State Variables**

   - Constants
   - Immutable variables
   - Regular state variables

3. **Events**

4. **Errors**

5. **Modifiers**

6. **Functions** (grouped by visibility and mutability)
   - Constructor
   - Receive function (if exists)
   - Fallback function (if exists)
   - External functions
   - Public functions
   - Internal functions
   - Private functions
   - View & Pure functions

## Function Layout

1. **Function Declaration**
2. **Modifiers**
3. **Visibility**
4. **Mutability**
5. **Virtual, Override, etc.**
6. **Returns**

## Example

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.19;

import "./Interface.sol";
import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

contract ExampleContract is SomeInterface {
    // Type declarations
    struct User {
        uint256 balance;
        bool isActive;
    }

    enum Status { Pending, Active, Inactive }

    // State variables
    uint256 public constant MAX_USERS = 1000;
    address public immutable i_owner;
    mapping(address => User) private s_users;

    // Events
    event UserAdded(address indexed user, uint256 initialBalance);
    event UserRemoved(address indexed user);

    // Errors
    error NotAuthorized();
    error InvalidAmount();

    // Modifiers
    modifier onlyOwner() {
        if (msg.sender != i_owner) revert NotAuthorized();
        _;
    }

    // Functions by visibility and mutability
    constructor(address owner) {
        i_owner = owner;
    }

    receive() external payable {}

    fallback() external payable {}

    function externalFunction() external {
        // Implementation
    }

    function publicFunction() public {
        // Implementation
    }

    function internalFunction() internal {
        // Implementation
    }

    function privateFunction() private {
        // Implementation
    }

    function viewFunction() public view returns (uint256) {
        // Implementation
    }

    function pureFunction(uint256 a, uint256 b) public pure returns (uint256) {
        return a + b;
    }
}
```
