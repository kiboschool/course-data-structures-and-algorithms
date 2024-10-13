# Space and time efficiency

When we talk about the efficiency of an algorithm, we are concerned with how the algorithm uses two resources: *space* and *time*.

<center>
<img
    src="/images/week-01/spacetime.jpg"
    class="center"
    alt="Artist concept of a warped field around Earth to illustrate spacetime, a four-dimensional description of the universe including height, width, length, and time."
    style="width:400px;" />
</center>

<figcaption align = "center">Figure: No, not <i>spacetime</i>. Space <b>and</b> time!</figcaption>

## Time efficiency

The time efficiency of an algorithm refers to the amount of computational time that an algorithm takes to complete its task. It is typically, though not always, the most constrained resource for solving a problem.

For example, if a hacker tried to guess the password for your movie streaming account, the main challenge would be the amount of time it takes. The hacker could guess every possible combination (or *permutation*) of letters, numbers, and special characters in every possible length, but that would take a *long* time.

Let's say that you could make the assumption that passwords are always ten characters long, and only consist of letters from the Latin alphabet (A...Z,a...z) and Arabic numerals (0...9). That still means there are 10<sup>62</sup> possible password combinations!

Guessing those at a rate of one million guesses per second would still take you quadrillions of quadrillions of years to guess them all. We try to avoid such *brute-force* algorithms, since they often take too long to compute. But soon, we will have the tools to evaluate the time efficiency of algorithms to judge which ones are efficient and which are not.

## Space efficiency

In addition to time, we are also often concerned with the amount of *space* that an algorithm requires to perform its computation. In computer science, the space efficiency of an algorithm refers to the amount of computer memory the algorithm needs to perform its task.

Many tasks do not require a significant amount of memory beyond what is given to them as input. For example, consider a program that computes *n factorial*, or `n! = n * (n-1) * (n-2) ... * 2 * 1`:

```python
def factorial(n):
    product = 1
    for i in range(1, n + 1):
        product *= i
    return product
```

Notice that this function does not require much memory -- just a few local variables (`n`, `product`, and `i`) to help compute the result.

On the other hand, recall this implementation of insertion sort from P1:

```python
def insertion_sort(a_list):
    results = [a_list[0]]

    for item in a_list:
        if item >= results[-1]:
            results.append(item)
            continue

        for i in range(len(results)):
            if item <= results[i]:
                results.insert(i, item)
                break

    return results
```

In addition to the list passed in as a parameter (`a_list`), another list named `results` is also formed as part of the execution of the function. `results` ultimately contains all of the elements of `a_list`, put into sorted order. This means that if `a_list` has 1 million elements, `results` will also have 1 million elements! This is a significant amount of memory required by the algorithm, and must be taken into account when discussing its space efficiency.

> Note: there are alternate implementations of the insertion sort algorithm that do not require using an extra list.

## Space-time tradeoffs

We now know that we can evaluate algorithms in terms of their space and time efficiencies. It's also important to note that often there is a *tradeoff* between space and time resources used in an algorithm.

For example, say that we wanted to write a program that was capable of calculating `n!` for all positive integers `n <= 10`. We could use the same algorithm from above, perhaps with some extra error-checking:

 ```python
def factorial(n):
    if n < 1 or n > 10:
        print("n must be positive and <= 10")
        return 0 # error

    product = 1
    for i in range(1, n + 1):
        product *= i
    return product
```

Let's think about other ways we could compute this result. Instead of calculating the result when the program is run, we could instead *precompute* the values of `n!` for all integers `1 <= n <= 10` and store those in a list. Then, all the function would have to do is return the entry at the appropriate index of the list:

 ```python
def factorial_precomputed(n):
    if n < 1 or n > 10:
        print("n must be positive and <= 10")
        return 0 # error

    factorials = [1, 2, 6, 24, 120, 720, 5040, 40320, 362880, 3628800]

    # n! is stored in index n - 1
    return factorials[n - 1]
```

`factorial_precomputed()` will take fewer steps to execute than `factorial()` because it doesn't need to use a `for` loop to actually calculate the value of `n!`. Therefore, it will be faster. However, it uses more *space* than `factorial()` because it needs an extra list of size `n`.

We have used some extra space in order to save time -- a space-time tradeoff! Precomputing a result and performing a simple lookup when needed is a very common form of a space-time tradeoff.

## Summary

* Algorithms can be evaluated in terms of how much computational time they take to complete
* Algorithms can also be evaluated in terms of how much memory they consume
* Sometimes, there is a tradeoff between the amount of time and space an algorithm takes
