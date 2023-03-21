# Fibonacci Sequence

One classic example of a problem that can be solved using recursion is the computation of the Fibonacci sequence. The Fibonacci sequence is a series of numbers in which each number is the sum of the two preceding ones, starting from 0 and 1. The sequence can be expressed mathematically as follows:

```
fib(0) = 0
fib(1) = 1
fib(n) = fib(n-1) + fib(n-2)  for n > 1
```

For example, the first 10 terms of the Fibonacci sequence are:

```
0, 1, 1, 2, 3, 5, 8, 13, 21, 34
```

The Fibonacci sequence is significant in mathematics and computer science because it is a ubiquitous example of a recursive sequence, and is often found in natural phenomena such as the growth patterns of plants. The sequence also exhibits a wide range of interesting mathematical properties, such as the golden ratio, which has many applications in art, architecture, and design.

Watch the following video to learn more about how the Fibonacci sequence appears in many aspects of our world:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/2tv6Ej6JVho"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

## Implementing Fibonacci

Based on the mathematical definition of the Fibonacci sequence above, try writing a recursive function that implements the nth Fibonacci number. Don't forget the base case(s)!<br>

<iframe src="https://trinket.io/embed/python3/b6d5365430" width="100%" height="356" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>

When satisfied with your effort at writing the function, watch the following video to see one potential solution:

<details>
<summary>
<i>Click to reveal the video.</i>
</summary>
<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/urPVT1lymzU"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>
</details>

Note the example at the end of the video, which shows that it seems to take many function calls to calculate even a small Fibonacci number, such as `fibonacci(6)`. Let's take a closer look at the efficiency of the recursive implementation of the Fibonacci function in the next lesson.
