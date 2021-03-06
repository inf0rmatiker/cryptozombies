# The First Test- Creating a New Zombie (cont'd)

Now that we've got our ducks -ahem zombies- in row, let's move forward to the next phase... 🧟🦆‍🧟🦆🧟🦆‍🧟🦆🧟🦆‍🧟🦆

## 2. Act

We've reached the part where we're going to be calling the function that creates a new zombie for Alice- `createRandomZombie`.

But there's a slight problem- how can we make it so the method "knows" who calls it? Another way to put it would be- how can we make sure Alice (and not Bob) is going to be the owner of this new zombie?🧐

Well... the problem is solved with the contract abstraction. One of the features of Truffle is that it wraps the original Solidity implementation and lets us specify the address that makes the function call by passing that address as an argument.

The following calls `createRandomZombie` and makes sure `msg.sender` is set to Alice's address:

```
const result = await contractInstance.createRandomZombie(zombieNames[0], {from: alice});
```

Now I have a quick question for you: do you know what gets stored in `result`?

Well, let me explain.

## Logs and Events

Once we specified the contract we wanted to test using `artifacts.require`, Truffle automatically provides the logs generated by our smart contract. What this means is that we can now retrieve the `name` of Alice's newly created zombie using something like this: `result.logs[0].args.name`. In a similar fashion, we can get the `id` and the `_dna`.

Besides these bits of information, `result` is going to be giving us several other useful details about the transaction:

- `result.tx`: the transaction hash
- `result.receipt`: an object containing the transaction receipt. If `result.receipt.status` is equal to `true` it means that the transaction was successful. Otherwise, it means that the transaction failed.

> Note: Note that logs can also be used as a much cheaper option to store data. The downside is that they can't be accessed from within the smart contract itself.

## 3. Assert

In this chapter we will be using the built-in assertion module which comes with a set of assertion functions such as `equal()` and `deepEqual()`. Simply put, these functions check the condition and `throw` an error if the result is not as expected. Since we will be comparing simple values, we are going to be running `assert.equal()`.
