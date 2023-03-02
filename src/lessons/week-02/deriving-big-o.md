# Deriving Big-O Expressions

In the previous lesson, we saw how we could derive the big-O running time for an algorithm by count the number of operations that it performs (simplified to comparisons and moves, for a sorting algorithm specifically).

However, this technique for deriving big-O expressions is not always possible. It may not be clear how many operations the algorithm performs; luckily, we had a closed-form expression for the number of comparisons that selection sort makes, but that may not be the case for the next algorithm that we analyze. Also, the number of operations an algorithm takes may change depending on the contents of the input -- a case that we will come back to.

In this lesson, we will learn some rules of thumb for deriving the big-O notation of algorithms by inspecting the numberand nature of *loops* (i.e., `for` loops, `while` loops) in the algorithm.

But why loops? We focus our analysis on the presence of loops because loops are one\* of the most common techniques for iterating over the input to an algorithm. A loop over the entire input of size `n` already guarantees that your algorithm is performing at least `O(n)` operations!

> \*The other main technique for doing so, *recursion*, will be discussed starting next week.

## Loops up to `n`

Probably the simplest case for this type of analysis is when you have a loop that iterates according to some expression involving `n`. For example, this algorithm is `O(n)`:

```python
def print_lst(lst):
    n = len(lst)
    for i in range(n):
       print(lst[i])
```

Remember that the algorithm doesn't have to iterate over *all* `n` items in order to be `O(n)`. Since lower order terms and coefficients are ignored for the purposes of big-O, we would have an algorithm like this:

```python
def my_strange_algorithm(lst):
    n = len(lst)
    for i in range(n / 1000000):
        print(lst[i])
```

`my_strange_algorithm()` is also `O(n)`, since for sufficiently large values of `n` the coefficient `1 / 1000000` will not matter.

Note that this same kind of analysis applies to `while` loops as well, as long as the number of iterations is on the order of the size of the input:

```python
def print_lst(lst):
    i = 0
    while i < len(lst):
        print(lst[i])
```

Other operations inside of the loop, including operations that would cause the algorithm to end, do not generally affectthe big-O expression either. For example, the following algorithm is still `O(n)`:

```python
def another_algorithm(lst):
    for i in range(5, len(lst) - 10):
        if lst[i] % 2 == 0:
            print(lst[i])
        else:
            return
```

## Loops up to a constant value

Some loops do not iterate with respect to the size of the input list. For example, you might have an algorithm like the following:

```python
def print_first_three(lst):
    for i in range(3):
       print(lst[i])
```

No matter what the size of the input list is -- could be five elements, or one million -- this function will only ever perform three iterations. Therefore, this algorithm is constant time: O(1).

## Back-to-back loops

Sometimes, algorithms contain loops that are in *serial*, or "back-to-back". When this happens, the operations add together. For example:

```python
def serial_loops(lst):
    for i in range(len(lst)):
        print(lst[i])

    for i in range(0, len(lst), -1):
        print(lst[i])
```

The first `for` loop, which prints the list, is `O(n)`. The second loop, which prints the list backwards, is also `O(n)`. Putting these two together, `O(n) + O(n) = O(2 * n) = O(n)`.

## Nested loops

If loops are composed in a *nested* fashion, the number of operations are multiplied, and therefore the running times are multiplied. For example, consider these nested loops:

```python
def nested_loops(lst):
    for i in range(len(lst)):
        for j in range(len(lst) - 5):
            if i < j:
                print(lst[i])
```

In this case, for every one iteration of the outer (`i`) loop, the inner (`j`) loop iterates `O(n)` times. The outer loop itself iterates `O(n)` times. Therefore, the `if` statement inside of the nested loops is evaluated `O(n) * O(n) = O(n^2)` times.

A couple of things to note:

* Strictly speaking, the inner loop iterates exactly `n - 5` times. This is `O(n)`.
* Conditional statements (`if i < j`) doesn't have any effect on the running time. For the purposes of big-O, you are concerned with the worst case behavior, so we will assume (even if it's not true) that `i < j` is always true and the body of the `if` is executed on every iteration.

However, it could also be the case that the inner loop looks slightly different:

```python
def nested_loops_2(lst):
    for i in range(len(lst)):
        for j in range(i):
            print(j)
```

Notice that the inner loop iterates up to `i`, the index of of the outer loop. What's the big-O notation of the algorithm now? Let's count the number of iterations of the inner loop to find out.

* On the 1st iteration of the outer loop (when `i` equals 0), the inner loop will iterate 0 times.
* On the 2nd iteration of the outer loop (when `i` equals 1), the inner loop will iterate 1 times.
* On the 3rd iteration of the outer loop (when `i` equals 2), the inner loop will iterate 2 times.
* On the final iteration of the outer loop (when `i` equals `n` - 1), the inner loop will iterate 1 time.

Therefore the total number of times the statements in the inner loop will be executed will be equal to the sum of the integers from 1 to `n` - 1. We know from our analysis of the number of comparisons in selection sort that this sum is equal to `n(n - 1)/2`, or n<sup>2</sup>/2 - n/2. This means that `nested_loops_2()` is `O(n^2)`!

<aside>
<b>Check your understanding</b>
<p>Consider the following function:</p>
<code>
def mystery_function(lst):
    total = 0
    for i in range(len(lst)):
        if i % 2 == 0: # i is even
            total += 2 * lst[i]

    for i in range(len(lst)):
        for j in range(100):
            if i < j + 1:
                total -= j

    return total
</code>
<p>What is the big-O running time of the function?</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b>The first <code>for</code> loop has a running time of <code>O(n)</code>, since the loop bound is some function of the size of the list (<code>n</code>). The second loop is <i>also</i> <code>O(n)</code>, since the outer loop is <code>O(n)</code> and the inner loop is <code>O(1)</code>. Our expression for the big-O running time is therefore <code>O(n) + O(n)\*O(1)</code></p>, which is <code>O(n)</code>.
</details>
</aside>

## Loops containing functions

When deriving the big-O notation by inspecting loops, you must take into the account the running time of any functions nested *inside* the loops as well. For example, it might be tempting to think of this function as `O(n^2)`:

```python
def nested_loops_func(lst):
    for i in range(len(lst)):
        for j in range(len(lst)):
            x = some_function(i, j)
            print(x)
```

However, we must also consider the running time of `some_function()`! Say that it is implemented as the following:

```python
def some_function(times, factor):
    total = 0
    for k in range(times):
        total += factor
    return total
```

It turns out that `some_function()` is `O(n)` itself. Therefore, nesting it inside of two nested loops makes `nested_loop_func()` `O(n^3)` overall.

## Loops on different inputs

Finally, it's worth noting that when an algorithm has multiple inputs, we use different symbols to represent their runtimes. For example, this function has two inputs:

```python
def multiple_inputs(lst1, lst2):
    for item in lst1:
        print(item)

    for item in lst2:
        print(item)
```

Since we don't know if `lst1` and `lst2` have the same lengths, we can't use `n` to represent the length of both of them. Instead, we can use `n` to represent the size of `lst1`, and `m` to represent the size of `lst2`. Therefore, this algorithm has a running time of `O(n + m)`.

## Summary

Here's a video that summarizes big-O notation and some of the techniques discussed above:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/watch?v=v4cd1O4zkGw"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>
