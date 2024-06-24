# SportsToken ERC20 Smart Contract
SportsToken is an ERC20 token contract built using the OpenZeppelin library. It includes basic ERC20 functionality with additional features for minting and burning tokens. Only the owner (the deployer) has the authority to mint new tokens and burn tokens from their balance.


## Contract Description:

### Contract Details

#### • Token Name: SportsToken
#### • Token Symbol: STK
#### • Decimals: 18 (default for ERC20 tokens)
#### • Initial Supply: Specified during deployment

### State Variables

#### •	Owner: A state variable to store the address of the contract owner.

### Constructor():
The constructor function initializes the owner variable with the address of the contract deployer (msg.sender).
Mints the initial supply of tokens to the owner's address using the _mint function provided by the OpenZeppelin ERC20 contract.

### Functions
#### •	transfer(address to, uint256 amount)
Overrides the transfer function from ERC20.
Calls the transfer function from ERC20 to perform the token transfer. 
It ensures that token transfers are executed following the standard ERC20 specifications.
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
• Open Remix IDE: Go to Remix IDE.

• Create a new file named with .sol extention. Copy and paste the SportsToken contract code into SportsToken.sol.
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract SportsToken is ERC20 {
    address public owner;

    constructor(uint256 initialSupply) ERC20("SportsToken", "STK") {
        owner = msg.sender;
        _mint(msg.sender, initialSupply);
    }
    modifier onlyOwner() {
        require(msg.sender == owner, "Only Owner Can Access");
        _;
    }
function transfer(address to, uint256 amount) public override returns (bool) {
        return ERC20.transfer(to, amount);
    }
    function mint(address to, uint256 amount) public onlyOwner {
        _mint(to, amount);
    }
    function burn(uint256 amount) public onlyOwner{
        _burn(msg.sender, amount);
    }
}
```

• Compile the Contract by selecting the appropriate compiler version (0.8.0 or above).

• Go to the "Deploy & Run Transactions" tab. Select the contract from the dropdown.

• Specify the initial supply (e.g., 1000000000000000000000000 for 1,000,000 tokens with 18 decimals). Click "Deploy".


## Authors

Gurleen Kaur
(@https://github.com/gurleenkaur0703)

## License

This project is licensed under the MIT License.
