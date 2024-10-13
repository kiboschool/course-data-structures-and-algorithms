# Trees in Python

Now that we knows the basics of a tree data structure, we can start to think about how we would actually use one in Python.

Just as we saw with linked lists, there is also no built-in tree data structure in Python. There are tree libraries that you can import, but we won't do so in this class. Instead, it's instructive for us to build a tree class from first principles.

## The `LinkedTree` class

We will create a `LinkedTree` class to represent a binary tree, where each node in the tree has a value and two possible child pointers: a left and a right. To do so, we will need our tree to be composed of tree nodes, which we will create using a nested, inner class:

```python
class LinkedTree:
    class TreeNode:
        def __init__(self, val, left=None, right=None):
            self.val = val
            self.left = left
            self.right = right

    def __init__(self, root):
        self.root = root
```

Notice that each `TreeNode` will have a value, a (possibly `None`) left pointer, and a (possibly `None`) right pointer.

## Building a `LinkedTree`

Just like with linked lists, we *could* create some `TreeNode` objects, link them together manually, and use one of them as the root of a new `LinkedTree`. For example:

```python
n1 = TreeNode(5)
n2 = TreeNode(10)
n3 = TreeNode(7)
n1.left = n2
n1.right = n3
tree = LinkedTree(n1)
```

After constructing this tree, this is what the picture would look like in memory:

<center>
<img src="/images/week-08/linked-tree.png"
    class="center"
    alt="A tree variable on the stack, which holds a reference to a LinkedTree object on the heap. The LinkedTree object has a single instance variable, root, which holds a reference to a TreeNode with a value of 5. The left child of the 5 is a TreeNode with a value 10, and the right child of the 5 is a TreeNode with a value 7. Both the 10 and the 7 nodes have no child nodes."
    style="width:500px;" />
</center>

Note that we represent each `TreeNode` as a box with three parts: a left child pointer, a value, and a right child pointer.

## Building a tree with random values

We could also write a method to construct a random tree for us. Watch the video below to see how to build of height `h` filled with random values:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/Jh5jEwa0x9w"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

## Counting the number of nodes in a tree

With our `LinkedTree` class, we can now write algorithms that operate on the tree. See the below implementation of a `num_nodes()` method, which finds the number of nodes in a tree:

```python
def __num_nodes(self, node):
    if node is None:
        return 0

    return 1 + self.__num_nodes(node.left) + self.__num_nodes(node.right)

def num_nodes(self):
    return self.__num_nodes(self.root)
```

The basic algorithm is that the count of nodes in the tree is equivalent to 1 (for the root node) + the number of nodes in the left subtree + the number of nodes in the subtree. When applied recursively, this will count the total number of nodes in the tree.

> Note: It is much easier to write recursive algorithms on trees than iterative algorithms, since we need to be able to traverse *up and down* the tree. Making recursive calls and then returning from those recursive calls models this *up and down* traversal naturally. Therefore, we generally won't write iterative algorithms on trees, with some exceptions.

As always, we are interested in finding the time complexity of our algorithm. For `num_nodes()`, we make one recursive call for each node in the tree. As the number of nodes in the tree increases, the number of recursive calls increases linearly. Therefore, the running time of `num_nodes()` is `O(n)`.

<aside>
<b>Check your understanding</b>
<p>What's the running time of <code>num_nodes()</code> in the best case?</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> There is no distinction between the best, average, and worst cases for this algorithm. The algorithm only ever has one case: count the number of nodes in the tree.</p>
<p>Sometimes it is tempting to think something like "the best case is when the number of nodes in the tree is one -- then, it is an <code>O(1)</code> algorithm." However, remember that with big-O notation, we are only interested in analyzing the algorithm for very large sizes of <code>n</code>.</p>
</details>
</aside>

## Finding the depth of a node

Watch the video below to see how to write a method that finds the depth of a node:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/dsL5sJr0cso"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

<aside>
<b>Check your understanding</b>
<p>What's the running time of <code>depth()</code> in the best case and in the worst case?</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> Unlike with <code>num_nodes()</code> above, for <code>depth()</code> there <i>is</i> a distinction between the best case and worst case. The best case occurs when the node we are looking for is at the root of the tree, since in that case no recursive calls are needed and the method is <code>O(1)</code>. Notice that this case applies regardless of the number of nodes in the tree.</p>
<p>The worst case is when the node we are looking for is a last node in the tree that we inspect. In that case, we have made a recursive call for every node in the tree, and therefore it is <code>O(n)</code>.
</details>
</aside>
