# Lists

We spent the first half of the course building our toolbox with the knowledge, skills, and programming constructs needed to create and use data structures, including:

* The memory model of Python
* Big-O notation
* Recursion
* Arrays and linked lists

With this knowledge, we are finally ready to describe some new ADTs! We will start with a "list."

## The list ADT

A *list* is a data structure in which items can be inserted, accessed, and removed from *any* position. In other words, a list has the following properties:

* Order matters: you can ask to insert, get, or remove an element at a specific position `i`
* Duplicates are allowed: there is no restriction regarding duplicates

It might be helpful to contrast the idea of a list with the set ADT, in which order did not matter (we could only grab a random element) and duplicates were *not* allowed.

To go along with our ADT, we can specify some operations that we want lists to support:

* `get_item(i)`: get the item at position `i`
* `add_item(item, i)`: add the specified item at position `i`
* `remove_item(i)`: remove the item at position `i`
* `length()`: get the number of items in the list
* `is_full()`: test if the list already has the maximum number of items
* `to_string()`: return a string representation of the list

The methods for the list ADT above are just defined for our purposes in this class -- there is no specific set of methods that a "list" is required to support in general. For example, Python's built-in list data structure is similar to this definition of the list ADT. However, it doesn't have any concept of being "full" (and so doesn't have a `is_full()` method) and also has other functionality, such as slicing.

## Linked lists vs. lists vs. Python lists

At this point we have learned about a few entities that are all called *lists*, so let's take a moment to remember the differences between them.

A *linked list* is a building block data structure in which data is connected using nodes and references. It can used to implement various ADTs.

A *list* is an ADT that represents a sequential collection of data where order matters and duplicates are allowed. It could be implemented in various ways, including using an array or a linked list.

A *Python list* is a Python-specific implementation of the list ADT, which uses an array under the hood along with some additional functionality (e.g., slicing).

## Implementing a list using an array

After creating the list ADT, the next question to ask is how should we implement it? Since a list is a sequential data structure, it's natural to consider an array.

Of course, since arrays don't exist as a built-in feature of Python, we will use Python lists. But recall that Python lists are implemented using arrays, so we need to keep that in mind as we use Python lists to implement the list ADT.

Watch the video below to see how the list ADT could be implemented using a Python list (i.e., an array):

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/52MZTc4ceH0"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

<aside>
<b>Check your understanding</b>
<p>What's the time complexity of the <code>remove_item()</code> method for the <code>ArrayList</code> class in the best case and in the worst case?</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> In the best case, if asked to remove the last item in the list, then no elements have to be copied over, and the running time is therefore <code>O(1)</code>. However, in the worst case (and in the average case), we have to shift over <code>O(n)</code> elements when removing an item from the middle or beginning of the list, and therefore the running time is <code>O(n)</code>.
</details>
</aside>

<aside>
<b>Check your understanding</b>
<p>In the <code>add_item()</code> method, to insert an item at position <code>i</code> we used a loop that started at the end of the list of items (<code>self.length - 1</code>), and moved over each item one-by-one until we reached item <code>i</code>:
<pre><code class="language-python">for j in <b>range(self.length - 1, i - 1, -1)</b>:
    self.items[j + 1] = self.items[j]
</code></pre>
The loop proceeded from right to left. If you tried to implement the loop by iterating from element <code>i</code> up to element <code>self.length - 1</code> (left to right), it would look like this:
<pre><code class="language-python">for j in <b>range(i, self.length)</b>:
    self.items[j + 1] = self.items[j]
</code></pre>
However, this won't work. Why not?
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> If you move the elements over from left-to-right, you will just end up copying the element at index <code>i</code> throughout the list -- into <i>every</i> position that the loop touches.
</details>
</aside>

## Implementing a list using a linked list

The other natural choice for implementing the list ADT would be to use a linked list. Watch the video below to see how this would work:

> **Note**: The class name `LLList` was chosen because it is the *linked list* (LL) implementation of a *list*.

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/kBG7IxExlm8"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

## Summary

Let's summarize the tradeoffs between the array and linked list implementations of the list ADT:

|              | `ArrayList`         | `LLList`                     |
|--------------|---------------------|------------------------------|
| `get_item()` | `O(1)` in all cases | Best: `O(1)` (`get_item(0)`)<br><br>Average/Worst: `O(n)` (getting item at middle/end)|
| `add_item()` | Best: `O(1)` (adding to end)<br><br>Average/Worst: `O(n)` (adding to beginning/middle) | Best: `O(1)` (`add_item(0)`)<br><br>Average/Worst: `O(n)` (adding to middle/end) |
