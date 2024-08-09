##   Arrays and strings

Arrays and Strings represent an ordered group of elements

Javascript uses dynamic arrays (An array cannot be resized .A dynamic array can be resized)

Strings are immutable in javascript 

Why should we care about something being mutable or immutable? If you have a mutable array `arr = ["a", "b", "c"]` and an immutable string `s = "abc"`, but you want to instead represent `"abd"`, you can easily do `arr[2] = "d"`, but you cannot do `s[2] = "d"`. As such, if you wanted the string `s = "abd"`, you would need to create it entirely from scratch

Complexity of array and string operations:-

![time-complexity-arrays-strings](../assets/time-complexity-arrays-strings.png)

> - Appending to the end of an array is [amortized O(1)](https://stackoverflow.com/questions/33044883/why-is-the-time-complexity-of-pythons-list-append-method-o1).