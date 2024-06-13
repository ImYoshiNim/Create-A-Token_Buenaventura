# Create a Token

In this Solidity program, we're building a basic MyToken contract, fulfilling the requirements outlined in Metacrafters, a computer science course. This contract simulates a digital currency with its own name, abbreviation, and total supply. We'll implement functions to mint new tokens, effectively increasing the total supply and assigning those tokens to a user's address, and burn existing tokens, reducing the total supply and deducting them from the user's balance. But remember, burning only works if the user has enough tokens to spare!

## Description

This program defines a MyToken contract that creates a digital currency with a name, abbreviation, and total supply. It allows users to mint new tokens (increasing supply and sender's balance) and burn existing ones (reducing supply and sender's balance), but only if the sender has enough tokens to burn.

## Functions

Mint Function:
The mint function increases the total supply of your token by a specified amount and increases the sender's balance in the contract by the same amount. It achieves this by adding (+=) the input value to both the totalSupply variable and the sender's balance in the balances mapping.

Burn Function:
The burn function decreases the total supply of your token by a specified amount and decreases the sender's balance in the contract by the same amount, if the sender has a sufficient balance to burn the specified number of tokens. It achieves this by subtracting (-=) the input value from both the totalSupply variable and

### Executing program
To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., Name_myToken.sol). Copy and paste the following code into the file:

```javascript
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
    string public tokenName = "ADAMTKN";
    string public tokenAbbr = "ADM";
    uint public totalSupply = 0;

    // mapping variable here
    mapping(address => uint) public balances;
    
    // mint function
    function mint (address _address, uint _value) public {
        totalSupply += _value;
        balances[_address] += _value;
    }

    // burn function
    function burn (address _address, uint _value) public {
        if(balances[_address] >= _value){
        totalSupply -= _value;
        balances[_address] -= _value;
        }
    }
}

```


To compile the code, navigate to the "Solidity Compiler" tab in the left-hand side of the sidebar. Ensure the "Compiler" version is set to "0.8.18", and then click the "Compile Name_myToken.sol" button.

Once the contract has finished compiling, select the "Deploy & Run Transactions" tab located on the sidebar's left side. Click "Deploy" after selecting the "My Token - FinalProject.sol" contract from the dropdown menu.

After the contract is deployed, you can communicate with it by calling the specified address's balance and by using the previously discussed mint and burn features. The "transact" button can be used to execute the "mint" and "burn" functions in the left-hand sidebar. This will add or subtract amounts from the total supply and the balance of the associated address.

## Authors


## License

This project is licensed under the MIT License - see the LICENSE.md file for details
