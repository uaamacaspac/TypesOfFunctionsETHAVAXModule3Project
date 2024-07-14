# Uriel Token Contract

This repository contains the `Uriel` ERC-20 token contract, which includes minting and burning functionalities. It is built using OpenZeppelin's secure and well-audited libraries.

## Contract Details

- **Token Name:** Uriel
- **Token Symbol:** UIL
- **Solidity Version:** ^0.8.0
- **Dependencies:** 
  - [OpenZeppelin ERC20](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/v4.3.0/contracts/token/ERC20/ERC20.sol)
  - [OpenZeppelin Ownable](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/v4.3.0/contracts/access/Ownable.sol)

## Functions

### Constructor
```solidity
constructor(uint256 initialSupply) ERC20("Uriel", "UIL") {
    _mint(msg.sender, initialSupply);
}
```
Initializes the contract with the given `initialSupply` and mints the tokens to the deployer's address.

### Mint
```solidity
function mint(address to, uint256 amount) public onlyOwner {
    _mint(to, amount);
}
```
Allows the contract owner to mint new tokens to the specified address.

### Burn
```solidity
function burn(uint256 amount) public {
    _burn(msg.sender, amount);
}
```
Allows any token holder to burn their tokens, reducing the total supply.

### Transfer
```solidity
function transfer(address recipient, uint256 amount) public override returns (bool) {
    require(recipient != address(0), "ERC20: transfer to the zero address");
    require(balanceOf(msg.sender) >= amount, "ERC20: transfer amount exceeds balance");

    // Call the parent contract's transfer function
    bool success = super.transfer(recipient, amount);

    return success;
}
```
Allows token holders to transfer their token to other addresses. Added this to the code as required by metacrafter and not just use the code from ERC20.

### ERC20 Inherited Functions
The following functions are inherited from the OpenZeppelin ERC20 contract:
- **totalSupply:** Returns the total number of tokens in circulation.
- **balanceOf:** Returns the token balance of a specified address.
- **transfer:** Transfers tokens to a specified address.
- **name:** Returns the name of the token.
- **owner:** Returns the address of the contract owner.

## Getting Started

### Prerequisites
- Remix

### Compile

- Compile the contract via Remix.


### Deployment

- Deploy the contract with the desired owner address and ready other addresses for the demonstration.

### Interacting with the Contract

- Use remix for calling the functions and change the addresses using remix to verify functions and modifiers functionality.
