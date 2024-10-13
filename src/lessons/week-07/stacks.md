# Stacks

The next ADT that we will consider is a *stack*.

A stack is another sequential data structure, but unlike a list, it does *not* provide the ability to insert or access an element at an arbitrary position `i`. Instead, elements can only be added or removed at one end (the "top"), and you can only access the item that is currently at the top:

To learn more about stacks, watch the following video:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/F1F2imiOJfk"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

To summarize, stacks provide a *last in, first out* (LIFO) abstraction -- the most recently pushed item (*last in*) will be the first one popped (*first out*) during a removal. The stack ADT provides us with the following functions:

* `push()`: add an item to the top of the stack
* `pop()`: remove the item at the top of the stack
* `top()`: get the item at the top of the stack, but don't remove it
* `is_empty()`: test if the stack is empty
* `is_full()`: test if the stack is full

> **Note**: there is no need for an iterator for stacks. Stacks don't provide the abstraction that you can iterate over their contents -- you can only access the item at the top.

Stacks have many real-world applications, including:

* The runtime stack, on which stack frames are pushed and popped
* Evaluating mathematical expressions and programming language expressions
* Supporting "undo" operations in software (go back to the most recent state)

## Implementing a stack using an array

As with lists, we can think about how a stack could be implemented as an array. Watch the following video to see a sample implementation:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/mXYDhoKZsZI"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

## Implementing a stack using a linked list

We can also efficiently implement stacks using a linked list. Watch the following video to see how:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/QHRuo7mGz-c"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

## Summary

Let's summarize the tradeoffs between the array and linked list implementations of the stack ADT:

|                  | `ArrayStack`                             | `LLStack`                                |
|------------------|------------------------------------------|------------------------------------------|
| `push()`         | `O(1)` (on average)                      | `O(1)`                                   |
| `pop()`          | `O(1)`                                   | `O(1)`                                   |
| Space efficiency | `O(m)` (`m` is number of expected items) | `O(n)` (`n` is number of items in stack) |
