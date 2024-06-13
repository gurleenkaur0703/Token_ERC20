# SportsToken ERC20 Smart Contract
This repository contains the Solidity smart contract for SportsToken, an ERC20-compliant token. 
The contract is designed using the OpenZeppelin ERC20 implementation to ensure security and standard compliance. 
The contract allows the owner to mint and burn tokens.
![image](https://github.com/gurleenkaur0703/Token_ERC20/assets/170515862/30295dfa-38d2-48b7-904d-93a0cd392b4a)

## Contract Description:

### Contract Details

#### • Token Name: SportsToken
#### • Token Symbol: ST
#### • Decimals: 18 (default for ERC20 tokens)
#### • Initial Supply: Specified during deployment

### State Variables

#### •	Owner: A state variable to store the address of the contract owner.

### Constructor():
The constructor function initializes the owner variable with the address of the contract deployer (msg.sender).
Mints the initial supply of tokens to the owner's address using the _mint function provided by the OpenZeppelin ERC20 contract.

### Functions
#### •	mint(address to, uint256 amount)
A public function that allows the owner to mint new tokens.
Uses require to ensure that only the owner can call this function
Calls the _mint function to mint the specified amount of tokens to the given address.

#### •	burn(uint256 amount) 
A public function that allows the owner to burn tokens.
Uses require to ensure that only the owner can call this function.
Calls the _burn function to burn the specified amount of tokens from the owner's balance.

## Getting Started

### Installing

•	Simply search for remix.ethereum.org in your web browser.	No installation is required.

### Executing program
• Open Remix IDE in your browser. Create a New File with .sol extention. Copy and paste the following code into the file:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/v4.0.0/contracts/token/ERC20/ERC20.sol";

contract SportsToken is ERC20("SportsToken", "ST") {
    address public owner;

    constructor(uint256 initialSupply)  {
        owner = msg.sender;

        _mint(owner, initialSupply);
    }

    function mint(address to, uint256 amount) public {

        require(msg.sender == owner, "Only the owner has the access to mint tokens");
        _mint(to, amount);
    }

    function burn(uint256 amount) public {

        require(msg.sender == owner, "Only the owner has the access to burn tokens");

        _burn(owner, amount);
    }
}

```
Compile and then deploy the Contract. When the contract is deployed, the constructor function is executed.
The constructor function takes an initialSupply parameter, which specifies the number of tokens to be minted initially.

After deployment, you can check the token balance of the owner's address. 
The balance of the owner's address will be equal to the initialSupply specified during deployment.

If the owner calls the mint function, the specified amount of tokens will be minted to the to address.
The balance of the to address will increase by the minted amount.

If the owner calls the burn function, the specified amount of tokens will be burned from the owner's balance.
The total supply of the token will decrease by the burned amount.


## Authors

Gurleen Kaur
(@https://github.com/gurleenkaur0703)

## License

This project is licensed under the MIT License.
