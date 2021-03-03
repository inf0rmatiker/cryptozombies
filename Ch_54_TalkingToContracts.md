# Talking to Contracts

Now that we've initialized Web3.js with MetaMask's Web3 provider, let's set it up to talk to our smart contract.

Web3.js will need 2 things to talk to your contract: its **address** and its **ABI**.

## Contract Address

After you finish writing your smart contract, you will compile it and deploy it to Ethereum. We're going to cover deployment in the next lesson, but since that's quite a different process from writing code, we've decided to go out of order and cover Web3.js first.

After you deploy your contract, it gets a fixed address on Ethereum where it will live forever. If you recall from Lesson 2, the address of the CryptoKitties contract on Ethereum mainnet is `0x06012c8cf97BEaD5deAe237070F9587f8E7A266d`.

You'll need to copy this address after deploying in order to talk to your smart contract.

## Contract ABI

The other thing Web3.js will need to talk to your contract is its **ABI**.

ABI stands for Application Binary Interface. Basically it's a representation of your contracts' methods in JSON format that tells Web3.js how to format function calls in a way your contract will understand.

When you compile your contract to deploy to Ethereum (which we'll cover in Lesson 7), the Solidity compiler will give you the ABI, so you'll need to copy and save this in addition to the contract address.

Since we haven't covered deployment yet, for this lesson we've compiled the ABI for you and put it in a file named `cryptozombies_abi.js`, stored in variable called `cryptoZombiesABI`.

If we include `cryptozombies_abi.js` in our project, we'll be able to access the CryptoZombies ABI using that variable.

## Instantiating a Web3.js Contract

Once you have your contract's address and ABI, you can instantiate it in Web3 as follows:

```
// Instantiate myContract
var myContract = new web3js.eth.Contract(myABI, myContractAddress);
```
