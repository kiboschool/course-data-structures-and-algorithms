# Traversing a Linked List

So far, we have written algorithms to build linked lists, which have only operated at the beginning or the end of a linked list. However, many algorithms require us to iterate over (or *traverse*) an entire sequential data structure. So how is that done with linked lists?

## Printing an `LLString`

For a first example of traversing a list, let's see how we could use iteration to print an `LLString`:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/JYBBTuOzsrU"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

As shown in the video, this method of traversing a list is a common programming pattern. Here's a template that you can use:

```python
    def traversal(self):
        trav = self.head
        while trav is not None:
            # ... do something here
            trav = trav.next
```

<aside>
<b>Check your understanding</b>
<p>The following version of the <code>print()</code> function does not use a <code>trav</code> variable to walk down the list. Why is this incorrect?</p>
<pre><code class="language-python">def print(self):
    while self.head is not None:
        print(self.head.val, end='')
        self.head = self.head.next
    print()
</code></pre>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> Although this will print out the string (seemingly correctly), in the process it changes <code>self.head</code> and therefore loses the reference to the beginning of the list. In other words, it corrupts the linked list object. For this reason, you should always use a local variable to keep track of your position in the list as you walk down it.</p>
</details>
</aside>

## Recursively printing an `LLString`

Linked lists are a naturally recursive data structure, since each linked list is either:

* Empty
* A single node, followed by a linked list

For this reason, it is often easier to write recursive functions to operate on linked lists. For example, watch the following video to see how to recursively print a linked list:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/kn_bZVtwh2U"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

## Finding the length of a list

Your turn: either iteratively or recursively, write a method `length()` that returns the length of the linked list. If the list is empty, the function should return 0.

<br>
<iframe src="https://trinket.io/embed/python3/7e595b62cf" width="100%" height="356" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>

<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p>Here's the iterative version:</p>
<pre><code class="language-python">def length(self):
    trav = self.head
    count = 0
    while trav is not None:
        count += 1
        trav = trav.next
    return count
</code></pre>
<p>And here's the recursive version:</p>
<pre><code class="language-python">def length(self):
    return self.__length(self.head)
</code></pre>
<pre><code class="language-python">def __length(self, node):
    if node is None:
        return 0
    else:
        return 1 + self.__length(node.next)
</code></pre>
</details> 
