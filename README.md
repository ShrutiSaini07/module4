# DegenToken

DegenToken is a simple ERC20 token contract implemented in Solidity. It allows users to create, transfer, and burn tokens.

## Getting Started

To get started with DegenToken, follow these steps:

### Prerequisites

- Install an Ethereum development environment or use an online development platform like Remix.

### Deployment

1. Deploy the DegenToken contract on an Ethereum network of your choice.
2. Once deployed, the contract will have a name "Degen Token," a symbol "DEGEN," and 18 decimal places.
3. The contract owner will receive an initial supply of 1,000,000 tokens.

## Functionality

The DegenToken contract provides the following functions:

- `mint(address to, uint256 amount)`: Allows the contract owner to mint new tokens and assign them to the specified address.
- `transfer(address to, uint256 value)`: Allows a token holder to transfer tokens to another address.
- `approve(address spender, uint256 value)`: Approves a specific amount of tokens to be spent by a designated address.
- `transferFrom(address from, address to, uint256 value)`: Allows a designated spender to transfer tokens on behalf of the token holder.
- `burn(uint256 value)`: Allows a token holder to burn a specific amount of their own tokens.

Please refer to the contract code for detailed information on the implementation of these functions.

## Example Usage

Here's an example of how you can interact with the DegenToken contract using JavaScript and the Web3 library:

```javascript
// Import Web3 library and create an instance
const Web3 = require('web3');
const web3 = new Web3('https://<ethereum-network-url>');

// Set the contract address and ABI
const contractAddress = '<DegenToken-contract-address>';
const contractABI = <DegenToken-contract-ABI>;

// Create a contract instance
const contract = new web3.eth.Contract(contractABI, contractAddress);

// Example: Mint tokens
const mintTokens = async (to, amount) => {
  try {
    const accounts = await web3.eth.getAccounts();
    const owner = accounts[0];

    const result = await contract.methods.mint(to, amount).send({ from: owner });
    console.log('Tokens minted:', result.transactionHash);
  } catch (error) {
    console.error('Error:', error);
  }
};

// Example: Transfer tokens
const transferTokens = async (to, value) => {
  try {
    const accounts = await web3.eth.getAccounts();
    const sender = accounts[0];

    const result = await contract.methods.transfer(to, value).send({ from: sender });
    console.log('Tokens transferred:', result.transactionHash);
  } catch (error) {
    console.error('Error:', error);
  }
};

// Example: Approve spending
const approveSpending = async (spender, value) => {
  try {
    const accounts = await web3.eth.getAccounts();
    const owner = accounts[0];

    const result = await contract.methods.approve(spender, value).send({ from: owner });
    console.log('Spending approved:', result.transactionHash);
  } catch (error) {
    console.error('Error:', error);
  }
};

// Example: Transfer from
const transferFrom = async (from, to, value) => {
  try {
    const accounts = await web3.eth.getAccounts();
    const spender = accounts[0];

    const result = await contract.methods.transferFrom(from, to, value).send({ from: spender });
    console.log('Tokens transferred:', result.transactionHash);
  } catch (error) {
    console.error('Error:', error);
  }
};

// Example: Burn tokens
const burnTokens = async (value) => {
  try {
    const accounts = await web3.eth.getAccounts();
    const owner = accounts[0];

    const result = await contract.methods.burn(value).send({ from: owner });
    console.log('Tokens burned:', result.transactionHash);
  } catch (error) {
    console.error('Error:', error);
  }
};

// Call the desired functions with appropriate parameters

mintTokens('<recipient-address>', '<amount-to-mint>');
transferTokens('<receiver-address>', '<amount-to-transfer>');
approveSpending('<spender-address>', '<allowance-value>');
transferFrom('<from-address>', '<to-address>', '<amount-to-transfer-from>');
burnTokens('<amount-to-burn>');

License
This project is licensed under the MIT License. 