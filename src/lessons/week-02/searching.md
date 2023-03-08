# Searching

Let's now put our algorithm analysis skills into practice in the context of *searching*.

Searching is a very common task in computer science. When we store data inside of data structures, we often need to search for and extract that information at a later point in time. In some applications, searches occur very frequently and need to be quickly executed.

For example, a large e-commerce website receives searches for products with keywords ("medium blue t-shirts"), and needs to search through their catalog of millions of products to return relevant results. The website may receive thousands of such requests every second!

Let's take a look at two methods of searching for data in a Python list: *linear search* and *binary search*. By the end of this week, we'll be able to compare the efficiency of these two algorithms.

> Data structures such as trees and hash tables provide the ability to perform data lookups very fast -- but we're not quite there yet! We'll stick to using Python lists for now.

## Linear search

A linear search simply iterates sequentially through a collection of items. The search checks every element of the collection, until either the desired item is found, or there are no more left items to inspect.

Here's an example of a linear search. The function below checks whether a list contains a given number:

```python
def contains_num(lst, num):
    for item in lst:
        if item == num:
            return True
    return False
```

From our big-O heuristics, we know that this function contains a single `for` loop that iterates over all items of the list, and so its running time is `O(n)`.

<aside>
<b>Check your understanding</b>
<p>Why is the below implementation of linear search incorrect?</p>
<pre><code class="language-python">def contains_num(lst, num):
    for item in lst:
        if item == num:
            return True
        else
            return False
</code></pre>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b>The code returns <code>False</code> too early. If the first element of the list is not <code>num</code>, then the body of the <code>else</code> clause will be executed, and <code>False</code> will be returned. However, the value may have appeared later in the list. The function can only be sure that <code>num</code> is not in the list after all items have been inspected.</p>
</details>
</aside>

Let's modify our linear searching algorithm. What could we do if the list was *sorted* -- with all of items of the list ordered according to their value, least to greatest? Could we improve the algorithm?

If the list were sorted, we could stop our search early if we were sure that the item was not in the list (the code in the `elif`):

```python
def contains_num(lst, num):
    for item in lst:
        if item == num:
            return True
        elif item > num:
            # we are past the point where num
            # would have been in the list
            return False
    return False
```

Since the list is sorted, if we've passed the point in the list where `num` should have been, we know that it doesn't appear in the list. Try tracing this newest version of the function with the list `[2, 4, 7, 8, 9]` while searching for the number `5`.

We have leveraged the fact that the list is in sorted order to improve our algorithm in *some* cases when `num` does not appear in the list.

<aside>
<b>Check your understanding</b>
<p>Describe a scenario where <code>num</code> does not appear in the list, but our optimization makes no difference.</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b>If the <code>num</code> we are looking for is greater than all of the elements in the list, then we have to search the entire list anyway before being sure that <code>num</code> doesn't appear.
</details>
</aside>

This optimization is nice, but it doesn't really improve our algorithm when the item *does* appear in the list. For that, we can use binary search.

## Binary search

One of the exercises from the P1 course involved writing a number guessing game, in which a program chooses a random number between 1 and 100, and the player guesses the number. If they guess the number, they win. If they guess too low or too high, the program tells them whether the guess was too high or too low and lets them keep guessing.

We mentioned in P1 that binary search would be a good algorithm to use in this problem, since it allows us to cut the space of what we're searching for in half with each guess. For the number guessing game, 50 would be a good initial guess, since the program would tell us whether the number was lower or higher, allowing us to then either ignore the numbers 1-49 or the numbers 51-100. Repeating this technique by guessing the "middle" number at each stage is binary search, which ends up being much faster than linear search!

Watch the video below to see an overview of binary search. **Note: you only need to watch the first 3 minutes, and can stop watching once the presenter starts writing code.**

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/P3YID7liBug"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

As the presenter mentioned, the number of items inspected by binary search is more like <code>log<sub>2</sub>n</code>, compared to the `n` items inspected by linear search. For this reason, binary search has a running time of `O(logn)`, which is much more efficient than `O(n)`!

> It's worth emphasizing that binary search only works if the collection is sorted, and that sortedness doesn't come for free. As items are inserted into the collection, care must be taken to insert it in sorted order, or else we wouldn't be able to use binary search.

Now that we have an understanding of binary search in general, watch the following video to develop an understanding of how binary search could be implemented using a `while` loop:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/fDKIpRe8GW4"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

## Summary

If a collection is sorted, then binary search can be a much faster way of performing a lookup than linear search. Sorting collections provides many benefits, so let's turn our attention to *sorting* as a topic next.
