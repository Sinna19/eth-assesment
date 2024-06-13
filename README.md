# MyToken Solidity Contract

## Overview

This project contains a simple Solidity smart contract for an ERC-20-like token named `MyToken`. The contract includes functionalities for minting and burning tokens and maintains a record of balances for different addresses.

## Contract Details

- **Token Name**: `MyToken`
- **Token Abbreviation**: `MTK`
- **Total Supply**: The total supply is set during deployment.

## Features

1. **Public Variables**:
   - `tokenName`: Name of the token.
   - `tokenAbbrv`: Abbreviation of the token.
   - `totalSupply`: Total supply of the token.

2. **Mapping**:
   - `balances`: Maps addresses to their respective token balances.

3. **Functions**:
   - `mint(address _to, uint256 _amount)`: Increases the total supply and the balance of the specified address.
   - `burn(address _from, uint256 _amount)`: Decreases the total supply and the balance of the specified address if the balance is sufficient.

## Deployment Instructions

### Prerequisites

- **Remix IDE**: Go to [Remix IDE](https://remix.ethereum.org/).
- **MetaMask**: For deploying to a testnet or the mainnet, make sure MetaMask is installed and configured.

### Steps to Deploy

1. **Open Remix IDE**:
   - Go to [Remix IDE](https://remix.ethereum.org/).

2. **Create a New File**:
   - In the left sidebar, click on the "File explorers" tab.
   - Click the "+" button to create a new file.
   - Name the file `MyToken.sol`.

3. **Paste the Contract Code**:
   - Copy the following Solidity code into `MyToken.sol`:

   ```solidity
   // SPDX-License-Identifier: MIT
   pragma solidity 0.8.18;

   contract MyToken {

       // Public variables
       string public tokenName;
       string public tokenAbbrv;
       uint256 public totalSupply;

       // Mapping of addresses to balances
       mapping(address => uint256) public balances;

       // Constructor to initialize the token details
       constructor(string memory _name, string memory _abbrv, uint256 _initialSupply) {
           tokenName = _name;
           tokenAbbrv = _abbrv;
           totalSupply = _initialSupply;
           // Assign the initial supply to the contract deployer
           balances[msg.sender] = _initialSupply;
       }

       // Mint function to create new tokens
       function mint(address _to, uint256 _amount) public {
           totalSupply += _amount;
           balances[_to] += _amount;
       }

       // Burn function to destroy tokens
       function burn(address _from, uint256 _amount) public {
           require(balances[_from] >= _amount, "Insufficient balance to burn");
           totalSupply -= _amount;
           balances[_from] -= _amount;
       }
   }
   
# Authors
  Aayushi Sinha

# License
This project is licensed under the MIT License.
