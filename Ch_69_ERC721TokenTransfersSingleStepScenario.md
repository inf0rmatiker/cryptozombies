# ERC721 Token Transfers- Single Step Scenario

So far we’ve merely been warming up...

But now it's time to really show off what you know!

In the next chapters, we're going to be putting what we’ve learned together and test something really cool.

To begin with, we're going to be testing the scenario in which Alice transfers her ERC721 token to Bob, in a single step.

Here is what our test should do:

Create a new zombie for Alice (Remember that a zombie is nothing more than an ERC721 token).

Make it so that Alice transfers her ERC721 token to Bob.

At this point, Bob should own the ERC721 token. If so, `ownerOf` would return a value that is equal to Bob's address.

Let's wrap it up by checking if Bob is the `newOwner`, inside an `assert`.
