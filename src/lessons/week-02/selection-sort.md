# Selection Sort

The first sorting algorithm that we will learn is *selection sort*. Watch the following video to learn how the algorithm works.

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/3hH8kTHFw2A"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

In summary, to sort a list, selection sort performs the following steps:

1. Find the minimum element in the list.
2. Swap the minimum element in the list with the element at index 0. The minimum element is now in its final sorted position.
3. Find the minimum element in the remaining portion of the list (starting from index 1).
4. Swap this element with the element at index 1. The second-to-minimum element is now in its final sorted position.
5. Continue finding the next-minimum element in the remaining portions of the list until you have swapped all elements into their final sorted positions.

<aside>
<b>Check your understanding</b>
<p>After the third pass of the selection sort algorithm, a list looks like this: <code>[20, 38, 44, 90, 77, 45, 81]</code>. After the <i>fourth</i> pass of selection sort, what will the list look like?</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> The fourth iteration of selection sort will look for the minimum element starting from index 3 in the list. In the unsorted portion of the list, 45 is the minimum element. Therefore, it will be swapped with the element at index 3, making this list: <code>[20, 38, 44, 45, 77, 90, 81]</code>.</p>
</details>
</aside>

Let's now think about how we could implement this algorithm in Python.

## Swapping elements

As you can see, a key part of selection sort is *swapping* elements. How can we accomplish that in Python?

Let's try defining the `swap()` function to swap two elements in a list. We'll make use of a variable `temp` to allow the swap to happen without overwriting one of the element's values before we can use it:

```python
def swap(elem1, elem2):
    temp = elem1
    elem1 = elem2
    elem2 = temp

lst = [5, 8, 2, 1, 9]
swap(lst[0], lst[3])
print(lst)
```

<aside>
<b>Check your understanding</b>
<p>What will be the output of the above code fragment? Trace the execution of the code using a memory diagram.</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> Insert 2-3 minute video with slides here.</p>
</details>
</aside>

As you can see, we will need to take a slightly different approach. Here's a second, improved version of the `swap()` function:

```python
def swap(lst, i, j):
    temp = lst[i]
    lst[i] = lst[j]
    lst[j] = temp

lst = [5, 8, 2, 1, 9]
swap(lst[0], lst[3])
print(lst)
```

<aside>
<b>Check your understanding</b>
<p>Now what will be the output of the code fragment above? Again trace the execution of the code using a memory diagram.</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> Insert 2-3 minute video with slides here.</p>
</details>
</aside>

## Selection sort in Python

Let's see how we can use the `swap()` function to implement selection sort in Python:

> VIDEO: 5 minute video walking through the code of selection sort.

## Counting comparisons and moves

Here again is the code for selection sort:

```python
def index_smallest(lst, start):
    index_min = start
    for i in range(start + 1, len(lst)):
        if lst[i] < lst[index_min]:
            index_min = i
    return index_min

def selection_sort(lst):
    for i in range(len(lst) - 1):
        j = index_smallest(lst, i)
        swap(lst, i, j)
```

Let's try counting the number of comparisons `C(n)` that selection sort makes for a list of size `n`. To sort a list of `n` elements, selection sort performs `n - 1` passes over the list.

* On the first pass, it performs `n - 1` comparisons to find the smallest element.
* On the second pass, it performs `n - 2` comparisons to find the smallest element.
* ...
* On the `n - 1`st pass, it performs 1 comparison to find the smallest element.

If you sum the comparisons across all of these passes, you would get:

`C(n) = 1 + 2 + 3 + ... + (n - 3) + (n - 2) + (n - 1)`

This is actually the same as the arithmetic sum that we saw in the heuristics of big-O lesson. There, we learned that this sum is equal to <code>n<sup>2</sup>/2 - n/2</code>, meaning that selection sort performs <code>O(n<sup>2</sup>)</code> comparisons.

What about the number of moves? Well again we know that selection sort performs `n - 1` passes, during each of which it performs one `swap()` operation. The `swap()` function performs three moves to shift values into a temporary variable and into the spots in the list, meaning that selection sort always performs exactly `3n - 3 = O(n)` moves.

## Big-O notation

To summarize, we have the following exact expressions for the number of comparisons `C(n)` and the number of moves `M(n)` that selection sort performs for a list of size `n`:

<code>C(n) = n<sup>2</sup>/2 - n/2 = O(n<sup>2</sup>)</code>

`M(n) = 3n - n = O(n)`

Using big-O notation, the number of comparisons is <code>O(n<sup>2</sup>)</code>. This means that if we doubled the size of the input list from `n` to `2n`, we would also expect the number of comparisons to approximately *quadruple*, since <code>(2n)<sup>2</sup> = 4n<sup>2</sup></code>.

On the other hand, the number of moves in selection sort is `O(n)`. If we double the length `n` of the list to sort to `2n`, we would expect the number of moves to approximately double.

During the course of its execution, selection sort performs <code>O(n<sup>2</sup>)</code> comparisons + `O(n)` moves. If we follow the same general principle of dropping lower order terms, then the number of comparisons dominates the number of moves and the overall running time of selection sort is <code>O(n<sup>2</sup>)</code>.
