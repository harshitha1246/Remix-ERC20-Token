# MyToken (MTK)

A simple ERC-20 compatible token built on Ethereum for learning blockchain development. This project demonstrates the fundamentals of smart contracts and token standards.

## Overview

MyToken is an educational ERC-20 token implementation that showcases how cryptocurrency tokens work on the Ethereum blockchain. It provides a complete implementation of the ERC-20 standard with proper event emission, input validation, and gas-efficient operations.

## Token Details

- **Name**: MyToken
- **Symbol**: MTK
- **Decimals**: 18
- **Total Supply**: 1,000,000 MTK (1,000,000,000,000,000,000,000,000 wei)
- **Solidity Version**: ^0.8.0
- **Standard**: ERC-20

## Features

✅ **Complete ERC-20 Implementation**
- Implements all required ERC-20 functions and events
- Full compliance with the Ethereum token standard

✅ **Transfer Functionality**
- Users can transfer tokens to other addresses
- Automatic balance updates and event emission

✅ **Approve and TransferFrom**
- Token owners can approve other addresses to spend tokens on their behalf
- Third parties can transfer tokens using the approved allowance
- Essential for decentralized exchanges and smart contract interactions

✅ **Event Emission**
- Transfer events for all token movements
- Approval events for allowance changes
- Enables off-chain tracking and wallet integration

✅ **Balance Tracking**
- Maintains accurate balance records for all addresses
- Public mapping for transparent balance queries

✅ **Input Validation**
- Zero address protection prevents accidental token burning
- Balance verification before transfers
- Allowance verification for delegated transfers
- Clear error messages for failed transactions

✅ **Clean, Well-Documented Code**
- Comprehensive inline comments
- Clear variable and function naming
- Follows Solidity best practices and conventions

## How to Deploy

### Using Remix IDE (Recommended for Learning)

1. **Open Remix IDE**
   - Visit https://remix.ethereum.org/
   - No installation required, works directly in your browser

2. **Create the Contract File**
   - Click the new file icon in the File Explorer
   - Name it `MyToken.sol`
   - Copy the complete contract code from this repository

3. **Compile the Contract**
   - Navigate to the Solidity Compiler tab (left sidebar)
   - Select compiler version `0.8.x` or higher
   - Click "Compile MyToken.sol"
   - Verify no errors appear in the compilation output

4. **Deploy the Contract**
   - Go to the "Deploy & Run Transactions" tab
   - Select "JavaScript VM" as the environment (simulates blockchain locally)
   - Enter the initial supply in the constructor
     - Example: `1000000000000000000000000` for 1 million tokens with 18 decimals
   - Click "Deploy"
   - The contract address will appear in the Deployed Contracts section

5. **Interact with Your Token**
   - Use the contract interface to call functions
   - Check balances, transfer tokens, and test approvals
   - View emitted events in the transaction logs

### Using Command Line (for Development)

```bash
# Clone the repository
git clone https://github.com/harshitha1246/Remix-ERC20-Token.git
cd Remix-ERC20-Token

# Install dependencies (if using Hardhat or Truffle)
npm install

# Compile
npx hardhat compile

# Deploy
npx hardhat run scripts/deploy.js --network localhost
```

## How to Use

### Check Balance

```solidity
// Returns the token balance of an address
balanceOf(address owner) → returns uint256

// Example in Remix:
// Call: balanceOf(0x5B38Da6a701c568545dCfcB03FcB875f56beddC4)
// Returns: 1000000000000000000000000
```

### Transfer Tokens

```solidity
// Transfer tokens from caller to another address
transfer(address to, uint256 amount) → returns bool

// Example in Remix:
// To: 0xAb8483F64d9C6d1ecF9b849Ae677dD3315835cb2
// Amount: 1000000000000000000 (1 token)
```

### Approve Spending

```solidity
// Approve another address to spend tokens on your behalf
approve(address spender, uint256 amount) → returns bool

// Example in Remix:
// Spender: 0xAb8483F64d9C6d1ecF9b849Ae677dD3315835cb2
// Amount: 500000000000000000 (0.5 tokens)
```

### Transfer on Behalf (TransferFrom)

```solidity
// Transfer tokens from one address to another using the spender's allowance
transferFrom(address from, address to, uint256 amount) → returns bool

// Example in Remix:
// From: 0x5B38Da6a701c568545dCfcB03FcB875f56beddC4
// To: 0x1aE0EA34a72D944a8C7603FfB3eC30a6669E454C
// Amount: 250000000000000000 (0.25 tokens)
```

### Get Token Information

```solidity
// Get all token information in one call
getTokenInfo() → returns (name, symbol, decimals, totalSupply)

// Get total supply
getTotalSupply() → returns uint256

// Access individual metadata
name → "MyToken"
symbol → "MTK"
decimals → 18
totalSupply → 1000000000000000000000000
```

## Testing Scenarios

### Basic Transfer Test

1. Deploy the contract with 1,000,000 token supply
2. Check initial balance (should be 1,000,000 tokens)
3. Transfer 100 tokens to Account B
4. Verify Account A balance decreased by 100
5. Verify Account B balance increased by 100
6. Confirm Transfer event was emitted

### Approve and TransferFrom Test

1. Account A approves Account B to spend 500 tokens
2. Check allowance (should be 500)
3. Switch to Account B
4. Account B transfers 300 tokens from A to C using transferFrom
5. Verify A's balance decreased by 300
6. Verify C's balance increased by 300
7. Verify A's allowance decreased to 200
8. Confirm Transfer event was emitted

