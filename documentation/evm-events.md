# Understanding EVM Events

## What Are Events?

Events in Ethereum are a way for smart contracts to communicate that something happened on the blockchain to your frontend application or other listening services. Think of them as the smart contract's way of logging important information.

## Why Use Events?

1. **Off-chain Notification**: They allow dApps (decentralized applications) to "listen" for specific happenings in the contract
2. **Gas Efficiency**: Storing data in events is much cheaper than storing in contract variables
3. **History**: Events create a permanent record on the blockchain that can be queried later

## Event Structure

```solidity
event Transfer(address indexed from, address indexed to, uint256 amount);
```

In this example:

- `Transfer` is the event name
- `from`, `to`, and `amount` are parameters that get logged
- `indexed` keyword marks parameters that can be filtered when searching for events

## Indexed vs Non-indexed Parameters

- **Indexed parameters** (max 3 per event):

  - Stored as "topics" in the event log
  - Can be efficiently searched and filtered
  - Good for addresses and identifiers

- **Non-indexed parameters**:
  - Stored in the data part of the log
  - Cannot be directly searched
  - Better for larger data like strings or arrays

## Emitting Events

To trigger an event, use the `emit` keyword:

```solidity
function transfer(address to, uint256 amount) public {
    // Transfer logic...

    emit Transfer(msg.sender, to, amount);
}
```

## Best Practices

1. **Naming**: Use past tense verbs (e.g., `Transferred`, `Deposited`)
2. **Indexing**: Index parameters you'll want to search by (usually addresses)
3. **Documentation**: Comment what each event represents
4. **When to emit**: Emit events after state changes are complete

## Real-world Uses

1. **NFT Transfers**: Track who bought which NFT
2. **Token Transactions**: Record token movements between wallets
3. **Governance**: Log voting results
4. **DeFi**: Record swaps, loans, and other financial activities

## Listening for Events in JavaScript (Web3/Ethers)

```javascript
// Example with ethers.js
contract.on("Transfer", (from, to, amount) => {
  console.log(`${amount} tokens transferred from ${from} to ${to}`);
});
```

## Cost Considerations

Events are one of the most gas-efficient ways to store data on the blockchain. They cost approximately:

- 375 gas for the event itself
- 375 gas for each indexed parameter
- 8 gas for each byte of non-indexed data

## Conclusion

Events are a crucial bridge between your smart contract and the outside world. They provide an efficient way to keep track of contract activity and allow off-chain applications to react to on-chain changes.
