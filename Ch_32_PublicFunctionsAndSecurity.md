# Public Functions & Security

Now let's modify `feedAndMultiply` to take our cooldown timer into account.

Looking back at this function, you can see we made it `public` in the previous lesson. An important security practice is to examine all your `public` and `external` functions, and try to think of ways users might abuse them. Remember — unless these functions have a modifier like `onlyOwner`, any user can call them and pass them any data they want to.

Re-examining this particular function, the user could call the function directly and pass in any `_targetDna` or `_species` they want to. This doesn't seem very game-like — we want them to follow our rules!

On closer inspection, this function only needs to be called by `feedOnKitty()`, so the easiest way to prevent these exploits is to make it `internal`.
