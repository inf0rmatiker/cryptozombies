# ERC721 Token Transfers- Two Step Scenario

Now, the `approve` followed by `transferFrom` way to transfer ERC721 tokens is far from being a walk in the park but I'm here to help.

In a nutshell, we have to test two different scenarios:

- Alice approves Bob to take the ERC721 token. Then, Bob (the approved address) calls `transferFrom`.

- Alice approves Bob to take the ERC721 token. Next, Alice transfers the ERC721 token.

The difference in the two scenarios lies with who calls the actual transfer, Alice or Bob.

We've made it look simple, right?

Let's take a look at the first scenario.

## Bob calls `transferFrom`

The steps for this scenario are as follows:

- Alice creates a new ERC721 token and then calls `approve`.
- Next, Bob runs `transferFrom` which should make him the owner of the EC721 token.
- Finally, we have to call `assert.equal` with `newOwner` and `bob` as parameters.
