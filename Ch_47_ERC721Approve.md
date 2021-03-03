# ERC721: Approve

Now, let's implement `approve`.

Remember, with approve the transfer happens in 2 steps:

1. You, the owner, call `approve` and give it the `_approved` address of the new owner, and the `_tokenId` you want him to take.

2. The new owner calls `transferFrom` with the `_tokenId`. Next, the contract checks to make sure the new owner has been already approved, and then transfers him the token.

Because this happens in 2 function calls, we need to use the `zombieApprovals` data structure to store who's been approved for what in between function calls.
