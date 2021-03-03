# The First Test- Creating a New Zombie

Before deploying to Ethereum, it is best to test your smart contracts locally.

You can do so by using a tool called [Ganache](https://truffleframework.com/ganache), which sets up a local Ethereum network.

Every time Ganache starts, it creates 10 test accounts and gives them 100 Ethers to make testing easier. Since Ganache and Truffle are tightly integrated we can access these accounts through the `accounts` array we've mentioned in the previous chapter.

But using `accounts[0]` and `accounts[1]` would not make our tests read well, right?

To aid comprehension, we'd like to use two placeholder names- Alice and Bob. So, inside the contract() function, let's initialize them like so:

```
let [alice, bob] = accounts;
```

> Note: Forgive the poor grammar. In JavaScript, the convention is to use lowercase for variable names.

Why Alice and Bob? There is a big tradition that makes Alice and Bob or "A and B" common names used in cryptography, physics, programming, and more. It's a short but interesting history, and well worth a [read](http://cryptocouple.com/) after you complete this lesson.

Now let's move on to our first test.

## Creating a New Zombie

Say Alice wants to play our awesome game. If so, the first thing she would want to do is to create her own zombie 🧟. To do that, the front-end (or Truffle in our case) would have to call the `createRandomZombie` function.

> Note: As a review, here is the Solidity code in our contract:

```
 function createRandomZombie(string _name) public {
   require(ownerZombieCount[msg.sender] == 0);
   uint randDna = _generateRandomDna(_name);
   randDna = randDna - randDna % 100;
   _createZombie(_name, randDna);
 }
```

We begin by testing this function.
