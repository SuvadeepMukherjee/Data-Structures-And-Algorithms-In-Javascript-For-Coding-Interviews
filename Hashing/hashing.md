## Hashing 

Before we start this chapter, let's quickly talk about data structures.

A data structure is a format for organizing data in an efficient way. We can split data structures into two things: the interface and the implementation.

The interface is like a contract that specifies how we can interact with the data structure – what operations we can perform on it, what inputs it expects, and what outputs we can expect.

For example, consider an array in JavaScript. The interface would include operations like appending, insertion, updating, and more. These operations are well-defined and have specific values that we must follow when we use them. If we want to append an element to an array, we use the built-in method like `push()`, passing in the element we want to add as an argument. This operation returns the new length of the array.

The implementation is the code that actually makes the data structure work. This is where the details of how the data is stored and how the operations are performed come into play. For example, the implementation of an array in JavaScript involves allocating memory for the array, tracking the size, and rearranging the elements when an operation like `pop()` is called.

For many data structures, the implementation can be quite complex, involving intricate algorithms and data manipulation. However, we don't need to worry about these details; we only need to understand the interface and how to use it properly.