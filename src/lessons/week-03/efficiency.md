# Recursion and Efficiency

We left off in the last lesson with the observation that when calculating `fibonacci(6)`, it seems to take more recursive function calls than we might have expected. Let's more precisely define the efficiency of the recursive implementationof calculating the nth Fibonacci number.

To help us do so, let's draw a *call tree* -- a diagram that illustrates how the recursive functions are called.

> Insert video drawing call tree of Fibonacci(4).

As illustrated in the video, calculating `fibonacci(4)` required us to call `fibonacci(1)` three times! As we calculate larger and larger Fibonacci numbers, the number of recursive calls that we need to make is going to grow considerably:

| Fibonacci number n | Number of function calls needed |
|--------------------|---------------------------------|
| 3                  | 5                               |
| 4                  | 9                               |
| 5                  | 17                              |
| ...                | ...                             |
| 10                 | 109                             |
| 20                 | 10946                           |
| 30                 | 1346269                         |

As the size of the input (nth Fibonacci number) increases, the number of function calls increases *exponentially* (<code>O(2<sup>n</sup>)</code>).

Since each function call takes constant time to execute (i.e., `O(1)`), the total running time of the recursive implementation of the Fibonacci sequence can be expressed as the product of the number of function calls and the running time per call. This gives a total running time of <code>O(2<sup>n</sup>) * O(1) = O(2<sup>n</sup>)</code>.

This is our first example of an exponential time algorithm. This is *much* slower than any of the algorithms we have seen so far. Before this, the slowest algorithms we had seen were selection sort and insertion sort (in the worst case), which were both <code>O(n<sup>2</sup>)</code>.

## Calculating big-O for recursive functions

When we learned heuristics for computing the big-O notation for loop-based algorithms, we said that you can multiply running times when operations are nested inside of loops. For example:

```python
def print_list(lst):
    for item in lst:
        print(lst)
```

Here, we perform a constant time operation (a print statement) inside of a linear (`O(n)`) loop, so the overall running time is `O(1) * O(n) = O(n)`.

The same principle applies for recursive functions, except instead of counting the number of iterations of a *loop*, we are counting the number of *recursive function calls*. This is because the number of recursive function calls determines the number of times the body of the function is executed.

Consider the following `count_down()` function, which counts down from `n` to 0:

```python
def count_down(n):
    if n <= 0:
        print(n)
    else:
        print(n)
        count(n - 1)
```

How many function calls does `count_down()` make to count down from `n`? We can organize our analysis using another table:

| n | Number of function calls needed |
|---|---------------------------------|
| 1 | 2                               |
| 2 | 3                               |
| 3 | 4                               |
| 4 | 5                               |
|...| ...                             |

It makes exactly `n + 1 = O(n)` function calls to count down from `n` to 0, and each one of those function calls performs a constant number of operations. Therefore, the big-O expression for `count_down(n)` is `O(n)`.

## Summary

The time complexity of a recursive function is determined in part by the number of times a recursive call is made for an input of size `n`. As we've seen, this can lead to running times such as <code>O(2<sup>n</sup>)</code> or `O(n)`. In the near future, we will see examples of recursive functions that run in time `O(logn)` and `O(nlogn)` as well.
