# Stacks & Queues in Python

Now that we've learned about stacks and queues in general, let's think about how you might actually use stacks and queues in the context of Python programs.

Although we built various versions of these data structures for educational purposes, you likely wouldn't actually use them in a program. Instead, Python provides some implementations that you may find useful.

## Stacks in Python

A Python list provides the ability to function as a stack. Strictly speaking, a stack doesn't have access to arbitrary elements of the list, as a Python list does. However, a stack can be simulated by only using methods that operate at the end of the Python list -- the "top" of the "stack."

To push an element onto the stack, use the Python lists's `append()` method. As we've seen many times before, this adds an element to the end of the list. In some cases, this can require the underlying array to be resized, but in most cases it is an efficient operation.

To *pop* an element from the stack, use the `pop()` method. This removes and returns the last element of the Python list.

Here's an example that pushes some elements on a stack and then pops them:

<iframe src="https://trinket.io/embed/python3/63a0468993" width="100%" height="356" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>

## Queues in Python

In theory, a Python list could also be used to implement a queue. The `append()` method could again be used to insert items at the rear of the "queue," and then the `pop()` method could be used with an optional parameter to remove the item at index 0 (the front of the "queue"):

<iframe src="https://trinket.io/embed/python3/076f51ad50" width="100%" height="356" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>

However, this approach is not efficient, since calling `pop(0)` requires shifting all elements of the Python list to the left.

<aside>
<b>Check your understanding</b>
<p>What's the time complexity of <code>pop(0)</code> on a Python list?</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> <code>pop(0)</code> is used to remove the item from the first position of the list, which requires shifting over all other elements by one position to the left. Therefore, <code>pop(0)</code> is an <code>O(n)</code> operation.
</details>
</aside>

Instead of using a Python list, you can use a `deque` from the `collections` library when you need a queue in Python.

A "deque" is a *double-ended queue* -- a queue that supports efficient enqueue and dequeue operations from either end of the collection. To use it in the traditional sense of a queue, use `append()` to enqueue items at the rear of the queue, and `popleft()` to dequeue items from the front of the queue:

<iframe src="https://trinket.io/embed/python3/e130167ca4" width="100%" height="356" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>
