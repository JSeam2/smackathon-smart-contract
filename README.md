# Smackathon Smart Contract Idea
This repository possess the smart contract implementation of the project

# Idea
We create a curation market for artists and fans. Artists can create unique collectible tokens that they can sell on the market to raise funds. To incentivise sales of tokens, Artists can indicate in the descriptions what these tokens would entitle fans to. For example, backstage access, skype sessions. Fans who collect the tokens essentially possess a proof of support, allowing fans to claim OG fan status, verified on the blockchain. The tokens are tradeable, and the artist can define a royalty percentage fee that can be taxed on trades.  

# Deployed @ Rinkeby Testnet
[Link](https://rinkeby.etherscan.io/address/0x57e8f6c1ef8a94ecb1d3d2bb454884d5399a8425)

# Features
## Tokens Usage
1. Artists can mint collectible tokens to raise funds
2. Artists can Auction tokens minted
3. Artists can define in a description field what the tokens entitle fans to.
4. Artists can define a royalty percentage fee between 0 and 100 that will be credited to the Artist upon future transactions. (This fee has default value at 5 or 5%)

## Tokens 
1. Tokens are ERC-721 compliant and are tradeable
2. The tokens possess the following information
    ```
    string name
    string description
    address artistAddress
    uint artistTokenNumber // nth token created by artist
    uint timeCreated
    uint royaltyPercentage // set at 5% for now 
	```	

## Token Sale Auction
1. All tokens are to be sold as an auction. 
2. After minting tokens, artists can create auctions to sell tokens.
3. Fans who buy tokens, can resell tokens, during each sale. The original artist will receive a commission from the sale.

# Development
We use truffle and [remix](https://remix.ethereum.org) for development. 

## Using Truffle for Testing Locally
1. Install truffle. Check truffle official site for [instructions](http://truffleframework.com/)
2. Install ganache. Check ganache official site for [instructions](http://truffleframework.com/ganache/)
3. Ensure you are at the project directory 
4. On a terminal run ganache on port 7545, the testrpc it should run on localhost:7545
    ```
    $ ganache-cli -p 7545
    ```
5. Compile the contracts with truffle
    ```
    $ truffle compile
    ```
6. Migrate or deploy using ganache
    ```
    $ truffle migrate --network ganache 
    ```
7. Interfact with the contract
    ```
    $ truffle console --network ganache
    ```
8. You may interface with the contracts like this eg.
    ```
    truffle(ganache)> ArtistToken.deployed().then(inst => {token = inst;})
    truffle(ganache)> ArtistToken.<<method>>
    ```
9. To run tests, tests are found in ./test folder
    ```
    $ truffle test
    ```        
## Using Remix IDE
1. Using remix we can easily deploy the contracts with some web3 injector like metamask. 
2. Goto [remix](https://remix.ethereum.org)
3. We will need to connect remix to our local file system [see documentation](https://remix.readthedocs.io/en/latest/tutorial_connect_remix_with_your_filesystem/) using remixd
4. Install remixd
5. With remixd installed all we need to do is setup a websocket connection
    ```
    $ remixd -s <absolute-path-to-the-shared-folder>
    ```
6. Click on the localhost connection icon on the web ide and we should be connected to remix and you can develop off there.        
 
# References
This repository uses code and creates derivative work from [open-zeppelin](https://github.com/OpenZeppelin/openzeppelin-solidity). The license is provided below [link](https://github.com/OpenZeppelin/openzeppelin-solidity/blob/master/LICENSE) 

```
The MIT License (MIT)

Copyright (c) 2016 Smart Contract Solutions, Inc.

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be included
in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS
OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
```
