# Queues

The final ADT that we will consider this week is the *queue*.

A queue is yet another sequential data structure. The main abstraction that it provides is a *first in, first out* (FIFO) policy: items are added at the rear and removed from the front, and you can only access the item that is currently at the front.

To learn more about queues, watch the following video:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/XuCbpw6Bj1U"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

To summarize, the queue ADT provides the following methods:

* `enqueue()`: add an item at the rear of the queue
* `dequeue()`: remove the item at the front of the queue
* `front()`: get the item at the front of the queue, but don't remove it
* `is_empty()`: test if the queue is empty
* `is_full()`: test if the queue is full

> **Note**: just like with stacks, there is no need for an iterator for a queue. It doesn't provide an iterable abstraction.

Since the FIFO abstraction is considered a "fair" policy in many real-world situations (e.g., "first come, first served"), queues have many applications across computer science and related operational fields. Any time a "request" of some kind needs to be served, it can be put in a queue, such as:

* Waiting in a virtual queue to buy tickets
* A Web server processing incoming HTTP requests for pages
* A printer serving requests for print jobs

## Implementing a queue using a linked list

Implementing a queue using a linked list can be easily done by maintaining both a `front` and `rear` reference to a linked list. Watch the following video to see how:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/bdQyL5y6tsg"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

A queue can also efficiently be implemented using an array, but the exact implementation of it is saved as a practice exercise for this week.

## Summary

Although we haven't yet covered the array implementation of a queue (you can find that as a practice problem), we can preview the efficiencies of the implementations below:

|                  | `ArrayQueue`<br>(see practice exercises)  | `LLQueue`                                |
|------------------|------------------------------------------|------------------------------------------|
| `enqueue()`      | `O(1)`                                   | `O(1)`                                   |
| `dequeue()`      | `O(1)`                                   | `O(1)`                                   |
| Space efficiency | `O(m)` (`m` is number of expected items) | `O(n)` (`n` is number of items in stack) |
