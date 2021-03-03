# Getting Set Up (cont'd)

Let's move forward. In this chapter, we're going to continue setting things up so we can write and run our tests.

## Build Artifacts

Every time you compile a smart contract, the Solidity compiler generates a JSON file (referred to as build artifacts) which contains the binary represenation of that contract and saves it in the `build/contracts` folder.

Next, when you run a migration, Truffle updates this file with the information related to that network.

The first thing you'll need to do every time you start writing a new test suite is to load the build artifacts of the contract you want to interact with. This way, Truffle will know how to format our function calls in a way the contract will understand.

Let's look at a simple example.

Say there was a contract called `myAwesomeContract`. We could do something like the following to load the build artifacts:

```
const myAwesomeContract = artifacts.require(“myAwesomeContract”);
```

The function returns something called a **contract abstraction**. In a nutshell, a contract abstraction hides the complexity of interacting with Ethereum and provides a convenient JavaScript interface to our Solidity smart contract. We'll be using it in the next chapters.

## The `contract()` function

Behind the scenes, Truffle adds a thin wrapper around Mocha in order to make testing simpler. Since our course focuses on Ethereum development, we won't be spending much time explaining the bits and bytes of Mocha. If you're inclined to learn more about Mocha, check out [their website](https://mochajs.org/), once you're done with this lesson. For now, you only have to understand what we cover here - how to:

- group tests by calling a function named `contract()`. It extends Mocha's `describe()` by providing a list of accounts for testing and doing some cleanup as well.

`contract()` takes two arguments. The first one, a `string`, must indicate what we’re going to test. The second parameter, a `callback`, is where we’re going to actually write our tests.

- execute them: the way we’ll be doing this is by calling a function named `it()` which also takes two arguments: a `string` that describes what the test actually does and a `callback`.

Putting it together, here's a bare-bones test:

```
 contract("MyAwesomeContract", (accounts) => {
   it("should be able to receive Ethers", () => {
   })
 })
```

> Note: A well-thought test explains what the code actually does. Make sure the description of the test suite and the test case can be read together as a coherent statement. It’s like you’re writing documentation.

Every test you’ll want to write follows this simple pattern. Pretty easy, isn't it?😁
