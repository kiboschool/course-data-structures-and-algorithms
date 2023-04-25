# Merge Sort

Let's now revisit the topic of sorting. Previously, we talked about selection sort, insertion sort, and radix sort, and compared and contrasted their efficiencies.

Now that we know recursion, let's learn an algorithm that recursively sorts a list. One such algorithm is *merge sort*, which uses a *divide-and-consquer* technique to sort a list in time `O(nlogn)`.

Watch the following video to learn how merge sort works:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/Pr2Jf83_kG0"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

To summarize, merge sort has two phases:

1. Start with a list of `n` elements. Repeatedly split the list in half using recursion until you are left with sublists of size 1. This is the base case, since sublists of size 1 are, naturally, sorted.

2. Merge the sublists of size 1 pairwise, into sorted sublists of size 2. Repeat this process, merging the sublists of size 2 pairwise into sublists of size 4, so on and so forth. Repeat until at last you merge the two sublists of size `n / 2` into one fully sorted list of size `n`.

<aside>
<b>Check your understanding</b>
<p>The video begins by introducing an algorithm for merging two sorted lists. Using pencil and paper, trace the execution of merging sorted lists <code>[5, 10, 15, 20]</code> and <code>[9, 13, 14, 22]</code> into a larger, also sorted list. You should only make one iteration over each list.
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> As described in the video, when merging two sorted lists, you trace through both input lists simultaneously, maintaining an index for each:</p>
<pre><code>[5, 10, 15, 20]     [9, 13, 14, 22]
 ^                   ^
result: []</code></pre>
<p>On the first iteration, you compare the first elements of each lists (5 and 9). Since 5 is smaller, you add that to the result list, and move on to the 10 in the list on the left:</p>
<pre><code>[5, 10, 15, 20]     [9, 13, 14, 22]
     ^               ^
result: [5]</code></pre>
<p>You compare the 10 with the left list with the 9 on the right list, and since 9 is smaller, you add the 9 to the result list, and move on to the 13 in the list on the right:</p>
<pre><code>[5, 10, 15, 20]     [9, 13, 14, 22]
     ^                   ^
result: [5, 9]</code></pre>
<p>You then compare the 10 with the left list with the 13 on the right list, and since 10 is smaller, you add the 10 to the result list, and move on to the 15 in the list on the left:</p>
<pre><code>[5, 10, 15, 20]     [9, 13, 14, 22]
         ^               ^
result: [5, 9, 10]</code></pre>
<p>Continue this process, advancing one element at a time in the appropriate list, until all elements are added to the result list.
</details>
</aside>

## Merge sort in Python

Watch the following video to step through the implementation of merge sort:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/cVZMah9kEjI"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

Here's the code written in the video:

```python
def merge_sort(lst):
    if len(lst) > 1:
        left_lst = lst[:len(lst) // 2]
        right_lst = lst[len(lst) // 2:]

        # Recursion
        merge_sort(left_lst)
        merge_sort(right_lst)

        # Merge lest_lst and right_lst
        i = 0     # left_lst index
        j = 0     # right_lst index
        k = 0     # merged list index
        while i < len(left_lst) and j < len(right_lst):
            if left_lst[i] < right_lst[i]:
                lst[k] = left_lst[i]
                i += 1
            else:
                lst[k] = right_lst[j]
                j += 1
            k += 1

        # Fill in remaining elements from left_lst
        while i < len(left_lst):
            lst[k] = left_lst[i]
            i += 1
            k += 1

        # Fill in remaining elements from right_lst
        while j < len(right_lst):
            lst[k] = right_lst[j]
            j += 1
            k += 1
```

A few notes:

* After the recursive calls to `merge_sort()` return, both `left_lst` and `right_lst` are sorted, and can therefore be merged into a single sorted list using the merging algorithm.
* Only one of bodies of the last two `while` loops will be executed, depending on which half (left or right) still has elements.
* The base is when the condition `if len(lst) > 1` is false. Lists that have a length of <= 1 are already sorted, so no further recursion is needed and the function doesn't need to do anything -- it can just return.

<aside>
<b>Check your understanding</b>
<p>Consider the list <code>[44, 90, 1, 15, 10, 8, 12, 77]</code>. What would the list look like after the completion of the <i>fourth</i> merge? In other words, after the fourth execution of the code that performs the merging step.
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b></p>
Insert video
</p>
</details>
</aside>

## Efficiency

> Insert video about efficiency.

To summarize, merge sort runs in time `O(nlogn)` in all cases, which is much better than selection sort and insertion sort, which typically run in time <code>O(n<sup>2</sup>)</code>. However, merge sort requires `O(n)` extra space, as it is not an in-place sorting algorithm.
