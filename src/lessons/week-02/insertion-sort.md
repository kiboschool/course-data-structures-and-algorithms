# Insertion Sort

Let's continue our explanation of sorting algorithms with *insertion sort*. Watch the video below for an overview of the algorithm:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/watch?v=JU767SDMDvA"
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
<p>After the third pass of the insertion sort algorithm, a list looks like this: `[10, 15, 20, 12, 44, 90, 77, 1, 8]`. After *two more* passes of insertion sort, what will the list look like?</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b>The fourth iteration of insertion sort will focus on the 12, and push it to the left two spaces to  will look for the minimum element starting from index 3 in the list. In the unsorted portion of the list, 45 is the minimum element. Therefore, it will be swapped with the element at index 3, making this list: <code>[20, 38, 44, 45, 77, 90, 81]</code>.</p>
</details>
</aside>


