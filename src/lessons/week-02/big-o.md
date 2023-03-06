# Big-O Notation

We are now ready to develop a formalism for classifying algorithms according to their time and space efficiencies. This formalism is known as *big-O notation*.

## What is big-O notation?

Big-O notation can be used to describe an algorithm's time and space efficiency. It describes an upper bound on the amount of resources that will be required for the algorithm as a function of the input size (`n`) to the algorithm.

> Time efficiency is sometimes known as *time complexity* or *running time*. Space efficiency is sometimes known as *space complexity*.

Watch the video below to learn about big-O notation and to hear an example where knowing the efficiency of an algorithm may have helped a software developer devise a better solution:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/RGuJga2Gl_k"
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
A software developer has written two algorithms to solve a problem. After performing some analysis, he finds Algorithm A has a running time of <code>O(n<sup>3</sup>)</code> and Algorithm B has a running time of <code>O(n<sup>2</sup> * logn)</code>. Which algorithm is more efficient?
</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p>
<b>Answer.</b> Algorithm B is more efficient. Algorithm A could equivalently be described as having an efficiency of <code>O(n * n * n)</code>, and Algorithm B is <code>O(n * n * logn)</code>. In other words, Algorithm B replaces one of the factors of <code>n</code> with <code>logn</code>, the latter of which grows more slowly as the input size (<code>n</code>) increases. Therefore, Algorithm B has a faster running time.
</p>
</details>
</aside>

To summarize, here are some of the most common efficiency classes, sorted by slowest to fastest:

* `O(n!)`, where `!` is the factorial function
* <code>O(c<sup>n</sup>)</code> where `c` is some constant
* <code>O(n<sup>c</sup>)</code> where `c` is some constant >2
* <code>O(n<sup>2</sup>)</code>
* `O(nlogn)`
* `O(n)`
* `O(logn)`
* `O(1)`

For example, we would say that as the input size `n` grows, an `O(n)` algorithm is faster than an <code>O(n<sup>2</sup>)</code> algorithm.

<!-- talk about this in live class
<blockquote>
<p>
Wait! I thought an <code>O(n<sup>2</sup>)</code> algorithm grows faster than an <code>O(n)</code> algorithm. Why is an <code>O(n)</code> algorithm considered faster?</p>
<p>⚠️ Be careful. "Faster" here refers to two separate concepts. The number of operations in an <code>O(n<sup>2</sup>)</code> algorithm grows faster than the number of operations in an <code>O(n)</code> algorithm as <code>n</code> increases. However, more operations is a <i>bad</i> thing in terms of algorithmic efficiency -- more operations means the algorithm is slower. Relatively speaking, an algorithm whose number of operations grows <i>slowly</i> as the input size increases is a <i>fast</i> algorithm because it will take less time to complete.</p>
</blockquote>
-->

## What is big-O measuring?

We mentioned above that a big-O expression defines an upper bound on the amount of resources used by an algorithm. But how do we measure the amount of resources?

For time efficiency, recall from last week we are concerned with the computational time of the algorithm. The computational time is determined by the number of *operations* that the algorithm performs. When a computer program is executed, the code of the program is broken down into a series of simple operations, for example:

* Adding two numbers together
* Comparing two numbers
* Fetching a value from main memory
* Assigning a value to a variable
* And many others!

Taken together, these fundamental operations compose an entire computer program. For some programs, we are actually able to derive an exact formula for the number of operations it performs. For example, we might be able to say that an algorithm performs `3n - 3` move operations, where `n` is the size of the input. To derive the big-O running time from this exact formula, we can use a couple of rules.

## The rules of big-O notation

### Rule 1: lower-order terms are ignored

Keep in mind that big-O defines what happens as `n` increases -- in theory, to infinity. Therefore, when analyzing the efficiency of algorithms, we think of `n` as a very large number.

When `n` is large, mathematical expressions involving `n` are dominated by their largest term (i.e., the term with the highest *degree* or exponent):

| **n**  || **n^2/2**  | **n/2** | **n^2/2 - n/2** |
|--------|-|------------|---------|-----------------|
| 10     || 50         | 5       | 45              |
| 100    || 5,000      | 50      | 4,950           |
| 10,000 || 50,000,000 | 5,000   | 49,995,000      |

