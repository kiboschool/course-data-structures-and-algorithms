# Doubly Linked Lists

A common variation of linked list is the *doubly* linked list. In this version, each node has both a `next` pointer as well as a pointer to the *previous* node, often called `prev` pointer. This makes it possible to traverse through the list in both directions, which makes some algorithms (such as deleting a node) easier to implement.

Watch the following video to learn more about doubly-linked lists:

> *Note*: there is a brief mention in the video of how to create a doubly linked list node in the C programming language using a `struct`. You can ignore this segment and just focus on the general ideas presented about doubly linked lists.

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/FHMPswJDCvU"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

<aside>
<b>Check your understanding</b>
<p>One of the main benefits of a doubly linked list is that it makes certain algorithms, such as deleting a node, easier to implement. What are the downsides to a doubly linked list (as opposed to a singly linked list)?<p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> Since each node in the linked list requires an additional <code>prev</code> pointer, the amount of memory needed in a doubly linked list is greater than that of a singly linked list. In addition, the linked list algorithms need to maintain the <code>prev</code> pointers as nodes are added and removed, which introduces a small amount of additional complexity to the code.</p>
</details>
</aside>
