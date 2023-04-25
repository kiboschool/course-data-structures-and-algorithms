# List Recursion

Recursion over lists is very similar to recursion over strings. Since lists in Python can be indexed and sliced like strings, the same principles that we learned in the last lesson also apply to lists.

## A mystery recursion function

Here's an example of a recursive function that operates on a list:

```python
def mystery(lst):
    if len(lst) == 0:
        return 0
    else:
        return lst[0] + mystery(lst[1:])
```

<aside>
<b>Check your understanding</b>
<p>Based on your understanding of recursion, what does this function do? If in doubt, try tracing the execution of <code>mystery([5, 3, 8])</code>.</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> This function sums all of the numbers in a list. It works by adding the first element of the list to the sum of the <i>rest</i> of the list at each step. The base case is when it's given an empty list, the sum is 0.</p>
</details>
</aside>

## Storing the recursive return value

Consider the following recursive function, which counts the even numbers in a list:

```python
def count_even_numbers(lst):
    if len(lst) == 0:
        return 0
    else:
        if lst[0] % 2 == 0:
            return 1 + count_even_numbers(lst[1:])
        else:
            return count_even_numbers(lst[1:])
```

For example, `count_even_numbers([1, 2, 3, 4, 5])` would evaluate to `2`, since there are two even numbers in that list.

This function checks whether the number at the first position of the list `l[0]` is even, and if it is, returns 1 *plus* the count of even numbers in the rest of the list (excluding the first character).

If the first number is not even, the function just returns the count of numbers in the rest of the list.

Here's an alternative way of implementing this function:

```python
def count_even_numbers(lst):
    if len(lst) == 0:
        return 0
    else:
        count_in_rest = count_even_numbers(lst[1:])
        if lst[0] % 2 == 0:
            return 1 + count_in_rest
        else:
            return count_in_rest
```

In this version of the function, we made the recursive call first, stored its return value in a variable, and then used that variable when deciding what to return. This approach can be useful to simplify the code of your recursive functions and to clarify the logic.

## Recursive binary search

At this point, we have mentioned binary search in multiple lessons, and even implemented it iteratively. Now, we are ready to implement a recursive version of binary search.

As before, binary search is suited for searching for a value in `O(logn)` time when the collection is sorted. Watch the following video to see how it is implemented.

> Insert video.

Here's the version of binary search from the video:

```python
def binary_search(lst, val, low, high):
    if low > high:
        return None
    else:
        mid = (low + high) // 2

        if lst[mid] == val:
            return mid
        elif val < lst[mid]:
            return binary_search(lst, val, low, mid - 1)
        else:
            return binary_search(lst, val, mid + 1, high)
```

> Reminder: `//` in Python performs integer division, which will truncate any fractional part of the result. For example, `7 // 2` is `3`.

<aside>
<b>Check your understanding</b>
<p>What's the base case in the recursive implementation of binary search above?</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> There are two base cases in the function. The first is when the value is found (<code>if lst[mid] == val</code>); in that case, the recursion can stop and the index of the value is returned. The other base case is when the value is not present in the list. This occurs when the condition <code>if low > high</code> is true, and the function returns <code>None</code>.</p>
</details>
</aside>

<aside>
<b>Check your understanding</b>
<p>Trace the execution of binary search for 8 on the list <code>[3, 5, 8, 15, 26, 38, 47, 136]</code>.</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> Here's a visualization of the execution using Python Tutor:</p>
<iframe width="800" height="500" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=def%20binary_search%28lst,%20val,%20low,%20high%29%3A%0A%20%20%20%20if%20low%20%3E%20high%3A%0A%20%20%20%20%20%20%20%20return%20None%0A%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20mid%20%3D%20%28low%20%2B%20high%29%20//%202%0A%0A%20%20%20%20%20%20%20%20if%20lst%5Bmid%5D%20%3D%3D%20val%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20return%20mid%0A%20%20%20%20%20%20%20%20elif%20val%20%3C%20lst%5Bmid%5D%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20return%20binary_search%28lst,%20val,%20low,%20mid%20-%201%29%0A%20%20%20%20%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20return%20binary_search%28lst,%20val,%20mid%20%2B%201,%20high%29%0A%0Alst%20%3D%20%5B3,%205,%208,%2015,%2026,%2038,%2047,%20136%5D%0Aprint%28binary_search%28lst,%208,%200,%20len%28lst%29%20-%201%29%29&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=0&heapPrimitives=nevernest&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>
</details>
</aside>
