# Radix sort

Both of the sorts we've considered so far are *comparative* sorting algorithms. They sort the lists by *comparing* elements of the list against each other to find their relative orderings, and puts them into position based on that ordering.

But that's not the only approach to sorting! One alternative is *distributive* sorting, which distributes the values of the list into positions based on an inherent characteristics of the values themselves.

One example of this is radix sort. Watch the video below to see how radix sort works:

> Insert 5 minute video showing radix sort.

In summary, the algorithm is as follows:

1. Place the values of the list into buckets 0-9 according to their least significant digit (the "ones" digit). At this point, the values are sorted with respect to their ones digits only.

2. Iterate over the values in the buckets, starting from the 0 bucket and proceeding all the way to the 9 bucket. Place the values of the list into buckets 0-9 according to their next significant digit (the "tens" digit). At this point, the values are sorted with respect to both their tens and ones digits.

3. Continue iterating over the values in the buckets (from 0 to 9), consider the next significant digit for each pass. Stop when there are no more digits to consider.

4. Format the buckets back into a list and return the list.

<aside>
<b>Check your understanding</b>
<p>What would the list of buckets look like after using radix sort on this list: <code>[61, 15, 20, 12, 44, 90, 77, 1, 8]</code>.</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> After the first iteration of radix sort, the values are placed into buckets according to their ones digit: <code>[[20, 90], [61, 1], [12], [], [44], [15], [], [77], [8], []]</code>.</p>
</details>
</aside>

## Runtime analysis

For random lists, both selection sort and insertion sort are <code>O(n<sup>2</sup>)</code> algorithms. Although we won't go into the proof here, it can actually be proven that comparative algorithms can do, at best, `O(nlogn)`. But can we do better with a non-comparative sort like radix sort?

Let's think about the running time of radix sort by defining some variables:

* `m` = number of digits
* `n` = length of the list

Using these variables, we can define the running time of radix sort to be `O(m * n)`. This is because the algorithm follows this pseudocode:

```
for each of m digits:
    for each of n values:
        place each value into a bucket according to its ith digit
``` 

In other words, radix sort performs `m` passes, each of which processes all `n` values of the list. Since these `for` loops are nested, we can use our big-O heuristics to see that the running times of these loops would be multiplied to yield a running time of `O(m * n)`.

In many cases, we can consider the maximum number of digits to be a constant, since numbers often have a finite representation in computer programs (e.g., 32-bit integers). Therefore, radix sort is often considered to be a linear-time `O(n)` sort!

Note that the algorithm requires a list of buckets at each step to distribute the values into, meaning that the sort is not in-place and requires `O(n)` extra space.
