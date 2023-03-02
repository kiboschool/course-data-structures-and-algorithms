# Big-O Notation

We have now reached the point where we are ready to develop a formalism for classifying algorithms according to their time and space efficiencies. This formalism is known as *big-O notation*.

## What is big-O notation?

Big-O notation can be used to describe an algorithm's time and space efficiciency. It describes an upper bound on the amount of resources that will be required for the algorithm as the input size to the algorithm increases.

Watch the video below to learn about big-O notation and to hear an example where knowing the efficiency of an algorithm may have helped the developer devise a better solution:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/watch?v=RGuJga2Gl_k"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

<aside>
<b>Check your understanding</b>
<p>
A software developer has written two algorithms to solve a problem. After performing some analysis, he finds Algorithm A has a running time of O(n^3) and Algorithm B has a running time of O(n^2 * logn). Which algorithm is more efficient?
</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p>
<b>Answer.</b> Algorithm B is more efficient. Algorithm A could equivalently be described as having an efficiency of O(n * n * n), and Algorithm B is O(n * n * logn). In other words, Algorithm B replaces one of the factors of `n` with `logn`, which grows more slowly as `n` increases. Therefore, Algorithm B has a faster running time.
</p>
</details>
</aside>

To summarize, here are some of the most common efficiency classes, sorted by slowest to fastest:

* O(n!), where ! is the factorial function
* O(c^n) where c is some constant
* O(n^c) where c is some constant > 2
* O(n^2)
* O(nlogn)
* O(n)
* O(logn)
* O(1)

> Wait! I thought an O(n^2) algorithm grows faster than an O(n) algorithm. Why is an O(n) algorithm considered faster?
>
> Be careful! "Faster" here refers to two separate concepts. The number of operations in an O(n^2) algorithm grows faster than the number of operations in an O(n) algorithm as `n` increases. However, more operations is a *bad* thing in terms of algorithmic efficiency -- more operations means the algorithm is slower. Relatively speaking, an algorithm whose number of operations grows *slowly* as the input size increases is a *fast* algorithm because it will take less time to complete.

## The rules of big-O notation

You may have noticed that the examples of big-O classes above use simple, one-term expressions. However, the counts of operations that we devised for selection sort had multiple terms and constants: `C(n) = n^2/2 - n/2` and `M(n) = 3n - 3`. So what efficiency classes do those expressions fit into? For this, we will need to consult two rules for big-O notation:

### Rule 1: lower-order terms are ignored

Keep in mind that big-O defines what happens as `n` increases -- in theory, to infinity. Therefore, when analyzing the efficiency of algorithms, we think of `n` as a very large number.

When `n` is large, mathematical expressions involving `n` are dominated by their largest term (i.e., the term with the highest *degree* or exponent):

> Insert table showing how n^2/2, n/2, and n^2/2 - n/2 change as n grows from 10 --> 100 --> 10,000

Therefore, in big-O notation we ignore all lower-order terms and focus only on the higest order term.

### Rule 2: coefficients are ignored

For the same reason, we typically ignore coefficients, even on the largest term. As `n` grows very large, coefficients are not significant. Even a coefficient such as `1/1,000,000,000,000` is insigficant when `n` grows toward infinity!

For example, `n^2/2 + n = O(n^2)` because we can ignore the lower-order term (`n`) and can also ignore the coefficient (`1/2`).

<aside>
<b>Check your understanding</b>
<p>What is the big-O running time for an algorithm that performs `7n - 5 + 99n*logn/500` operations?</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> Since `n*logn` is the highest order term, `7n - 5 + 99n*logn/500 = O(nlogn)`.</code></p>
</details>
</aside>

## Back to selection sort

Now that we know about big-O notation, we can revisit our counts of the number of comparisons `C(n)` and the number of moves `M(n)` of selection sort and derive their big-O expressions:

`C(n) = n^2/2 - n/2 = O(n^2)`

`M(n) = 3n - n = O(n)`

In other words, the number of comparisons is O(n^2) and the number of moves is O(n) for selection sort. If we double the length `n` of the list to sort to `2n`, we would expect the number of moves to approximately double. We would also expect the number of comparisons to approximately *quadruple*, since (2n)^2 = 4n^2.

During the course of its execution, selection sort performs O(n^2) comparisons + O(n) moves. If we follow the same general principle of dropping lower order terms, then the number of comparisons dominates the number of moves and the overall running time of selection sort is O(n^2).

There you have it! We at last have a succinct and rigorously-defined way of labeling the efficiency of algorithms. We can now use big-O notation to analyze algorithms and compare them.

> What would happen if you ran an O(n) algorithm on a fast computer, and compared how long it takes to execute to an O(logn) algorithm running on a slow computer?
>
> Over time, advancements in hardware and software technology have enabled modern computers to be faster than computers of 10, 20, even 50 years ago by orders of magnitude. For some input sizes, it's true that a fast computer running an O(n) algorithm will complete faster than an older computer running an O(logn) algorithm. However, if you keep increasing the input size, there will eventually come a point where the slower computer will execute faster since the O(logn) algorithm will eventually be more efficient.
>
> Keep in mind that big-O notation is a theoretical tool to help us analyze algorithms in broad terms. However, if you're  concerned with the performance of an algorithm running a real task on actual computer, lower-order terms, coefficients, and the capabilities of the hardware and software *do* matter.

## Summary

We've covered a lot of ground in this lesson. Watch the video below to see a quick summary of big-O notation, and make sure that your understanding aligns with what it describes before moving on to the next lesson.

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/watch?v=g2o22C3CRfU"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>
