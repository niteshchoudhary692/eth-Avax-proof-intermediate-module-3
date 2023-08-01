MyToken Smart Contract

This repository contains the Solidity smart contract named MyToken, which implements a basic token with minting, transfer, burning capabilities, and account restriction functionality. The contract is designed to be deployed on the Ethereum blockchain and allows users to interact with the token using standard Ethereum wallets and interfaces.

Contract Description

The MyToken contract includes the following features:

Token Properties:

string public name: The name of the token (e.g., "MyToken").
string public symbol: The token symbol (e.g., "MTK").
uint8 public decimals: The decimal precision of the token (e.g., 18 for 18 decimal places).
uint256 public totalSupply: The total supply of tokens in circulation.
address public owner: The address of the contract owner with special privileges.

Balances and Ownership:

mapping(address => uint256) public balances: A mapping that stores the token balances of each address.
mapping(address => bool) public restrictedAccounts: A mapping that indicates whether an account is restricted from certain actions.
Events:

event Transfer(address indexed from, address indexed to, uint256 amount): An event emitted when tokens are transferred from one address to another.
event OwnershipTransferred(address indexed previousOwner, address indexed newOwner): An event emitted when ownership of the contract is transferred.
event AccountRestricted(address indexed account): An event emitted when an account is restricted from performing certain actions.
event AccountUnrestricted(address indexed account): An event emitted when an account's restrictions are lifted.
Constructor Function:

The constructor initializes the contract with the provided token name, symbol, decimal units, and initial supply. The contract deployer becomes the contract owner and receives the entire initial supply.

Token Minting - mint Function:

The mint function allows the contract owner to create new tokens and assign them to a specified address.
It takes two parameters: to (recipient address) and amount (the number of tokens to mint).
The function performs several checks, such as ensuring the recipient address is not zero and the amount is greater than zero.
After validation, it increases the total token supply and adds the minted amount to the recipient's balance.
The function emits the Transfer event to indicate the token transfer from address 0 to the recipient.

Token Transfer - transfer Function:

The transfer function allows any user to transfer their tokens to another address.
It takes two parameters: to (recipient address) and amount (the number of tokens to transfer).
The function checks if the recipient address is valid, the amount is greater than zero, and the sender has sufficient balance.
If all conditions are met, the function deducts the transferred amount from the sender's balance and increases the recipient's balance.
The function emits the Transfer event to indicate the token transfer from the sender to the recipient.

Token Burning - burn Function:

The burn function allows any user to burn (destroy) a specified amount of their tokens.
It takes the amount to burn as a parameter and performs similar checks to ensure the amount is valid and the user has sufficient balance.
After verification, the function reduces the total token supply and subtracts the burned amount from the sender's balance.
The function emits the Transfer event to indicate the token transfer from the sender to address 0 (burned).

Ownership Transfer - transferOwnership Function:

The transferOwnership function lets the current contract owner transfer ownership to a new address.
It takes the newOwner address as a parameter.
The function verifies that the new owner's address is not zero and then proceeds to transfer ownership to the new address.
The function emits the OwnershipTransferred event to indicate the change in ownership.

Account Restriction - restrictAccount and unrestrictAccount Functions:

The restrictAccount function allows the contract owner to restrict a specific address from performing token transfers and burning tokens.
It takes the account address as a parameter and sets its restrictedAccounts status to true.
The unrestrictAccount function allows the contract owner to remove the restriction from a previously restricted address by setting its restrictedAccounts status to false.
Both functions emit the AccountRestricted and AccountUnrestricted events, respectively, to indicate the account's restriction status.

Error Handling Mechanisms

The contract demonstrates error handling using the following statements:

require: Used to validate certain conditions before executing a function. If the condition evaluates to false, the transaction will revert with a specific error message. It is commonly used for access control, input validation, and other checks within functions.
assert: Utilized to check for internal errors and ensure certain conditions are always true. If the condition evaluates to false, it indicates a critical bug in the contract, causing the transaction to revert with no specific error message.
revert: Used to provide custom error messages and revert the transaction based on certain conditions. It is often used in pure functions to signal expected conditions without indicating a bug in the contract.

Usage

Clone the repository and navigate to the project directory.
Make sure you have a compatible Solidity compiler installed (e.g., version 0.8.0 or higher).
Use your preferred Solidity development tool to deploy and interact with the smart contract.

Disclaimer

This repository is intended for educational purposes only. The error handling mechanisms demonstrated in the contract may not be suitable for all real-world scenarios. For production use, additional considerations and best practices must be followed to ensure robustness and security.