### Edge Case Testing

1. **Zero Address Transfer**: Try transferring to address(0) - should fail with "Cannot transfer to zero address"
2. **Insufficient Balance**: Try transferring more tokens than you have - should fail with "Insufficient balance"
3. **Insufficient Allowance**: Try using transferFrom without proper approval - should fail with "Insufficient allowance"
4. **Zero Address Approval**: Try approving address(0) - should fail with "Cannot approve zero address"

## Common Mistakes to Avoid

⚠️ **Forgetting to Emit Events**: Always emit Transfer and Approval events after state changes - this is required by the ERC-20 standard and enables wallet integration.

⚠️ **Not Validating Zero Address**: Always check that recipient addresses are not `address(0)` to prevent accidentally burning tokens.

⚠️ **Insufficient Input Validation**: Always verify sender has sufficient balance before transferring and that spenders have sufficient allowance.

⚠️ **Forgetting to Decrease Allowance**: In transferFrom, remember to reduce the allowance after transfer to prevent unlimited spending.

⚠️ **Incorrect Decimal Values**: Using wrong decimals value can make your token incompatible with wallets (18 is the standard, matching ETH).

⚠️ **Integer Overflow (in older Solidity)**: With Solidity 0.8.x, overflow protection is built-in, but be aware of this in older versions.

## What You'll Learn

By studying and working with this project, you'll gain understanding of:

📚 **Smart Contract Development**
- Writing Solidity smart contracts
- Understanding contract structure and functions
- State variables and their management
- Events and logging

📚 **ERC-20 Token Standard**
- What ERC-20 means and why it's important
- The required functions and events
- How tokens are tracked and transferred
- The approve/transferFrom pattern for delegated transfers

📚 **Blockchain Concepts**
- How tokens differ from coins
- Address management and accounts
- State changes and transactions
- Event emission for transparency

📚 **Security Considerations**
- Input validation and error handling
- Preventing common vulnerabilities
- Best practices for safe smart contracts

📚 **Ethereum Ecosystem**
- Using Remix IDE for development and testing
- Deploying to local blockchain (JavaScript VM)
- Interacting with deployed contracts
- Understanding gas and transaction costs

## Technical Details

### State Variables

```solidity
string public name = "MyToken"              // Token name
string public symbol = "MTK"                 // Token symbol  
uint8 public decimals = 18                  // Number of decimal places
uint256 public totalSupply                  // Total tokens in circulation
mapping(address => uint256) public balanceOf    // Address to balance mapping
mapping(address => mapping(address => uint256)) public allowance  // Allowances for delegated transfers
```

### Functions

**Core ERC-20 Functions:**
- `transfer(address, uint256)` - Direct token transfer
- `approve(address, uint256)` - Approve token spending
- `transferFrom(address, address, uint256)` - Transfer on behalf
- `balanceOf(address)` - Query token balance
- `allowance(address, address)` - Query spending approval

**Helper Functions:**
- `getTotalSupply()` - Get total supply
- `getTokenInfo()` - Get all metadata at once

### Events

```solidity
event Transfer(address indexed from, address indexed to, uint256 value)
event Approval(address indexed owner, address indexed spender, uint256 value)
```

## Frequently Asked Questions

**Q: What does ERC-20 mean?**
A: ERC-20 is a token standard on Ethereum that defines a common interface for token contracts. It stands for "Ethereum Request for Comments - 20" and ensures tokens work consistently across wallets and exchanges.

**Q: Why do we use 18 decimals?**
A: 18 decimals is the Ethereum standard (same as ETH). This allows tokens to represent fractional amounts with high precision while staying compatible with wallets and exchanges.

**Q: What's the difference between transfer and transferFrom?**
A: `transfer()` moves tokens from your own balance, while `transferFrom()` moves tokens from another address (that has approved you) to a third address. This is essential for decentralized exchanges and automated interactions.

**Q: Can I change the total supply after deployment?**
A: In this basic implementation, no. The total supply is set at deployment. More advanced tokens add mint/burn functions to modify supply.

**Q: Do I need real ETH to deploy this?**
A: No! For learning, use Remix's JavaScript VM which simulates a blockchain locally. For testnets or mainnet, you need ETH to pay for gas.

**Q: Is this production-ready?**
A: This is a learning implementation. Production tokens often add features like ownership controls, upgradeable contracts, and enhanced security audits.

**Q: How do I track my token on block explorers?**
A: If deployed to a testnet (like Goerli), you can view your token on block explorers like Etherscan by entering your contract address.

## Resources for Further Learning

- [ERC-20 Token Standard](https://ethereum.org/en/developers/docs/standards/tokens/erc-20/)
- [Solidity Documentation](https://docs.soliditylang.org/)
- [Remix IDE Documentation](https://remix-ide.readthedocs.io/)
- [OpenZeppelin Token Contracts](https://docs.openzeppelin.com/contracts/4.x/tokens/)
- [Ethereum Development Documentation](https://ethereum.org/en/developers/)

## License

This project is open source and available under the MIT License. Feel free to use it for learning, teaching, or as a base for your own projects.

## Author

Created as an educational project to demonstrate ERC-20 token development on Ethereum.

---

**Happy Learning! 🚀**

This is your first step into blockchain development. Use this token as a foundation to explore more advanced concepts like token economics, governance, and DeFi protocols.
