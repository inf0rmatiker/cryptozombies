# Zombie Modifiers

Now let's use our `aboveLevel` modifier to create some functions.

Our game will have some incentives for people to level up their zombies:

For zombies level 2 and higher, users will be able to change their name.
For zombies level 20 and higher, users will be able to give them custom DNA.
We'll implement these functions below. Here's the example code from the previous lesson for reference:

```
// A mapping to store a user's age:
mapping (uint => uint) public age;

// Require that this user be older than a certain age:
modifier olderThan(uint _age, uint _userId) {
  require (age[_userId] >= _age);
  _;
}

// Must be older than 16 to drive a car (in the US, at least)
function driveCar(uint _userId) public olderThan(16, _userId) {
  // Some function logic
}
```

> Note: `calldata` is somehow similar to `memory`, but it's only available to `external` functions.
