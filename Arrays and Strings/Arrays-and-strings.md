##   Arrays and strings

In terms of algorithm problems, arrays (1D) and strings are very  similar: they both represent an ordered group of elements.

"Array" can mean something different between languages. Javascript uses  dynamic arrays by default . Initialization is as easy as `arr = []`, and you don't  need to worry about the type of data you store in the list or the size  of the list. Other languages like C++ require you to specify the size  and data type of the array during initialization, but also have support  for lists (like `std::vector` in C++).

> Technically, an array can't be resized. A dynamic array, or list, can be.

Similarly, strings are implemented differently between languages. In  Javascript , they are immutable. In C++, they are mutable.

> Mutable: a type of data that can be changed. Immutable: A type of  data that cannot be changed. If you want to change something immutable,  you will need to recreate the entire thing.

Why should we care about something being mutable or immutable? If you have a mutable array `arr = ["a", "b", "c"]` and an immutable string `s = "abc"`, but you want to instead represent `"abd"`, you can easily do `arr[2] = "d"`, but you cannot do `s[2] = "d"`. As such, if you wanted the string `s = "abd"`, you would need to create it entirely from scratch. With such a small  string, it's not a big deal. But sometimes you are dealing with strings  with 100,000 characters, so creating new versions just to modify one  character is very expensive (O(n)O(n), where nn is the size of the string).

![time-complexity-arrays-strings](../assets/time-complexity-arrays-strings.png)

> - Appending to the end of a list is [amortized O(1)](https://stackoverflow.com/questions/33044883/why-is-the-time-complexity-of-pythons-list-append-method-o1).