Therefore, in big-O notation we ignore all lower-order terms and focus only on the higest order term.

### Rule 2: coefficients are ignored

For the same reason, we typically ignore coefficients, even on the largest term. As `n` grows very large, coefficients are not significant. Even a coefficient such as `1/1,000,000,000,000` is insigficant when `n` grows toward infinity!

For example, <code>n<sup>2</sup>/2 + n = O(n<sup>2</sup>)</code> because we can ignore the lower-order term (`n`) and can also ignore the coefficient (`1/2`).

<aside>
<b>Check your understanding</b>
<p>What is the big-O running time for an algorithm that performs <code>7n - 5 + 99n*logn/500</code> operations?</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b>After ignoring all coefficients and lower-order terms (<code>n</code>), we have that <code>7n - 5 + 99n*logn/500 = O(nlogn)</code>.</p>
</details>
</aside>

<!-- talk about this in async session
> What would happen if you ran an `O(n)` algorithm on a fast computer, and compared how long it takes to execute to an `O(logn)` algorithm running on a slow computer?
>
> Over time, advancements in hardware and software technology have enabled modern computers to be faster than computers of 10, 20, even 50 years ago by orders of magnitude. For some input sizes, it's true that a fast computer running an `O(n)` algorithm will complete faster than an older computer running an `O(logn)` algorithm. However, if you keep increasing the input size, there will eventually come a point where the slower computer will execute faster since the `O(logn)` algorithm will eventually be more efficient.
>
> Keep in mind that big-O notation is a theoretical tool to help us analyze algorithms in broad terms. However, if you're  concerned with the performance of an algorithm running a real task on actual computer, lower-order terms, coefficients, and the capabilities of the hardware and software *do* matter.
-->

## Big-O and Worst-Case Analysis

An algorithm can behave differently depending on the contents of its input. For example, consider this algorithm:

```python
def print_odd_len_list(lst):
    # if the list has an even number of elements
    if len(lst) % 2 == 0:
        return

    for item in lst:
        print(item)
```

Clearly, the `if` statement here impacts how long this algorithm takes to run. If the given `lst` has an odd number of elements, the function prints all of the elements, one-by-one. However, if `lst` has an even number of elements, the function simply returns without doing any printing. How do we analyze the effect that conditional execution (i.e., `if` statements) has on the running time of an algorithm?

We can break our analysis down into different cases. For `print_odd_len_list()`, the *best* case occurs when the list is an even length, because there is the least amount of work to do. For even-length lists, the function is O(1) -- no matter how long the list is, it can always immediately return!

In the *worst* case, an odd-length list is given. In this case, the function iterates over the entire list, and is therefore `O(n)`.

When we're analyzing algorithms, we are typically interested in the worst case behavior when devising our big-O expression. This allows us to ignore conditional execution and just focus on the overall structure of the algorithm. This worst-case analysis is for theoretical purposes only. In real-world applications, the best case -- and how often it occurs compared to the worst case -- matters!

Still, when someone asks for the big-O analysis of an algorithm, unless otherwise specified they are asking for the performance of the algorithm in the worst case.

<blockquote>
<p>
For selection sort (and many other algorithms), the best case and worst case are the same: the algorithm always repeatedly finds the smallest item in the list and swaps it into its final sorted place. Even if the input was an already-sorted list, the running time would still be <code>O(n<sup>2</sup>)</code>!
</p>
</blockquote>

## Big-O and Space

We can also use big-O notation to express the amount of *extra space* that an algorithm uses. By "extra" space, we mean memory resources that are needed to complete the algorithm, excluding the input.

For example, in selection sort, the only extra memory resources that are needed are some local variables, including loop indexes and the `temp` variable used to swap elements of the list. We consider this a *constant* amount of extra memory. Even though we may be doing O(n) swaps in the execution of the algorithm, we don't use `n` copies of the `temp` variable *all at once*. Overall, we would say that selection sort has an `O(1)` space efficiency.

We will soon see examples of algorithms that require more than a constant amount of extra space. We will revisit this topic when we learn about radix sort later this week.

## Summary

We've covered a lot of ground in this lesson. Watch the video below to see a quick summary of big-O notation, and make sure that your understanding aligns with what it describes before moving on to the next lesson.

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/g2o22C3CRfU"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>
