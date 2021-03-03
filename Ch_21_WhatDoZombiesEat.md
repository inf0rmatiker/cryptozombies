# What Do Zombies Eat?

It's time to feed our zombies! And what do zombies like to eat most?

Well it just so happens that CryptoZombies love to eat...

CryptoKitties! 😱😱😱

(Yes, I'm serious 😆 )

In order to do this we'll need to read the kittyDna from the CryptoKitties smart contract. We can do that because the CryptoKitties data is stored openly on the blockchain. Isn't the blockchain cool?!

Don't worry — our game isn't actually going to hurt anyone's CryptoKitty. We're only reading the CryptoKitties data, we're not able to actually delete it 😉

## Interacting with other contracts

For our contract to talk to another contract on the blockchain that we don't own, first we need to define an **interface**.

Let's look at a simple example. Say there was a contract on the blockchain that looked like this:

```
contract LuckyNumber {
  mapping(address => uint) numbers;

  function setNum(uint _num) public {
    numbers[msg.sender] = _num;
  }

  function getNum(address _myAddress) public view returns (uint) {
    return numbers[_myAddress];
  }
}
```

This would be a simple contract where anyone could store their lucky number, and it will be associated with their Ethereum address. Then anyone else could look up that person's lucky number using their address.

Now let's say we had an external contract that wanted to read the data in this contract using the `getNum` function.

First we'd have to define an **interface** of the `LuckyNumber` contract:

```
contract NumberInterface {
  function getNum(address _myAddress) public view returns (uint);
}
```

Notice that this looks like defining a contract, with a few differences. For one, we're only declaring the functions we want to interact with — in this case `getNum` — and we don't mention any of the other functions or state variables.

Secondly, we're not defining the function bodies. Instead of curly braces (`{` and `}`), we're simply ending the function declaration with a semi-colon (`;`).

So it kind of looks like a contract skeleton. This is how the compiler knows it's an interface.

By including this interface in our dapp's code our contract knows what the other contract's functions look like, how to call them, and what sort of response to expect.

We'll get into actually calling the other contract's functions in the next lesson, but for now let's declare our interface for the CryptoKitties contract.
