# Use Truffle with Loom!

It might not seem much, but you just deployed the CryptoZombies smart contract!

Even if Truffle helped a lot, this is no small feat, so pat yourself on the back.

## Loom Basechain

Now, if you want to build DApps on Ethereum, there's one thing you should be aware of - on the main net, users are required to pay gas fees for every transaction. But this isn't ideal for a user-facing DApp or a game. It can easily ruin the user experience.

Conversely, on Loom, your users can have much speedier and gas-free transactions, making it a much better fit for games and other non-financial applications.

This means that your Loom zombies will be fast zombies!

That's not all - deploying to Loom is no different from deploying to Rinkeby, or to the Ethereum main net. If you know how to do one, you also know how to do the other.

In the next chapters, we'll be walking you through deploying to Loom.

## `loom-truffle-provider`

We at Loom are using Truffle to build, test, and deploy our smart contracts. To make our life easier, we developed something called a provider that lets Truffle deploy to Loom just like it deploys to Rinkeby or Ethereum main net.

Without delving too much into details, the provider works like a bridge that makes Web3 calls compatible with Loom. The beauty of it is that, to use it, you don't have to understand how it works under the hood.

## Put it to the test:

We've made `loom-truffle-provider` available as an `npm` package. Let's install it.

> Note: This time, there's no need to make the package available globally.
