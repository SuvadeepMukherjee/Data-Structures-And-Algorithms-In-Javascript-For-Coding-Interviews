##   Arrays and strings

#### Q1:Javascript uses dynamic Arrays ? Is the above statement correct ? 

**Answer** : Yes , javascript uses dynamic arrays 

#### Q2: Can arrays be resized ? 

**Answer**: Technically an array cannot be resized , dynamic arrays can be resized 

#### Q3:Are strings mutable or immutable ? 

**Answer**: Strings are immutable in javascript 

#### Q4:Are arrays in javascript mutable ? 

**Answer**: Yes arrays are mutable in js 

#### Q5:Why should we care about something being mutable and immutable ? 

**Answer**:if we have a mutable array `arr = ["a", "b", "c"]` and an immutable string `s = "abc"`, but we want to instead represent `"abd"`, we can easily do `arr[2] = "d"`, but we cannot do `s[2] = "d"`. As such, if we wanted the string `s = "abd"`, we would need to create it entirely from scratch. With such a small  string, it's not a big deal. But sometimes we are dealing with strings  with 100,000 characters, so creating new versions just to modify one  character is very expensive (O(n), where n is the size of the string).

#### Q6: Time Complexity of the following operations in arrays and strings 

1. Appending to end
2. Popping from end 
3. Insertion , not from end 
4. Deletion not from end 
5. Modifying an element 
6. Random access
7. Checking if element exists

**Answer**:

![time-complexity-arrays-strings](../assets/time-complexity-arrays-strings.png)

> - Appending to the end of an array is [amortized O(1)](https://stackoverflow.com/questions/33044883/why-is-the-time-complexity-of-pythons-list-append-method-o1).