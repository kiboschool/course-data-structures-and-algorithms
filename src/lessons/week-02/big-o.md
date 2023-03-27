# Big-O Notation

Last week, we started exploring how algorithms can be evaluated in terms of their space and time efficiencies. This week, we will learn a more formal method for classifying the efficiency of an algorithm: *big-O notation*. You will use big-O notation to analyze algorithms not just for the rest of this course, but likely for the rest of your computer science career as well!

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
<b>Recall</b>
<p>
The logarithm function, y = log<sub>b</sub>(n) ("the log of n to the base b"), represents the exponent y to which b must be raised to produce n. In other words, to satisfy b<sup>y</sup> = n. Here are some examples:
</p>
<div class="table-wrapper"><table><thead><tr><th>Log expression</th><th>Equivalent value</th></tr></thead><tbody>
<tr><td>log<sub>10</sub>(1000)</td><td>3 (since 10<sup>3</sup> = 1000)</td></tr>
<tr><td>log<sub>2</sub>(32)</td><td>5 (since 2<sup>5</sup> = 32)</td></tr>
<tr><td>log<sub>2</sub>(1024)</td><td>10 (since 2<sup>10</sup> = 1024)</td></tr>
</tbody></table>
</div>
In computer science we typically deal with situations where b = 2, since as we will see, we often use algorithms that split the size of the input in <i>half</i> (i.e., into two segments) at each step. However, for big-O notation the base is not important, so it is typically omitted and we just say log(n).
</aside>

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

* `O(n!)` ("factorial time")
* <code>O(c<sup>n</sup>)</code> where `c` is some constant ("exponential time")
* <code>O(n<sup>c</sup>)</code> where `c` is some constant >2 ("polynomial time")
* <code>O(n<sup>2</sup>)</code> ("quadratic time")
* `O(nlogn)` ("linearithmic time" or "log-linear time")
* `O(n)` ("linear time")
* `O(logn)` ("logarithmic time")
* `O(1)` ("constant time")

For example, we would say that as the input size `n` grows, an `O(n)` algorithm is faster than an <code>O(n<sup>2</sup>)</code> algorithm.

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
<p><b>Answer.</b> After ignoring all coefficients and lower-order terms (<code>n</code>), we have that <code>7n - 5 + 99n*logn/500 = O(nlogn)</code>.</p>
</details>
</aside>

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

When we're analyzing algorithms, we are typically interested in the worst case behavior when devising our big-O expression. This allows us to ignore conditional execution and just focus on the overall structure of the algorithm. This worst-case analysis is for theoretical purposes only. In real-world applications, we do consider how frequently the best case would occur, along with whether there would be an average case (i.e., somewhere between best and worst). 

Still, when someone asks for the big-O analysis of an algorithm, unless otherwise specified they are asking for the performance of the algorithm in the worst case.

## Big-O and Space

We can also use big-O notation to express the amount of *extra space* that an algorithm uses. By "extra" space, we mean memory resources that are needed to complete the algorithm, excluding the input.

In some algorithms, the only extra memory resources that are needed are some local variables, such as loop indexes or a constant number of other variables on the stack. These algorithms have a space complexity of `O(1)`.

Other algorithms require a more significant amount of extra space. For example, an algorithm that makes a copy of a list has a space complexity of `O(n)`, since the amount of extra space needed by the algorithm linearly increases as the size `n` of the input list increases.

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

<aside>
<b>Check your understanding</b>
<p>
Order the following big-O efficiency classes, from fastest (most efficient) to slowest (least efficient): <code>O(nlogn)</code>, <code>O(3<sup>n</sup>)</code>, <code>O(1)</code>, <code>O(n<sup>3</sup>)</code>.
</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p>
<b>Answer.</b> <code>O(1)</code>, <code>O(nlogn)</code>, <code>O(n<sup>3</sup>)</code>, <code>O(3<sup>n</sup>)</code>.
</p>
</details>
</aside>


