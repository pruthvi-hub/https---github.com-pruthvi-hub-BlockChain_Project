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
0x8a51546fc92cbf8dd33d66b1c4f1f108fe612796

## Secondary Accounts

- [SA_01](https://ropsten.etherscan.io/address/0xadc35d76f875959ccf0b8d84fb4437f4723a81b4)
0xAdC35D76f875959CCF0B8D84FB4437f4723a81B4
- [SA_02](https://ropsten.etherscan.io/address/0xdc3bdb898ada30e5ba32a5d45ac6e63f29d69387)
0xdC3bdb898ADA30E5BA32a5d45aC6E63F29D69387

# ERC20 TRC Contract

[Token Contract Address](https://ropsten.etherscan.io/token/0x943845aa72da72ef7e19e0f9b2493f5949bc465f?a=0x8a51546fc92cbf8dd33d66b1c4f1f108fe612796)


[Sample Transaction Result](https://ropsten.etherscan.io/tx/0xeb201a16eecb8ba51e29a974dc63e36fdd50c21f0244366b3e757b1eecc77072)

# How to Execute TRC Token Distribution Node Application (Manual)

1. Download and install [Node](https://nodejs.org/en/download/)!
2. Go to BlockChain folder, make sure you can see package.json and type below command:
   ```npm
   npm i
   ```
3. Put the correct private key in BCAP/distribution.js line **7**

   ```
   How to get the correct private key?

   Try to decode BCAP/encrypted_private_key.txt using Salad Chiper, https://cryptii.com/
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

   Try to BCAP/decode encrypted_private_key.txt using Salad Chiper, https://cryptii.com/
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
