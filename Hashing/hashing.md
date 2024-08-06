## Hashing 

A data structure is a format for organizing data in an efficient way. We can split data structures into two things: the interface and the implementation.

The interface is like a contract that specifies how we can interact with the data structure – what operations we can perform on it, what inputs it expects, and what outputs we can expect.

For example, consider an array in JavaScript. The interface would include operations like appending, insertion, updating, and more. These operations are well-defined and have specific values that we must follow when we use them. If we want to append an element to an array, we use the built-in method like `push()`, passing in the element we want to add as an argument. This operation returns the new length of the array.

The implementation is the code that actually makes the data structure work. This is where the details of how the data is stored and how the operations are performed come into play. For example, the implementation of an array in JavaScript involves allocating memory for the array, tracking the size, and rearranging the elements when an operation like `pop()` is called.

For many data structures, the implementation can be quite complex, involving intricate algorithms and data manipulation. 

 All major  data structures have built-in implementations in javascript. In an interview, it is expected that we know how to use the  built-in data structures, but we wouldn't be asked to implement them  ourself.

------

In this chapter, we are going to talk about hash maps and sets, which are implemented using [hashing](https://en.wikipedia.org/wiki/Hash_function).

A hash function is a function that takes an input and  deterministically converts it to an integer that is less than a fixed  size set by the programmer. Inputs are called **keys** and  the same input will always be converted to the same integer. Here's an  example hash algorithm for a string containing letters of the English  alphabet ( lets say the fixed size we want to set is `x` ):

1. Declare an integer `total`.
2. Iterate over the string. For each character, convert it to its position in the alphabet. For example, `a -> 1`, `c -> 3`, `z -> 26`.
3. Take that value, and multiply it by the current position in the string (index + 1). Add this to `total`. For example, given the string `"abc"`, the `b` is at position `2` in the alphabet and position `2` in the string, so it would contribute `2 * 2 = 4` towards `total`.
4. After going through every character, `total % x` is the converted value.

This algorithm  is just an  example of how one could convert strings into integers.  The final converted value will be in the range `[0, x - 1]`.

------

### What is the point of a hash function?

We know that arrays have O(1) random access. Given an arbitrary index, we can access and update its  value in the array in constant time. The main constraint with arrays is  that they are a fixed size, and the indices have to be integers. Because hash functions can convert any input into an integer, we can  effectively remove the constraint of indices needing to be integers.  When a hash function is combined with an array, it creates a **hash map**, also known as a **hash table** or **dictionary**.

With arrays, we **map** indices to values. With hash maps, we map **keys** to values, and a key can be almost anything. 

A hash map  is extremely powerful and allows us to reduce the  time complexity of an algorithm by a factor of O(n) for a huge amount of problems. Javascript has a [built-in implementation of a hash map](https://en.wikipedia.org/wiki/Hash_table#Implementations),  they're called `maps` and declaring one is as simple as `map =new Map()`. .

To summarize, a hash map is an unordered data structure that stores key-value pairs. A hash map can add and remove elements in O(1), as well as update values associated with a key and check if a key exists, also in O(1).When we iterate over the keys, values of a `Map`  they will be returned in the order in which they were inserted.

> An ordered data structure is one where the insertion order is  "remembered". An unordered data structure is one where the insertion  order is not relevant.

------

### Comparison with arrays

In terms of time complexity, hash maps blow arrays out of the water. The following operations are all O(1) for a hash map:

- Add an element and associate it with a value
- Delete an element if it exists
- Check if an element exists

A hash map also has many of the same useful properties as an array with the same time complexity:

- Find length/number of elements
- Updating values
- Iterate over elements

> Hash maps are also just easier/cleaner to work with. Even if your  keys are integers and you could get away with using an array, if you  don't know what the max size of your key is, then you don't know how  large you should size your array. With hash maps, you don't need to  worry about that, since the key will be converted to a new integer  within the size limit anyways.

However, from a practical perspective, there are some disadvantages  to using hash maps, and it's important to know them as it is common in  interviews to talk about tradeoffs.

The biggest disadvantage of hash maps is that for smaller input  sizes, they can be slower due to overhead. Because big O ignores  constants, the O(1) time complexity can sometimes be deceiving - it's usually something more like O(10) because every key needs to go through the hash function, and there can also be **collisions**, which we will talk about in the next section.

Hash tables can also take up more space. Dynamic arrays are actually  fixed-size arrays that resize themselves when they go beyond their  capacity. Hash tables are also implemented using a fixed size array -  remember that the size is a limit set by the programmer. The problem is, resizing a hash table is much more expensive because every existing key needs to be re-hashed, and also a hash table may use an array that is  significantly larger than the number of elements stored, resulting in a  huge waste of space. Let's say you chose your limit as 10,000 items, but you only end up storing 10. Okay, you could argue that 10,000 is too  large, but then what if your next test case ends up needing to store  100,000 elements? The point is, when you don't know how many elements  you need to store, arrays are more flexible with resizing and not  wasting space.

> Note: remember that time complexity functions only involve the variables you define. When we say that hash map operations are O(1), the variable we are concerned with is usually n, which is the size of the hash map. However, this may be misleading. For example, hashing a string requires O(m) time, where m is the length of the string. The constant time operations are only constant **relative to the size of the map**.