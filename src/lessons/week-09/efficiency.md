# Efficiency of BSTs

Up to this point, we have looked at three of the main BST algorithms: search, insertion, and deletion. However, we haven't remarked on their efficiencies yet. Actually, the way we analyze all of their time complexities will be the same, so it makes sense to discuss it all at once.

Before we talk about the efficiency of these BST algorithms, let's think first about the efficiency of other tree algorithms that we've seen.

## Efficiency of "regular" tree algorithms

Last week, when we considered non-search trees, we basically saw two types of algorithms:

1. Algorithms that *always* need to visit every node in the tree (i.e., always `O(n)`). Tree traversals and counting the number of nodes fall into this category.

2. Algorithms that can *sometimes* terminate before visiting every node. For example, when trying to find a depth of a node, in the best case the node we're searching for is at the root of the tree (`O(1)`). In the worst case, we need to look at all nodes (`O(n)`).

With BSTs, we have a third common type of algorithm:

3. Algorithms that can focus on a particular *path* in the tree. They don't need to look at all nodes -- they follow a path from the root down to a particular node.

<aside>
<b>Check your understanding</b>
<p>Actually, one of the Huffman tree algorithms that we learned last week was of this "path-following" variety. Which one?</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> When decoding a string using a Huffman tree, we start at the root node and follow a path in the tree as dictated by the 0s and 1s in the string (0 --> go left, 1 --> go right).
</details>
</aside>

## Efficiency of BST algorithms

With binary search trees, the search-tree property often allows algorithms to ignore entire subtrees and proceed down a particular path of the tree. For example, during `search()`, we were able to focus on a particular path down only the parts of the tree where it was possible for the given key to be found.

In the worst case, whenever we were searching, inserting, or deleting a node, we had to traverse from the root node all the way down to a leaf node. In other words, we traversed a path throughout the *height* `h` of the tree. Therefore, we could say that search, insertion, and deletion are all `O(h)` algorithms in the worst case.

<aside>
<b>Check your understanding</b>
<p>What is the best-case time complexity of the BST algorithms for searching, insertion, and deletion?
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> The best-case time complexity for all three algorithms is <code>O(1)</code>.</p>
<p>In search, the best case scenario occurs when the key we're looking for is in the root node.</p>
<p>In deletion, the best case occurs when the key we want to delete is in the root node.</p>
<p>In insertion, the best case occurs when the root node has no right subtree, and we are inserting a key that is greater than the root node's key. (Or, equivalently, when the root node has no left subtree, and the key we are inserting is less than the root node's key.)</p>
</details>
</aside>

## Balanced vs. unbalanced trees

We now know that in the worst case, searching and the related algorithms for BSTs is `O(h)`, where `h` is the height of the tree. Ideally, the height of the tree is approximately `logn`, where `n` is the number of nodes in the tree:

<center>
<img src="/images/week-09/bst-balanced.png"
    class="center"
    alt="A binary search tree with three levels that are completely full, which is a balanced tree."
    style="width:375px;" />
</center>

The height of this tree is `logn` because of the branching structure of the tree. Each interior node has a left and right child, which essentially divides the number of nodes to fill out the tree by *two* at each node. Therefore, to be specific about the base of the logarithm, the height is approximately<code>log<sub><b>2</b></sub>n</code> levels.

However, not all BSTs are *balanced* in this manner. Depending on how the keys of the BST are inserted, the tree may become unbalanced. For example, if we inserted all of the keys of a BST in sorted order, we would end up with a tree that has only right children:

<center>
<img src="/images/week-09/bst-height-worst.png"
    class="center"
    alt="A binary search tree that has only right children. The tree therefore takes the shape of a linked list."
    style="width:475px;" />
</center>

In this case, the height `h` is exactly `n - 1` = `O(n)`. Therefore, the BST algorithms would all be `O(n)`!

## Summary

To summarize, here are the time complexities of the three main BST methods:<br>

|                                 | Search    | Insertion | Deletion |
|---------------------------------|-----------|-----------|----------|
| Best Case                       | `O(1)`    | `O(1)`    | `O(1)`   |
| Average Case<br>(balanced tree) | `O(logn)` | `O(logn)` | `O(logn)`|
| Worst Case<br>(unbalanced tree) | `O(n)`    | `O(n)`    | `O(n)`   |

Clearly, it would be beneficial to avoid the worst case performance of unbalanced trees. We look at *balanced* BSTs next.
