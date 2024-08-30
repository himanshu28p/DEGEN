Degen Smart Contract
The Degen smart contract is designed to manage game assets, allowing the owner to create, transfer, and destroy assets. Users can redeem these assets for in-game items by utilizing the redeem functions provided in the contract.

Table of Contents
Contract Overview
Installation
Functions
Asset Management
Item Redemption
Usage
License
Contract Overview
The Degen smart contract allows the owner to manage assets and users to redeem these assets for in-game items. The contract maintains a balance for each user and tracks redeemed items for them.

Key Features
Asset Management: Create, transfer, and destroy assets.
Item Redemption: Redeem assets for in-game items.
Balance Tracking: Check user balances and redeemed items.
Installation
To interact with the Degen smart contract, you need to have a development environment set up for Solidity. Follow these steps:

Install Node.js and npm.
Install Truffle or Hardhat.
Install Ganache for local blockchain testing.
Deploy the contract using Truffle or Hardhat:


truffle migrate --network development
or


npx hardhat run scripts/deploy.js --network localhost
Functions
Asset Management
createAsset(address account, uint256 amount)

Creates new assets for a specific account.
Only callable by the contract owner.
transferAsset(address recipient, uint256 amount)

Transfers assets from the caller's account to the recipient.
destroyAsset(uint256 amount)

Destroys a specified amount of assets from the caller's account.
checkBalance(address account)

Returns the asset balance of a specified account.
Item Redemption
showRedeemableItems()

Returns a list of redeemable items and their corresponding costs.
redeemAsset(uint256 item, uint256 quantity)

Allows users to redeem assets for in-game items.
Validates sufficient balance and whether the item has been redeemed before.
showRedeemedItems(address account)

Returns a list of items redeemed by the specified account.
Usage
Deploy the Contract: Use a local blockchain like Ganache or a test network.
Create Assets: The owner can create assets for any account using createAsset.
Transfer Assets: Users can transfer assets to other users using transferAsset.
Redeem Items: Users can redeem their assets for items using redeemAsset.
Check Balance and Redeemed Items: Use checkBalance and showRedeemedItems to view asset balances and redeemed items.
Example
solidity

// Creating assets for a user (only owner can execute)
degen.createAsset(userAddress, 1000);

// Transferring assets to another user
degen.transferAsset(recipientAddress, 500);

// Redeeming an item
degen.redeemAsset(1, 2); // Redeems 2 of Item1

// Checking balance of a user
uint256 balance = degen.checkBalance(userAddress);

// Displaying redeemed items
string memory redeemedItems = degen.showRedeemedItems(userAddress);
