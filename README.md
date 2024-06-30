# Functions and Errors
This solidity program demonstrates the creation of our own personalized ERC20 token and deploying it using Remix editor.

## Description

This program is a simple contract written in Solidity, a programming language used for developing smart contracts on the Ethereum blockchain. In the contract only the owner is able to
mint tokens and any user is able to transfer or burn tokens.

## Getting Started

### Executing program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., ERC20Token.sol). 
Copy and paste the following code into the file:

```javascript
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.9;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract Token is ERC20("Asphalt","ASP"){
    address private owner = msg.sender;

    modifier onlyOwner() {
        require(msg.sender == owner, "Action denied, only owner can perform this action.");
        _;
    }

    function mintTokens(address to, uint256 amount) public onlyOwner {
        _mint(to, amount);
    }

    function burnTokens(uint256 amount) public {
        _burn(msg.sender, amount);
    }

    function transfer(address recipient, uint256 amount) public virtual override returns (bool) {
        _transfer(_msgSender(), recipient, amount);
        return true;
    }
}
```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.18" (or another compatible version), 
and then click on the "Compile ERC20Token.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. 
Select the "ERC20Token" contract from the dropdown menu, and then click on the "Deploy" button.

Once the contract is deployed, you can interact with the ERC20 token using the functions you have created. The functions to mint, transfer and burn tokens can be used and tested as per requirement.
The tokens can be minted only by the owner whereas the transfer and burning of tokens can be done by any user account.

## Authors

Aditya Singh
