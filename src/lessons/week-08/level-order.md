# Level Order Traversal

We mentioned in the previous lesson that visiting the nodes of a tree level-by-level, top to bottom is known as a *level-order* traversal. However, we haven't yet talked about how a level-order traversal is implemented.

Pre-order, in-order, and post-order traversals have a natural recursive implementation. A level-order traversal is actually easier to implement iteratively, but we will also need the help of queue to do it!

## Implementing a level-order traversal

The basic idea behind a level-order traversal is that we want to visit all of the nodes at level `h` before we visit the nodes at level `h + 1`. To do so, we can enqueue the children of each node as we encounter them:

```python
from collections import deque

def levelorder_print(self):
    q = deque()
    q.append(self.root)

    while len(q) > 0:
        node = q.popleft()
        print(node.val)

        if node.left is not None:
            q.append(node.left)

        if node.right is not None:
            q.append(node.right)
```

Watch the following video to see how a level-order traversal works:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/zn806uoIGp4"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

<aside>
<b>Check your understanding</b>
<p>Consider the following tree</p>
<center>
<img src="/images/week-08/level-order-practice.png"
    class="center"
    alt="A tree data structure with a 5 at the root node and 1 and 7 as its left and right children, respectively. The 1 node has 8 and 4 as its left and right children. The 8 has only a right child, which is a 9. The 4 node also has only a right child, which is a 2. The 7 node (in the right half of the tree) has only a 3 as its right node. The 3 has a 10 and 6 as its left and right children."
    style="width:300px;" />
</center>
What is the level-order traversal of the above tree?
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> <code>5, 1, 7, 8, 4, 3, 9, 2, 10, 6</code></p>
</details>
</aside>
