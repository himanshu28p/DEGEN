Degen Smart Contract
Overview
The Degen smart contract allows the creation, transfer, and destruction of a virtual asset called GameAsset (GA). Users can also redeem assets for items and track their redeemed items.

Features
Create Asset: Mint new assets to a specified account.
Transfer Asset: Transfer assets between accounts.
Destroy Asset: Burn assets from the sender's account.
Show Redeemable Items: Display a list of items available for redemption.
Redeem Asset: Redeem assets for specific items.
Check Balance: Check the balance of assets for a given account.
Show Redeemed Items: View a list of items redeemed by an account.
Getting Started
Prerequisites
Solidity ^0.8.0
Deployment
Deploy the Degen contract using Remix or any other Solidity-compatible IDE.

Usage
Create Asset: Only the owner can create assets.


createAsset(address account, uint256 amount)
Transfer Asset: Transfer assets to another account.

transferAsset(address recipient, uint256 amount)
Destroy Asset: Burn assets from your account.


destroyAsset(uint256 amount)
Show Redeemable Items: View available items for redemption.


showRedeemableItems()
Redeem Asset: Redeem assets for an item.


redeemAsset(uint256 item, uint256 quantity)
Check Balance: Check your asset balance.

checkBalance(address account)
Show Redeemed Items: View items you have redeemed.


showRedeemedItems(address account)
