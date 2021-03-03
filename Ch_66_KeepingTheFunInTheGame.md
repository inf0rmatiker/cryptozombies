# Keeping the Fun in the Game

Awesome work so far! Now we know for sure our users can create new zombies👌🏻.

However, if they could keep calling this function to create unlimited zombies in their army, the game wouldn't be very fun. Thus, in Chapter 4 of Lesson 2 we've added a `require` statement to the `createZombieFunction()` that makes sure each user can't own more than one zombie:

```
require(ownerZombieCount[msg.sender] == 0)
```

Let's test this feature and see if it works.

## Hooks

In just a few minutes🤞, we'll have more than one test and the way this works is that each test should start with a clean sheet. Thus, for every single test we'll have to create a new instance of our smart contract like so:

```
const contractInstance = await CryptoZombies.new();
```

Wouldn't be nice if you could write this just once and have Truffle run it automatically for every test?

Well... one of Mocha's (and Truffle's) features is the ability to have some snippets of code called hooks run before or after a test. To run something before a test gets executed, the code should be put inside a function named `beforeEach()`.

So, instead of writing `contract.new()` several times, you just do it once like this:

```
beforeEach(async () => {
  // let's put here the code that creates a new contract instance
});
```

Then, Truffle will take care of everything. That's pretty sweet, isn't it?

## 🧟‍♂️Here be... zombies of every kind!!!🧟‍♂️

If you really, really want to achieve mastery, go ahead and read on. Otherwise... just click next and off you go to the next chapter.

You still around?😁

Awesome! After all, why would you want to deny yourself a whole lot of awesomeness?

Now, let's circle back to how `contract.new` works. Basically, every time we call this function, Truffle makes it so that a new contract gets deployed.

On one side, this is helpful because it lets us start each test with a clean sheet.

On the other side, if everybody would create countless contracts the blockchain will become bloated. We want you to hang around, but not your old test contracts!

We would want to prevent this from happening, right?

Happily, the solution is pretty straightforward... our contract should `selfdestruct` once it's no longer needed.

The way this works is as follows:

- first, we would want to add a new function to the `CryptoZombies` smart contract like so:

```
function kill() public onlyOwner {
   selfdestruct(owner());
}
```

> Note: If you want to learn more about `selfdestruct()`, you can read the Solidity docs [here](https://solidity.readthedocs.io/en/v0.4.21/introduction-to-smart-contracts.html#self-destruct). The most important thing to bear in mind is that `selfdestruct` is the only way for code at a certain address to be removed from the blockchain. This makes it a pretty important feature!

- next, somewhat similar to the `beforeEach()` function explained above, we'll make a function called `afterEach()`:

```
afterEach(async () => {
   await contractInstance.kill();
});
```

- Lastly, Truffle will make sure this function is called after a test gets executed.

And voila, the smart contract removed itself!

We have a lot of ground to cover in this lesson, and implementing this feature will likely require at least 2 additional chapters. So, we trust you to add it.💪🏻
