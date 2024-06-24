# Project Title

Mastering Solidity.

## Description

This Solidity smart contract manages a digital token called "Magestic Coin" (MC). It includes public variables for the token’s name, abbreviation, and total supply. The contract tracks the balance of tokens each user holds through a mapping. It provides a `mintToken` function to create new tokens and add them to a user’s balance, increasing the total supply. Conversely, the `burnToken` function destroys tokens from a user's balance, reducing the total supply, but only if the user has enough tokens to burn. This contract facilitates the creation and destruction of tokens while maintaining accurate balances and total supply.
## Getting Started

### Installing

* To run your `MyToken` contract in Remix, open [Remix IDE](https://remix.ethereum.org/), create a new file named `MyToken.sol`, paste the contract code, compile it using Solidity version `0.8.18`, and deploy it in the JavaScript VM environment. You can then interact with the contract's functions to mint and burn tokens and check balances.

### Executing program

* To run the `MyToken` contract in Remix IDE, start by opening [Remix IDE](https://remix.ethereum.org/) in your web browser. Create a new file named `MyToken.sol` and paste the provided contract code into this file. Next, switch to the "Solidity Compiler" tab, select the compiler version `0.8.18`, and compile the contract. Once compiled, move to the "Deploy & Run Transactions" tab, choose the "JavaScript VM (London)" environment, and deploy the `MyToken` contract. After deployment, you can interact with the contract by calling its functions, such as minting new tokens or burning existing ones, directly from the Remix interface.
* Project Code

```
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

/*
       REQUIREMENTS
    1. Your contract will have public variables that store the details about your coin (Token Name, Token Abbrv., Total Supply)
    2. Your contract will have a mapping of addresses to accounts (address => uint)
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
    string  public tokenName = "Magestic Coin";
    string public tokenNot  = "MC";
    uint256 public totalSupply = 0;




    // mapping variable here
        mapping (address => uint256) public accounts;

    // mint function
    function mintToken(address _address ,uint256 _value ) public {
            totalSupply+=_value;
            accounts[_address] += _value;
            
    }
    // burn function
        function burnToken(address _address ,uint256 _value ) public  {
            if(accounts[_address]>=_value){

            totalSupply -=_value;
            accounts[_address] -= _value;
            }   
            
    }

}
```
## Usage

To interact with this contract, you can use tools like Remix to deploy and test the contract on Ethereum testnets or local blockchain environments.

## Authors
Ridham Dhir  
ridham.dhir18@gmail.com


## License

This project is licensed under the MIT License - see the LICENSE.md file for details
