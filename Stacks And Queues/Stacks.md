## Stacks

#### Q:What is a stack ? 

**Answer**:A stack is an ordered collection of elements where elements are only added and removed from the same end .

Example of stack 

1. Stack of plates in a kitchen 
2. History of our current browsers tab 

Another Term used to describe stacks is **LIFO** which stands for Last in , first out .The last(most recent) element placed is the first element to come out.

#### Q:What are the operations  we can perform on a stack ?

**Answer**: The following operations can be performed on a stack 

1. Pushing -> inserting into a stack
2. Popping -> removing from a stack
3. Peek -> looking at the element at the top of the stack 

#### Q:How can we implement a stack ? 

**Answer**:Using a dynamic array is the most common and easiest way to inplement a stack .Sometimes a stack may be implemented with a Linked List with a tail pointer 

Implementing a stack using a dynamic array => 

```js
// Declaration: we will just use a list
let stack = [];

// Pushing elements:
stack.push(1);
stack.push(2);
stack.push(3);

// Popping elements:
stack.pop(); // 3
stack.pop(); // 2

// Check if empty:
!stack.length; // false

// Check element at top
stack[stack.length - 1]; // 1

// Get size
stack.length; // 1


```

####  Q:Time complexity of stack operations 

**Answer**:If we implement a stack using an array (dynamic array) then the time complexity of our stack is same as that of a dynamic array .O(1) push , pop and random access and O(n) search 