# Iterators

Let's now use one of our list implementations to solve a problem: counting the number of times a given item appears in a list.

We can write a function to do so. However, let's write it from the perspective of a program that it *outside* of the `ArrayList` or `LLList` class:

```python
from lllist import LLList
import random

def count(list_impl, item):
    total = 0
    for i in range(list_impl.length()):
        list_item = list_impl.get_item(i)
        if list_item == item:
            total += 1
    return total

# create a new LLList
my_list = LLList()

# add one million random numbers to the list
for i in range(10000):
    my_list.add_item(random.randint(1, 100), 0)

# count how many times 13 is in the list
print(count(my_list, 13))
```

This program creates a new list, adds one million random numbers to it, and then counts the number of times 13 appears in the list.

However, there's something surprising about this function: it is inefficient! To see why, watch the following video:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/a6XLD0HLsmE"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

To summarize, the `count()` function as written above is efficient when the list that is passed in as a parameter is an `ArrayList`. However, when an `LLList` is passed in as a parameter, the function isn't very efficient.

To fix this issue, we'll need to use an iterator.

## Iterators

An *iterator* is an object that can be used to maintain state about the current position of a traversal over a data structure. The main benefit of an iterator is that it allows functions *outside* of the data structure's class to efficiently iterate over an instance of a data structure.

Iterators typically have just two methods:

* `has_next()`: whether there is another item in the traversal
* `next()`: returns the next item and advances the iterator

Functions can then create iterators and call these methods. For example, the `count()` method could be changed to use an iterator:

<pre><code class="language-python">def count(list_impl, item):
    total = 0
    <b>it = list_impl.iterator()</b>
    <b>while it.has_next()</b>:
        list_item = <b>it.next()</b>
        if list_item == item:
            total += 1
    return total
</code></pre>

In order for each implementation of the list ADT to have an iterator, we can add an `iterator()` method to the list of expected methods:

* `iterator()`: returns an iterator for the list

## Making an efficient `LLList` iterator

Watch the video below to see how to make an efficient iterator for the `LLList` class:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/gYQW_yF0y3Q"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

By using the iterator, we've improved the time complexity of the `count()` function from <code>O(n<sup>2</sup>)</code> to `O(n)`!

<aside>
<b>Check your understanding</b>
<p>In the above video, we added an iterator for the <code>LLList</code> class. However, in order for the <code>count()</code> function to work if <code>list_impl</code> is an <code>ArrayList</code>, we also need to implement the iterator the <code>ArrayList</code> class. What would the implementations of the <code>has_next()</code> and <code>next()</code> methods look like?
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> This is the implementation of the <code>ArrayListIterator</code>:</p>
<pre><code class="language-python">class ArrayList:
    ...<br><br>
    class ArrayListIterator:
        def __init__(self, items, num_items):
            self.i = 0
            self.items = items
            self.num_items = num_items<br>
        def has_next(self):
            return self.i < self.num_items<br>
        def next(self):
            item = self.items[self.i]
            self.i += 1
            return item<br><br>
    def iterator():
        return ArrayListIterator(self.items, self.num_items)
</code></pre>
<p>The <code>iterator()</code> method simply creates a new <code>ArrayListIterator</code> object, and passes in the list of items (and the number of items). This allows the iterator to access the data. In its constructor, the iterator also initializes a variable <code>self.i</code> to use as the index of where the iterator currently is in the list.</p>
<p>The <code>has_next()</code> method just needs to check whether the index has moved past the number of items yet.</p>
<p>The <code>next()</code> method is also quite simple: it just saves the item at index <code>i</code>, advances the iterator, and returns the item.</p>
</details>
</aside>
