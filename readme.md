# Assignment Table Checklist

| Mark | Output                                                                                                                                                                                                                                    | Location                                                                            |
| ---- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| 5%   | Setting up Ethereum account (public address and private key to be provided for Node.JS application)                                                                                                                                       | BCAP/address_of_owner.txtBCAP/encrypted_private_key.txt |
| 5%   | Deploying verified ERC20 contract to Ethereum Test Net (contract address to be provided for Node.JS application)                                                                                                                          | BCAP/testnet_address_of_contract.txt                                  |
| 15%  | Providing functional Node.JS application to process token distribution file                                                                                                                                                               | BCAP/distribution.js                                                            |
| 5%   | Providing access to github repo containing delivered assignment code                                                                                                                                                                      | BCAP/github_repo_url.txt                                                       |
| 10%  | Providing complete and clear readme.md instructions for application execution of token distribution                                                                                                                                       | readme.md                                                                           |
| 5%   | Providing Node.js application Docker container, along with clear instructions for building and executing distribution via Docker                                                                                                          | PruthvirajBlockChain-container.zip readme.md                       |
| 5%   | Making Docker container available on Docker Hub                                                                                                                                                                                           | BCAP/docker_hub_url.txt                                                        |
| 25%  | Providing 2-page report on process of development of contract and setting up of accounts across the platform                                                                                                                              | reports/BlockChainReport1.docx                                            |
| 20%  | Providing 1-page report on the Use and Purpose of Smart Contracts as demonstrated in your project work. Provide your thoughts and insight into the impact of the ability to create tokens in this manner, including any ethical concerns. | reports/BlockChainReport2.docx                                             |
| 5%   | 5-7 Min Pre-recorded Demonstration displaying the operation of the contract.                                                                                                                                                              | videos/BlockChain.mov                                        |

# Ethereum Accounts

## Main Account

- [MA_01](https://ropsten.etherscan.io/token/0x943845aa72da72ef7e19e0f9b2493f5949bc465f?a=0x8a51546fc92cbf8dd33d66b1c4f1f108fe612796)

## Secondary Accounts

- [SA_01](https://ropsten.etherscan.io/token/0x943845Aa72dA72Ef7e19e0F9B2493F5949bC465F?a=0x94ed1bef740620d7e868594ae0cf772184)
- [SA_02](https://ropsten.etherscan.io/address/0xdc3bdb898ada30e5ba32a5d45ac6e63f29d69387)

# ERC20 TRC Contract

[Token Contract Address](https://ropsten.etherscan.io/token/0x943845aa72da72ef7e19e0f9b2493f5949bc465f?a=0x8a51546fc92cbf8dd33d66b1c4f1f108fe612796)

Instead of code the distribution formula in node,
I create two new functions in Solidity contract to support token distribution.
Below are the details about both functions.

### Get Balance of Owner by Percentage

```solidity
function balanceOfOwnerByPercentage(uint256 percentageAmount) public view returns (uint256) {
    return _balances[tokenOwner].mul(percentageAmount).div(100);
}
```

### Parameter 1: percentageAmount (%)

```solidity
Sample Value:
5
```

## Distribute Token

```solidity
function transferMultipleByPercentage(address[] memory addresses, uint256 percentageAmount) public returns (bool) {
    uint256 amount = balanceOfOwnerByPercentage(percentageAmount).div(addresses.length);

    for (uint i = 0; i < addresses.length; i++) {
        _balances[tokenOwner] = _balances[tokenOwner].sub(amount, "transfer amount exceeds balance");
        _balances[addresses[i]] = _balances[addresses[i]].add(amount);
        emit Transfer(tokenOwner, addresses[i], amount);
    }
    return true;
}
```

### Parameter 1: Address[] (Pass account addresses as array)

```solidity
Sample Value:
["0x2F814cCb88A752F5ba274D76Fc65c2F9e5F264F0",
  "0xEa31b9ee14BdE262a76b873C33a8253C7Cd28020",
  "0xdE42B1B0575C85a4fae476a86D21b4BaCcF1F758",
  "0xcF250d3777BD6C86A302739C86058371997d6693",
  "0xeC1C18b1d9CD728C208113A6E1E7234425b1a29f"]
```

### Parameter 2: percentageAmount (%)

```solidity
Sample Value:
5
```

[Sample Transaction Result](https://ropsten.etherscan.io/tx/0xeb201a16eecb8ba51e29a974dc63e36fdd50c21f0244366b3e757b1eecc77072)

# How to Execute TRC Token Distribution Node Application (Manual)

1. Download and install [Node](https://nodejs.org/en/download/)!
2. Go to BlockChain folder, make sure you can see package.json and type below command:
   ```npm
   npm i
   ```
3. Put the correct private key in src/tokenDistribution.js line **7**

   ```
   How to get the correct private key?

   Try to decode documents/encrypted_private_key.txt using Salad Chiper, https://cryptii.com/
   ```

4. Modify BCAP/addresses.txt, make sure you put correct ETH accounts that you want to transfer, put line space between each of them
5. Make sure you still in BlockChain folder, type below command to run the application:
   ```npm
   node BCAP/distribution.js
   ```

# How to Execute TRC Token Distribution Node Application (Docker)

1. Put the correct private key in BCAP/distribution.js line **7**

   ```
   How to get the correct private key?

   Try to documents/decode encrypted_private_key.txt using Salad Chiper, https://cryptii.com/
   ```

2. Modify BCAP/addresses.txt, make sure you put correct ETH accounts that you want to transfer, put line space between each of them

3. Go to BlockChain folder, make sure you can see dockerfile and type below command:

   ```docker
   docker build -t BlockChain .
   ```

4. To run the docker, you can simply type below command:
   ```docker
   docker run BlockChain
   ```
5. If you lazy to build and configure, I have pushed defaulted value token distribution application as Docker image to Docker Hub, you can pull it and run using below command:
   ```docker
   docker pull BlockChain
   docker run BlockChain
   ```

# Closing

If you have any issues or want to clarify something, contact me at x20190182@student.ncirl.ie<br />
