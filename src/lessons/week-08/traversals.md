# Tree Traversals

In this lesson, we will think about how to traverse over a tree in a pre-defined, standard way.

All of the previous data structures that we have considered were linear, and iterating over a linear data structure has an obvious beginning and end. However, with a tree, the order in which we visit the nodes of the tree in an algorithm is not obvious. For example, consider the following tree:

<center>
<img src="/images/week-08/binary-tree.png"
    class="center"
    alt="A binary tree. The root is a 1, whose left and right children are 2 and 3. The 2 node's left and right children are 4 and 5. The 5 node's left and right children are 7 and 8. The 3 node has only a right child, which is a 6. The 6 node has only a left child, which is a 9."
    style="width:300px;" />
</center>

One way of traversing this tree would be in *level-order*: the nodes are visited one level at a time, from top to bottom. A level-order traversal would therefore visit the nodes in the order `1 2 3 4 5 6 7 8 9`.

However, we've already written an algorithm that does not visit the nodes in level-order! The `num_nodes()` method from the previous lesson, for example, accounted for the root node in the count, then recursively visited the left subtree, and then recursively visited the right subtree:

```python
def __num_nodes(self, node):
    if node is None:
        return 0

    return 1 + self.__num_nodes(node.left) + self.__num_nodes(node.right)
```

For the above tree, `__num_nodes()` would have visited the nodes in the order `1 2 4 5 7 8 3 6 9`.

Often, it does not matter the order in which the nodes are visited. For some scenarios, such as evaluating an algebraic expression that is modeled as a tree, the order *does* matter. Therefore, there are some well-known traversal orders, described below.

## Pre-order traversal

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/1WxLM2hwL-U"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

To summarize, a *pre-order* traversal of a binary tree first visits the current node, then visits the current node's left subtree, and then recursively visits the current node's right subtree:

```python
def __preorder_print(self, cur):
    if cur is None:
        return

    print(cur.val)
    self.__preorder_print(cur.left)
    self.__preorder_print(cur.right)

def preorder_print(self):
    self.__preorder_print(self.root)
```

## In-order traversal

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/5dySuyZf9Qg"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

An *in-order* traversal of a binary tree first visits the left subtree recursively, then visits the current node, and then visits the right subtree recursively:

```python
def __inorder_print(self, cur):
    if cur is None:
        return

    self.__inorder_print(cur.left)
    print(cur.val)
    self.__inorder_print(cur.right)

def inorder_print(self):
    self.__inorder_print(self.root)
```

## Post-order traversal

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/4zVdfkpcT6U"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

An *post-order* traversal of a binary tree first visits the left subtree recursively, then visits the right subtree recursively, and then visits the current node:

```python
def __postorder_print(self, cur):
    if cur is None:
        return

    self.__postorder_print(cur.left)
    self.__postorder_print(cur.right)
    print(cur.val)

def postorder_print(self):
    self.__postorder_print(self.root)
```

<aside>
<b>Check your understanding</b>
<p>Consider the following tree</p>
<center>
<img src="/images/week-08/binary-tree-practice.png"
    class="center"
    alt="A tree data structure with a 5 at the root node and 5 and 3 as its left and right children, respectively. The 5 node has 1 and 4 as its left and right children. The 1 has only a right child, which is a 2. The 3 node has 9 and 7 as its left and right children. The 9 has only a right child, which is a 6."
    style="width:300px;" />
</center>
<ol>
  <li>What is the pre-order traversal of the above tree?</li>
  <li>What is the in-order traversal of the above tree?</li>
  <li>What is the post-order traversal of the above tree?</li>
</ol>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b></p>
<ol>
  <li><code>8, 5, 1, 2, 4, 3, 9, 6, 7</code></li>
  <li><code>1, 2, 5, 4, 8, 9, 6, 3, 7</code></li>
  <li><code>2, 1, 4, 5, 6, 9, 7, 3, 8</code></li>
</ol>
</details>
</aside>
