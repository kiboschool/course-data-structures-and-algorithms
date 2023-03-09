# Insertion Sort

Let's continue our tour of sorting algorithms with *insertion sort*. Watch the video below for an overview of the algorithm:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/JU767SDMDvA"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

To summarize, here are the steps of insertion sort:

1. Start with the element at index 1. Compare the element with all elements to its left (in this case, just the element at index 0). If the element at index 1 is less than the element at index 0, then slide the element at index 1 over so that the elements have switched places. The first *two* elements of the list are now sorted with respect to each other.

2. Consider the element at index 2. Again compare it with all elements to its left, sliding it over as necessary to maintain sortedness among the first three elements in the list. The first *three* elements of the list are now sorted with respect to each other.

3. Continue throughout the length of the list, taking one element at a time and finding its appropriate place in the sorted part of the list. During some iterations, an element may not need to be pushed left at all (if it is greater than the first element to its left).

<aside>
<b>Check your understanding</b>
<p>After the third pass of the insertion sort algorithm, a list looks like this: <code>[10, 15, 20, 12, 44, 90, 77, 1, 8]</code>. After <i>two more</i> passes of insertion sort, what will the list look like?</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> The fourth iteration of insertion sort will focus on the 12, and push it to the left two spaces to  will look for the minimum element starting from index 3 in the list. In the unsorted portion of the list, 45 is the minimum element. Therefore, it will be swapped with the element at index 3, making this list: <code>[20, 38, 44, 45, 77, 90, 81]</code>.</p>
</details>
</aside>

## Insertion sort in Python

Let's see how insertion sort can be implemented in Python:

> VIDEO: 5 minute video walking through the code of selection sort.

## Big-O analysis of insertion sort

Let's take another look at the code for insertion sort:

```python
def insertion_sort(lst):
    for i in range(1, len(lst)):
        to_insert = lst[i]
        j = i
        while j > 0 and to_insert < lst[j - 1]:
            lst[j] = lst[j - 1]
            j -= 1
        lst[j] = to_insert
```

Unlike selection sort, with insertion sort there is a difference between the best case and worst case behavior of the algorithm.

### Best case analysis

Let's trace through what would happen if the list given to insertion sort was already sorted:

> Insert 2-3 minute video tracing the loop and seeing that the while loop is never executed.

Since the body of the `while` loop is never executed, we can essentially ignore it for the purposes of our big-O analysis. This essentially leaves us with a single `for` loop to execute. We can therefore say that in the best case (a fully sorted list), the running time of insertion sort is only `O(n)`!

### Worst case analysis

The worst case scenario for insertion sort occurs when the algorithm is given a *reverse sorted* list as input. This is an inefficient scenario for insertion sort because it means that each element is compared to *all* elements to its left on every iteration of the algorithm.

Let's count the number of comparisons in this case:

* `lst[1]` is compared to 1 element (`lst[0]`)
* `lst[2]` is compared to 2 elements (`lst[0]` and `lst[1]`)
* ...
* `lst[n - 1]` is compared to `n` - 1 elements

Therefore, the number of comparisons `C(n) = 1 + 2 + ... + (n - 2) + (n - 1)`. We've seen this pattern before! It's again an <code>O(n<sup>2</sup>)</code> algorithm.

### Average case analysis

In the average case, the input list is neither sorted nor reverse sorted, but simply a random collection of numbers. In this scenario, some elements may need to be shifted left many times, some elements may need to be shifted left only a few times, and some elements may not need to be shifted left at all.

Under this scenario, the nested `while` loop is running a non-negligible number of times, and so we basically have nested loops, leaving us with an <code>O(n^<sup>2</sup>)</code> algorithm in general.

## Space complexity

How much extra space is needed for algorithms like selection sort and insertion sort?

Both of these algorithms are *in-place* sorting algorithms, meaning that the sorting can be done within the input list itself. We may need to use a small number of temporary variables to do swapping or to keep track of which value to insert, but this is a constant amount of extra memory. Therefore, the space complexity of both selection sort and insertion sort are `O(1)`.
