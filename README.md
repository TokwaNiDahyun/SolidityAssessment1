# San Miguel Beer Token (SMB) – A Custom Token Smart Contract

This Solidity program implements a simple token contract that demonstrates how to create, mint, and burn tokens. It covers fundamental concepts of Solidity, including public variables, mappings, and conditional checks. The project is intended to give beginners an introduction to developing smart contracts for tokens on the Ethereum blockchain.

## Description  

The contract allows users to manage a custom token with the following key features:
1. Public variables to store details about the token:  
   - **Token Name:** San Miguel Beer  
   - **Token Abbreviation:** SMB  
   - **Total Supply:** A dynamic value that changes with minting and burning events.  

2. A **mapping** to keep track of each address's token balance.  
3. A **mint function** to increase the token supply and assign tokens to a specified address.  
4. A **burn function** to reduce the supply and deduct tokens from an address, with safety checks to prevent burning more tokens than an address holds.

## Getting Started  

### Executing Program  

To run and interact with this contract, follow these steps:  

1. **Use Remix IDE:**  
   Go to [Remix](https://remix.ethereum.org/) and create a new file by clicking the "+" icon in the sidebar. Save the file with a `.sol` extension (e.g., `MyToken.sol`).  

2. **Copy and Paste Code:**  
   Copy the following code into your new file:  

   ```solidity
   // SPDX-License-Identifier: MIT
   pragma solidity 0.8.26;

   contract MyToken {

    // public variables here
    string public tokenName = "San Miguel Beer";
    string public tokenAbbrv = "SMB";
    uint public totalSupply = 0;

    // mapping variable here
   mapping(address => uint) public balances;

    // mint function
   function mint (address addr, uint val) public {
      totalSupply += val;
      balances[addr] += val;
   } 

    // burn function
   function burn (address addr, uint val) public {
      if (balances[addr] >= val) {
         totalSupply -= val;
         balances[addr]-= val;
      }
   } 
}

3. **Compile the Code:**

   * Click on the **Solidity Compiler** tab in the left sidebar.
   * Set the compiler version to `0.8.26` (or a compatible one).
   * Click **Compile MyToken.sol** to compile the code.

4. **Deploy the Contract:**

   * Go to the **Deploy & Run Transactions** tab.
   * Select **MyToken** from the contract dropdown menu.
   * Click **Deploy** to deploy the contract to the blockchain.

5. **Interact with the Contract:**

   * Use the **mint** function to add tokens by entering an address and value, then clicking **transact**.
   * Use the **burn** function to destroy tokens by providing an address and value, ensuring the address holds enough tokens to burn.

## Authors

Joshua FEUTECH Student

## License

This project is licensed under the MIT License – see the [LICENSE.md](LICENSE.md) file for details.
