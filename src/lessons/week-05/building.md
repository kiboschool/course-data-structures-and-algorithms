# Building Linked Lists

To begin our study of linked lists in Python, let's start with the algorithm for constructing a linked list from scratch.

## A linked list string

To guide our study of linked lists, we will work with a string that is represented as a linked list of characters. Each node will contain a single character, and the linked list as a whole represents a string:

<center>
<img
  src="/images/week-06/llstring.png"
  alt="A linked list with five nodes, each with one letter of the string hello."
  style="width:350px;" />
</center>

In Python, strings are implemented using arrays of characters. However, using a linked list representation of a string will allow us to learn the basics of manipulating linked data structures with a familiar data type.

The linked list as a whole will be represented using an `LLString` object. Each individual node of the list will be represented using a `Node` object. We can define `Node` to be a class nested within the `LLString` class:

```python
class LLString:
    class Node:
        def __init__(self, val, next):
            self.val = val
            self.next = next

    def __init__(self):
        self.head = None
```

The `LLString` constructor simply initializes the `head` of the linked list to `None`. In order to actually add some nodes to the linked list, let's write a new method in this class.

## Adding a node to a linked list

Watch the video below to see how to add a node to the beginning of a linked list:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/iYdM_6kOpUA"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

<aside>
<b>Check your understanding</b>
<p>What's the time complexity of the <code>prepend()</code> method for the <code>LLString</code> class?</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> The running time is always <code>O(1)</code>. Regardless of the length of the list, a new node can always be added to the front of the list and <code>self.head</code> updated. Contrast this running time with arrays, which would require <code>O(n)</code> time to move over the other elements of the array, and also possibly resize the array.</p>
</details>
</aside>

## Appending a node to a linked list

What if we wanted to add a node to the *end* of the list? We have two options:

1. Starting at `self.head`, iterate all the way to the end of the list and add a node.
2. Maintain a reference to the end of the list (the *tail*), so that we can quickly add a new node.

We will see how to iterate down a linked list to do (1) in the next lesson. For now, let's focus on (2). To start, we will need to create `self.tail` in the `LLString` constructor, and also make sure that the `prepend()` function sets it when the first node is added to the list:

<pre><code class="language-python">class LLString:
    class Node:
        def __init__(self, val, next):
            self.val = val
            self.next = next

    def __init__(self):
        self.head = None
        <b>self.tail = None</b>

    def prepend(self, new_val):
        new_node = LLString.Node(new_val, self.head)
        self.head = new_node
        <b>if self.tail is None:
            self.tail = new_node</b>
</code></pre>

Now that we have `self.tail`, watch the video below to see how to add a node to the end of a linked list:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/P8b-K9ilZds"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

## Converting a string to a linked list

To make our work with `LLString` easier, let's update the constructor so that it converts a Python string to an `LLList`. To do so, we can make use of our new `append()` method:

```python
def __init__(self, s):
    self.head = None
    self.tail = None

    for char in s:
        self.append(char)
```

With this, we can create new linked lists with a single call:

```python
str1 = LLString('hello')
```

Putting it all together, here's our current version of the `LLString` class:

```python
class LLString:
    class Node:
        def __init__(self, val, next):
            self.val = val
            self.next = next

    def __init__(self, s):
        self.head = None
        self.tail = None

        for char in s:
            self.append(char)

    def prepend(self, new_val):
        new_node = LLString.Node(new_val, self.head)
        self.head = new_node

        if self.tail is None:
            self.tail = new_node

    def append(self, new_val):
        new_node = LLString.Node(new_val, None)

        if self.tail is not None:
            self.tail.next = new_node
        self.tail = new_node

        if self.head is None:
            self.head = new_node
```
