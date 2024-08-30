Degen Smart Contract
The Degen smart contract is a Solidity-based contract designed for managing game assets within a blockchain environment. It allows the contract owner to create assets, and users can transfer, destroy, and redeem these assets for in-game items.

Table of Contents
Introduction
Prerequisites
Installation
Contract Details
State Variables
Modifiers
Functions
Asset Management
Item Redemption
Utility Functions
Usage
Deploying the Contract
Interacting with the Contract
Examples
License
Introduction
The Degen smart contract facilitates the creation, transfer, and destruction of game assets, as well as the redemption of these assets for specific in-game items. The contract keeps track of each user's balance and their redeemed items, ensuring that assets are managed securely and efficiently.

Prerequisites
To deploy and interact with the Degen smart contract, ensure you have the following installed:

Node.js and npm
Truffle or Hardhat for development and deployment
Ganache for local blockchain testing
A code editor like Visual Studio Code
Installation
Clone the repository to your local machine:


git clone https://github.com/yourusername/DegenContract.git
cd DegenContract
Install the necessary dependencies:


npm install
Compile the contract using Truffle or Hardhat:


truffle compile
or


npx hardhat compile
Deploy the contract to a local blockchain:


truffle migrate --network development
or

npx hardhat run scripts/deploy.js --network localhost
Contract Details
State Variables
string public assetName: The name of the asset.
string public assetSymbol: The symbol of the asset.
address public assetOwner: The owner of the asset.
mapping(address => bool) private hasItemX: Tracks if an item has been redeemed by an address (where X is the item number).
mapping(address => uint256[4]) private redeemedItems: Keeps track of the quantity of redeemed items for each address.
mapping(address => uint256) private balances: Stores the balance of assets for each address.
Modifiers
onlyOwner: Restricts function access to only the asset owner.
Functions
Asset Management
createAsset(address account, uint256 amount)
Creates a specified amount of assets for a given account.
Only callable by the contract owner.

transferAsset(address recipient, uint256 amount)
Transfers a specified amount of assets from the sender's account to the recipient's account.

destroyAsset(uint256 amount)
Destroys a specified amount of assets from the sender's account.

checkBalance(address account) public view returns (uint256)
Returns the balance of the specified account.

Item Redemption
showRedeemableItems() public pure returns (string memory)
Returns a string listing all redeemable items and their corresponding costs.

redeemAsset(uint256 item, uint256 quantity) public
Allows a user to redeem a specific item in a given quantity. Checks for sufficient balance and redemption status.

Utility Functions
showRedeemedItems(address account) public view returns (string memory)
Returns a formatted string of all items redeemed by a specified account.

toString(uint256 value) private pure returns (string memory)
Converts a uint256 to a string representation.

Usage
Deploying the Contract
Deploy the contract to your desired network (local or testnet):


truffle migrate --network development
or


npx hardhat run scripts/deploy.js --network localhost
Note the deployed contract address for interacting with it.

Interacting with the Contract
You can interact with the Degen contract using a web interface (e.g., a dApp) or directly through a console like Truffle or Hardhat.

Examples
Creating Assets for a User (Owner Only)

degen.createAsset(userAddress, 1000);
This function call creates 1000 assets for userAddress. Only the owner can call this function.

Transferring Assets to Another User


degen.transferAsset(recipientAddress, 500);
This transfers 500 assets from the sender's account to recipientAddress.

Redeeming an Item


degen.redeemAsset(1, 2);
Redeems 2 units of Item1 for the caller's account.

Checking Balance of a User


uint256 balance = degen.checkBalance(userAddress);
This returns the balance of assets for userAddress.

Displaying Redeemed Items

string memory redeemedItems = degen.showRedeemedItems(userAddress);
This returns a string with all redeemed items for userAddress.
