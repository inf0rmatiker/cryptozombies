# Withdraws

In the previous chapter, we learned how to send Ether to a contract. So what happens after you send it?

After you send Ether to a contract, it gets stored in the contract's Ethereum account, and it will be trapped there — unless you add a function to withdraw the Ether from the contract.

You can write a function to withdraw Ether from the contract as follows:

```
contract GetPaid is Ownable {
  function withdraw() external onlyOwner {
    address payable _owner = address(uint160(owner()));
    _owner.transfer(address(this).balance);
  }
}
```

Note that we're using `owner()` and `onlyOwner` from the `Ownable` contract, assuming that was imported.

And most important for `_owner` variable that it's have to be a `address payable` type for doing a sending and transferring ether instruction.

But our `owner()` isn't a type `address payable` so we have to explicitly cast to `address payable`. Casting any integer type like `uint160` to address produces an `address payable`.

You can transfer Ether to an address using the `transfer` function, and `address(this).balance` will return the total balance stored on the contract. So if 100 users had paid 1 Ether to our contract, `address(this).balance` would equal 100 Ether.

You can use `transfer` to send funds to any Ethereum address. For example, you could have a function that transfers Ether back to the `msg.sender` if they overpaid for an item:

```
uint itemFee = 0.001 ether;
msg.sender.transfer(msg.value - itemFee);
```

Or in a contract with a buyer and a seller, you could save the seller's address in storage, then when someone purchases his item, transfer him the fee paid by the buyer: `seller.transfer(msg.value)`.

These are some examples of what makes Ethereum programming really cool — you can have decentralized marketplaces like this that aren't controlled by anyone.
