## Hashing 

Before we start this chapter, let's quickly talk about data structures.

A data structure is a format for organizing data in an efficient way. We can split data structures into two things: the interface and the implementation.

The interface is like a contract that specifies how we can interact with the data structure – what operations we can perform on it, what inputs it expects, and what outputs we can expect.

For example, consider an array in JavaScript. The interface would include operations like appending, insertion, updating, and more. These operations are well-defined and have specific values that we must follow when we use them. If we want to append an element to an array, we use the built-in method like `push()`, passing in the element we want to add as an argument. This operation returns the new length of the array.

The implementation is the code that actually makes the data structure work. This is where the details of how the data is stored and how the operations are performed come into play. For example, the implementation of an array in JavaScript involves allocating memory for the array, tracking the size, and rearranging the elements when an operation like `pop()` is called.

For many data structures, the implementation can be quite complex, involving intricate algorithms and data manipulation. However, we don't need to worry about these details; we only need to understand the interface and how to use it properly.

For many data structures, the implementation can be quite complex,  involving intricate algorithms and data manipulation. However we don't  need to worry about those details - we only need to understand the  interface and how to use it properly.

In this article and a few others in the course, we will talk about  the underlying implementation details behind a data structure. While it  does help to have a basic understanding, don't worry too much about  memorizing these details. It is  included  for completeness.

The more important thing is to understand the interface. All major  data structures have built-in implementations in javascript. In an interview, it is expected that you know how to use the  built-in data structures, but you wouldn't be asked to implement them  yourself.

------

In this chapter, we are going to talk about hash maps and sets, which are implemented using [hashing](https://en.wikipedia.org/wiki/Hash_function).

A hash function is a function that takes an input and  deterministically converts it to an integer that is less than a fixed  size set by the programmer. Inputs are called **keys** and  the same input will always be converted to the same integer. Here's an  example hash algorithm for a string containing letters of the English  alphabet ( lets say the fixed size we want to set is `x` :

1. Declare an integer `total`.
2. Iterate over the string. For each character, convert it to its position in the alphabet. For example, `a -> 1`, `c -> 3`, `z -> 26`.
3. Take that value, and multiply it by the current position in the string (index + 1). Add this to `total`. For example, given the string `"abc"`, the `b` is at position `2` in the alphabet and position `2` in the string, so it would contribute `2 * 2 = 4` towards `total`.
4. After going through every character, `total % x` is the converted value.

This algorithm isn't actually a good hash function but is just an  example of how one could convert strings into integers.  The final converted value will be in the range `[0, x - 1]`.