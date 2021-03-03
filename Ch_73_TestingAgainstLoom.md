# Testing Against Loom

Impressive! You must have been practicing.

Now, this tutorial would not be complete without showing you how to test against **Loom Testnet**.

Recall from our previous lessons that, on **Loom**, users have access to much speedier and gas-free transactions than on Ethereum. This makes DAppChains a much better fit for something like a game or a user-facing DApp.

And you know what? Deploying and testing against Loom is not different at all. We've gone ahead and summed up what needs to be done so you can test against **Loom**. Let's have a quick look.

## Configure Truffle for Testing on Loom

First things first. Let's tell Truffle how to deploy to Loom Testnet by placing the following snippet inside the `networks` object.

```
    loom_testnet: {
      provider: function() {
        const privateKey = 'YOUR_PRIVATE_KEY';
        const chainId = 'extdev-plasma-us1';
        const writeUrl = 'wss://extdev-basechain-us1.dappchains.com/websocket';
        const readUrl = 'wss://extdev-basechain-us1.dappchains.com/queryws';
        return new LoomTruffleProvider(chainId, writeUrl, readUrl, privateKey);
      },
      network_id: 'extdev'
    }

```

> Note: Never reveal your private key! We are only doing this for the sake of simplicity. A much safer solution would be to save your private key into a file and read its value from that file. If you do this, make sure you avoid pushing the file in which you saved your private key to GitHub, where anyone can see it.

## The accounts array

In order to make Truffle "talk" to Loom we've replaced the default `HDWalletProvider` with our own [Truffle Provider](https://github.com/loomnetwork/loom-truffle-provider). As a result, we have to tell our provider to fill in the accounts array so we can test our game. In order to do that, we are required to replace the line of code that `return`s a new `LoomTruffleProvider`:

```
return new LoomTruffleProvider(chainId, writeUrl, readUrl, privateKey)
```

with this:

```
const loomTruffleProvider = new LoomTruffleProvider(chainId, writeUrl, readUrl, privateKey);
loomTruffleProvider.createExtraAccountsFromMnemonic(mnemonic, 10);
return loomTruffleProvider;
```
