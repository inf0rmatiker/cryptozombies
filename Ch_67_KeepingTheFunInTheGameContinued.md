# Keeping the Fun in the Game (cont'd)

In this chapter, we're going to fill in the body of our second test. Here's what it should do:

- First, Alice should call `createRandomZombie` and give it `zombieNames[0]` as the name of her first zombie.
- Next, Alice should try to create her second zombie. The only thing that's different is that this time, the zombie name should be set to `zombieNames[1]`.
- At this point, we expect the contract to `throw` an error.
- Since our test should pass only if the smart contract errors out, our logic will look a bit different. We’ll have to wrap the second `createRandomZombie` function call inside of a `try/catch` block as follows:

```
try {
    //try to create the second zombie
    await contractInstance.createRandomZombie(zombieNames[1], {from: alice});
    assert(true);
  }
  catch (err) {
    return;
  }
assert(false, "The contract did not throw.");
```

Now we've got exactly what we wanted, right?

Hmmm... we're pretty close but not quite there.

In order to keep our tests nice and tidy we've moved the code above to `helpers/utils.js` and imported it into “CryptoZombies.js” like so:

```
const utils = require("./helpers/utils");
```

And this is how the line of code that calls the function should look like:

```
await utils.shouldThrow(myAwesomeContractInstance.myAwesomeFunction());
```
