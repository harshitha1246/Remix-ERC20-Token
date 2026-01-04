# MyToken (MTK) - My First ERC-20 Token 🚀

So... I decided to build my own cryptocurrency token. Yeah, that's right. This is MyToken - an ERC-20 token I created while learning blockchain development. It's super simple but actually functional. You can transfer tokens, approve spending, and all that good stuff.

## What is this?

MyToken is basically my learning project for understanding how tokens work on Ethereum. It's a complete ERC-20 implementation - meaning it follows all the rules that make tokens work with wallets and exchanges. I built it with Solidity and tested it in Remix IDE.

## Token Info

- **Name:** MyToken
- **Symbol:** MTK  
- **Decimals:** 18 (like ETH does)
- **Total Supply:** 1,000,000 tokens
- **Built with:** Solidity 0.8.0+
- **Standard:** ERC-20

## What can it do?

✅ **Transfer tokens** - Send tokens to anyone  
✅ **Approve spending** - Let others spend your tokens  
✅ **Check balances** - See how many tokens an address has  
✅ **Track approvals** - Monitor who you've authorized to spend
✅ **Emit events** - Log all transactions so everyone can see what happened

## How to use it

If you want to use this token:

1. Go to [Remix IDE](https://remix.ethereum.org/)
2. Create a new file called `MyToken.sol`
3. Copy the contract code from the `contracts/` folder
4. Compile it (make sure you're using Solidity 0.8.0 or newer)
5. Deploy it to the JavaScript VM (it's free and simulates a blockchain)
6. Enter `1000000000000000000000000` as the initial supply (that's 1 million tokens)
7. Start playing around with it!

## Functions you can use

```
balanceOf(address) -> shows how many tokens someone has
transfer(address, amount) -> send tokens to someone
approve(address, amount) -> let someone spend your tokens
transferFrom(address, address, amount) -> transfer on behalf of someone
allowance(address, address) -> check if you're approved to spend
```

## Testing it out

I tested:
- ✓ Initial balance (should show 1 million tokens)
- ✓ Transfers between accounts
- ✓ Checking balances after transfers
- ✓ Approving and transferring from another account
- ✓ Events being emitted when transfers happen

All of it works. No bugs. Pretty solid for a first try honestly.

## The code

If you want to see how it actually works, check out `contracts/MyToken.sol`. I put comments in there explaining what each function does. It's not too complicated - mostly just managing mappings (like dictionaries) to track balances and approvals.

## What I learned

Building this token taught me:
- How ERC-20 works (it's actually pretty logical once you get it)
- Why events are important (they let everyone see what happened)
- Input validation matters (gotta check for zero addresses and stuff)
- Decimals are weird but necessary (18 is the standard for a reason)

## Deployment

You can deploy this to:
- **Remix VM** (local, free, good for testing)
- **Ethereum testnet** (goerli, sepolia, etc - costs fake ETH)
- **Ethereum mainnet** (real ETH, real money, be careful!)

I tested it on the Remix VM and it works perfectly.

## Notes

- This is a learning project, not production code
- It's missing some features like minting/burning (destroying tokens)
- But it does have all the core ERC-20 stuff
- The code is pretty straightforward, no fancy patterns

---

Built for the Partnr Network Global Placement Program. Feel free to use this as a reference or starting point for your own token projects!
