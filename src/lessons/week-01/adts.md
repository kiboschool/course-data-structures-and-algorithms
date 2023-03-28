# Abstract data types

Let's now leave behind efficiency and metrics for the moment, and touch on another building block that will resurface repeatedly in this course: *abstract data types*, or ADTs.

## What are ADTs?

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/HkUTnW_v4yM"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

To summarize, ADTs define the semantics of how a data structure should behave, including the operations that the data structure should support. However, an ADT doesn't define how the data structure should be implemented -- it is only an *abstract* description.

## ADTs and Python

Now that we know what an ADT is in general terms, let's think about how to use ADTs in code.

Python does not have a specific language feature that represents an ADT. When we need to implement an ADT using a Python class, we will include the name of the ADT in the class name. This way, we will have a hint about the expected behavior of objects of that class.

For example, if we wanted to create a list-based implementation of a tuple as described in the video, it might look like this:

```python
class ListTuple:
    def __init__(self, a, b):
        self.items = [a, b]

    def get_item_a(self):
        return self.items[0]

    def get_item_b(self):
        return self.items[1]

    def set_item_a(self, new_a):
        self.items[0] = new_a

    def get_item_b(self, new_b):
        self.items[1] = new_b
```

Under the hood, the tuple abstraction is implemented as a Python list. On the other hand, if we wanted to create a variable-based representation of a tuple, it would look like this:

```python
class TwoVariableTuple:
    def __init__(self, a, b):
        self.a = a
        self.b = b

    def get_item_a(self):
        return self.a

    def get_item_b(self):
        return self.b

    def set_item_a(self, new_a):
        self.a = new_a

    def get_item_b(self, new_b):
        self.b = new_b
```

Both `ListTuple` and `TwoVariableTuple` provide the operations of a tuple, just implemented in different ways!

You might be wondering at this point why we would need to have multiple implementations of an ADT if they provide the same behavior. The answer is efficiency. One implementation of an ADT might be more efficient than another implementation of an ADT. Once we see more fundamental ways of organizing data other than lists, the differences in efficiency in how we implement ADTs will become clearer.

<aside>

**ADTs in other languages**

Unlike Python, some other programming languages have constructs that specifically represent ADTs. For example, Java has language features such as *interfaces* and abstract classes, which allow you to define the expected behavior of an ADT (its method signatures), without specifying how it is implemented. Other classes will then implement those interfaces by defining the methods. The key is that if a class promises to implement an ADT but does not define one or more of the methods of the ADT, it will not *compile* (i.e., it will not be able to be executed).

Python doesn't work this way. Python checks whether a method can be found and called at runtime -- while the program is executing. Therefore, there is no way to "promise" ahead of time that a class implements a certain method, and interfaces are not necessary.

If you're interested in reading about ways Python can have something like an ADT, check out this [optional reading](https://realpython.com/python-interface). However, we won't be using any of these techniques in this course.

</aside>

<aside>
<b>Check your understanding</b>

Consider the following ADT: a <i>set</i>. A set has the following operations: (1) insert an item into the set, (2) check whether the set contains an item, and (3) delete an item from the set. There is no concept of "position" -- i.e., you can't say <i>give me the fourth item in the set</i>.

How could you implement this ADT in Python? Provide a high-level description of the kind of class you would write.
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>

<b>Answer.</b> You could write a Python class that uses a list to hold the items in the set. The class should have three methods: one for inserting items into the list (you can just append the given item to the end of the list if it does not already exist in the list), one for checking whether an item is in the list (perhaps using the `in` operator), and one for iterating over the list to delete the item.

</details>
</aside>
