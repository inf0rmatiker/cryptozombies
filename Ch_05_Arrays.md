# Arrays
When you want a collection of something, you can use an array. There are two types of arrays in Solidity: **fixed** arrays and **dynamic** arrays:

```
// Array with a fixed length of 2 elements:
uint[2] fixedArray;
// another fixed Array, can contain 5 strings:
string[5] stringArray;
// a dynamic Array - has no fixed size, can keep growing:
uint[] dynamicArray;
```

You can also create an array of **structs**. Using the previous chapter's `Person` struct:

```
Person[] people; // dynamic Array, we can keep adding to it
```

Remember that state variables are stored permanently in the blockchain? So creating a dynamic array of structs like this can be useful for storing structured data in your contract, kind of like a database.

## Public Arrays
You can declare an array as `public`, and Solidity will automatically create a **getter** method for it. The syntax looks like:

```
Person[] public people;
```

Other contracts would then be able to read from, but not write to, this array. So this is a useful pattern for storing public data in your contract.
