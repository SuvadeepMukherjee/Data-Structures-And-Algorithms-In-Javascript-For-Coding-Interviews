## Two Pointers

Two pointers involves having two integer variables that both  move along an iterable. 

There are several ways to implement two pointers. To start, let's look at the following method:

> Start the pointers at the edges of the input. Move them towards each other until they meet.

Converting this idea into instructions:

1. Start one pointer at the first index `0` and the other pointer at the last index `input.length - 1`.
2. Use a while loop until the pointers are equal to each other.
3. At each iteration of the loop, move the pointers towards each other. This means either increment the pointer that started at the first  index, decrement the pointer that started at the last index, or both.  Deciding which pointers to move will depend on the problem we are trying to solve.

Here's some pseudocode illustrating the concept:

```
function fn(arr):
    left = 0
    right = arr.length - 1

    while left < right:
        Do some logic here depending on the problem
        Do some more logic here to decide on one of the following:
            1. left++
            2. right--
            3. Both left++ and right--
```

The strength of this technique is that we will never have more than O(n) iterations for the while loop because the pointers start n away from each other and move at least one step closer in every  iteration. Therefore, if we can keep the work inside each iteration at O(1), this technique will result in a linear runtime, which is usually the best possible runtime. Let's look at some examples.

------

> Example 1: Given a string `s`, return `true` if it is a palindrome, `false` otherwise.
>
> A string is a palindrome if it reads the same forward as backward.  That means, after reversing it, it is still the same string. For  example: "abcdcba", or "racecar".
>     

```js
var checkIfPalindrome = function (s) {
  let left = 0;
  let right = s.length - 1;
  while (left < right) {
    if (s[left] != s[right]) {
      return false;
    }

    left++;
    right--;
  }

  return true;
};

```
Time Complexity : O(n) , The time complexity is O(n) because the while loop iterations cost O(1) each, and there can never be more than O(n) iterations of the while loop - the pointers start at a distance of n from each other and move closer by one step each iteration.

Space Complexity : O(1) , No matter how big the input is, we always only use two integer variables

------

> Example 2: Given a **sorted** array of unique integers and a target integer, return `true` if there exists a pair of numbers that sum to target, `false` otherwise. This problem is similar to [Two Sum](https://leetcode.com/problems/two-sum/). (In Two Sum, the input is not sorted).
>
> For example, given `nums = [1, 2, 4, 6, 8, 9, 14, 15]` and `target = 13`, return true because `4 + 9 = 13`.    

```js
var checkForTarget = function(nums, target) {
    let left = 0;
    let right = nums.length - 1;
    
    while (left < right) {
        // curr is the current sum
        let curr = nums[left] + nums[right];
        if (curr == target) {
            return true;
        }
        
        if (curr > target) {
            right--;
        } else {
            left++;
        }
    }
```

Like in the previous example, this algorithm uses O(1) space and has a time complexity of O(n)

### Another way to use two pointers

> Move along both inputs simultaneously until all elements have been checked.

Converting this idea into instructions:

1. Create two pointers, one for each iterable. Each pointer should start at the first index.
2. Use a while loop until one of the pointers reaches the end of its iterable.
3. At each iteration of the loop, move the pointers forward. This means incrementing either one of the pointers or both of the pointers.  Deciding which pointers to move will depend on the problem we are trying to solve.
4. Because our while loop will stop when one of the pointers reaches  the end, the other pointer will not be at the end of its respective  iterable when the loop finishes. Sometimes, we need to iterate through  all elements - if this is the case, you will need to write extra code  here to make sure both iterables are exhausted.

Here's some pseudocode illustrating the concept:

```
function fn(arr1, arr2):
    i = j = 0
    while i < arr1.length AND j < arr2.length:
        Do some logic here depending on the problem
        Do some more logic here to decide on one of the following:
            1. i++
            2. j++
            3. Both i++ and j++

    // Step 4: make sure both iterables are exhausted
    // Note that only one of these loops would run
    while i < arr1.length:
        Do some logic here depending on the problem
        i++

    while j < arr2.length:
        Do some logic here depending on the problem
        j++
```

Similar to the first method we looked at, this method will have a linear time complexity of O(n+m) if the work inside the while loop is O(1), where `n = arr1.length` and `m = arr2.length`. This is because at every iteration, we move at least one pointer forward, and the pointers cannot be moved forward more than `n + m` times without the arrays being exhausted. Let's look at some examples..

------

> Example 3: Given two sorted integer arrays `arr1` and `arr2`, return a new array that combines both of them and is also sorted.

​    
```js
var combine = function (arr1, arr2) {
  // ans is the answer
  let ans = [];
  let i = 0,
    j = 0;
  while (i < arr1.length && j < arr2.length) {
    if (arr1[i] < arr2[j]) {
      ans.push(arr1[i]);
      i++;
    } else {
      ans.push(arr2[j]);
      j++;
    }
  }

  while (i < arr1.length) {
    ans.push(arr1[i]);
    i++;
  }

  while (j < arr2.length) {
    ans.push(arr2[j]);
    j++;
  }

  return ans;
};

```
------

> Example 4: [392. Is Subsequence](https://leetcode.com/problems/is-subsequence/).
>
> Given two strings `s` and `t`, return `true` if `s` is a subsequence of `t`, or `false` otherwise.
>
> A subsequence of a string is a sequence of characters that can be  obtained by deleting some (or none) of the characters from the original  string, while maintaining the relative order of the remaining  characters. For example, "ace" is a subsequence of "abcde" while "aec"  is not.
>         

```js
 var isSubsequence = function (s, t) {
  let i = 0,
    j = 0;
  while (i < s.length && j < t.length) {
    if (s[i] == t[j]) {
      i++;
    }

    j++;
  }

  return i == s.length;
};

```