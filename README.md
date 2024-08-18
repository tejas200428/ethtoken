# Kitty Token Contract

This Solidity program is a simple illustration of the generation, minting, and burning of tokens.

## Description

This program is a simple contract written in Solidity, a programming language used for developing smart contracts on the Ethereum blockchain. The contract defines a token with a name, abbreviation, and total supply. It includes functionalities to mint new tokens and burn existing ones.

## Getting Started

### Executing Program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at [Remix Ethereum](https://remix.ethereum.org/).

```solidity
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;
/*
       REQUIREMENTS
    1. Your contract will have public variables that store the details about your coin (Token Name, Token Abbrv., Total Supply)
    2. Your contract will have a mapping of addresses to balances (address => uint)
    3. You will have a mint function that takes two parameters: an address and a value. 
       The function then increases the total supply by that number and increases the balance 
       of the “sender” address by that amount
    4. Your contract will have a burn function, which works the opposite of the mint function, as it will destroy tokens. 
       It will take an address and value just like the mint functions. It will then deduct the value from the total supply 
       and from the balance of the “sender”.
    5. Lastly, your burn function should have conditionals to make sure the balance of "sender" is greater than or equal 
       to the amount that is supposed to be burned.
*/
contract MyToken {
  
    // public variables here
    bytes32 public tokenName = "Kitty";
    bytes32 public tokenAbbrv = "KTY";
    uint public supply = 0;
    // mapping variable here
    mapping(address=>uint) public balances;
    // mint function
    function mint(address _addr, uint _value) public {
        supply+=_value;
        balances[_addr]+=_value;
    }
// burn function
    function burn(address _addr, uint _value) public {
        if(balances[_addr]>=_value){
            supply-=_value;
            balances[_addr]-=_value;
        } else{
            revert("Insufficient balance");
        }
    }
}
```
To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.18" (or another compatible version), and then click on the "Compile Token.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "Token" contract from the dropdown menu, and then click on the "Deploy" button.

## License
This project is licensed under the MIT License - see the LICENSE.md file for details
