# Modifying a Linked List

We've now learned how to build and traverse a linked list, but there is still one broad class of algorithms we still need to talk about: modifying an existing linked list.

## Deleting a node from a linked list

Watch the following video to see how to delete a node from a linked list:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/rSqg9Ur1TTI"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

## Inserting a node in a linked list

Instead of adding a new node to the beginning or end of a linked list, we may wish to add a node in the middle of the list -- at position `i`.

Using what you learned from the node deletion video above, try implementing the `insert()` function below. The function should create a new node with the value `new_val`, and insert the node into position `i` of the linked list. For example, if the list contains the string `'rat'`, then `insert('f', 2)` should change the linked list so that it contains the string `'raft'`.

If there is no position `i` of the list (i.e., the list is not long enough), the function should just add the node at the end of the list.

Remember to update `self.head` (and as an extra challenge, `self.tail`) if needed.

<iframe src="https://trinket.io/embed/python3/f0d16b554d" width="100%" height="356" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>

<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p>Here's a solution:</p>
<pre><code class="language-python">def insert(self, new_val, i):
    new_node = LLString.Node(new_val, None)
    trav = self.head
    prev = None<br>
    if i < 0:
        return<br>
    if trav is None:
        # list is empty
        self.head = new_node
        self.tail = new_node
        return<br>
    num = 0
    while num < i:
        prev = trav
        trav = trav.next
        num += 1
        if trav is None:
            # add to the end
            prev.next = new_node
            self.tail = new_node
            return<br>
    if i == 0:
        new_node.next = self.head
        self.head = new_node
    else:
        new_node.next = trav
        prev.next = new_node
</code></pre>
</details>
