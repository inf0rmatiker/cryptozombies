# Zombie DNA

Let's finish writing the `feedAndMultiply` function.

The formula for calculating a new zombie's DNA is simple: the average between the feeding zombie's DNA and the target's DNA.

For example:

```
function testDnaSplicing() public {
  uint zombieDna = 2222222222222222;
  uint targetDna = 4444444444444444;
  uint newZombieDna = (zombieDna + targetDna) / 2;
  // ^ will be equal to 3333333333333333
}
```

Later we can make our formula more complicated if we want to, like adding some randomness to the new zombie's DNA. But for now we'll keep it simple — we can always come back to it later.
