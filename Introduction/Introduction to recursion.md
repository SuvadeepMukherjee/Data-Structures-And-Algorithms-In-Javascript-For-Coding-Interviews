## Introduction to recursion

Recursion is a problem solving method. In code, recursion is implemented using a function that calls itself.

The opposite of a recursive algorithm would be an iterative algorithm. There [is a branch](https://en.wikipedia.org/wiki/Computability_theory) of study that proves that any iterative algorithm can be written  recursively. While iterative algorithms use for loops and while loops to simulate repetition, recursive algorithms use function calls to  simulate the same logic.

Let's say that we wanted to print the numbers from 1 to 10. Here's equivalent javascript code  for an iterative algorithm:

```js
for (let i = 1; i <= 10; i++) {

  console.log(i);

}
```

Here's some pseudocode for an equivalent recursive algorithm:

```js
function fn(i) {
  console.log(i);
  fn(i + 1);
  return;
}
fn(10);
```

Each call to `fn` first prints `i` (which starts at 1), and then calls `fn` again, but incrementing `i` (to print the next number).

> The first function call prints `1`, then calls `fn(2)`. In `fn(2)`, we print `2`, then call `fn(3)`, and so on.

However, this code is actually wrong.  The  function calls will never stop! Running this code would print natural  numbers (positive integers) infinitely (or until the Maximum call stack size exceeded). The `return` line never gets reached because `fn(i + 1)` comes before it.

We need what is called a **base case** to make the recursion stop. Base cases are conditions at the start of recursive functions that terminate the calls.

```js
function fn(i) {
  if (i > 10) return;
  console.log(i);
  fn(i + 1);
  return;
}
fn(1);
```

> After we call `fn(10)`, we print `10` and call `fn(11)`. In the `fn(11)` call, we trigger the base case and return. So now we are back in the call to `fn(10)` and move to the next line, which is the return statement. This makes us return back to the `fn(9)` call and so on, until we eventually return from the `fn(1)` call and the algorithm terminates.

An important thing to understand about recursion is the order in which  the code runs - the order in which the computer executes instructions.  With an iterative program, it's easy - start at the top, and go line by  line. With recursion, it can get confusing because calls can cascade on  top of each other. Let's print numbers again, but this time only up to  3. Let's also add another print statement and number the lines: