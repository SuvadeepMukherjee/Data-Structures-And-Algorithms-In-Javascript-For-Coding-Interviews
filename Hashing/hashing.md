## Hashing 

Before we start this chapter, let's quickly talk about data structures.

A data structure is a format for organising data in a efficient way , we can split data structures into 2 things: the interface and the implementation 

The interface is like a contract that specifies how we can interact with the data structure -what operations we can perform on it , what inputs it expects and what outputs we can expect 

For example , consider a dynamic array ,The interface would include operations like appending, insertion,updating and more . These operations are well defined and have specific value that we must follow when we use them .If we want to append an element to an array , we use the built in method like `push()` while passing in the element we want to add as an argument .This operation returns the new length of the array 

The implementation is the code that actually makes the data structure work .This is where the details of how the data os stored and how the operations are performed come into play .For example the implementation of a  array in javascript  might involve allocating memory for the array , tracking the size and rearranging the elements when an operation like `pop()` is called 

For many data structures the implemenatation can be quite complex , involving intricate algorithms and data manipulation .However we dont need to worry about these detals , we only need to understand the interface and how to use it properly  