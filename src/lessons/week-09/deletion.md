# Deletion in BSTs

Sometimes, we may wish to delete a (key, value) pair from a BST. When we do so, we must be careful to maintain the search-tree property even after the deletion is complete.

When deleting a node, we must start at the root of the tree and traverse the path to the node to be deleted. If the node is found, then there are three different scenarios to consider: when the node to delete has no children (a leaf node), when it has one child, and when it has two children.

## Case 1: node to delete is a leaf node

This is the simplest case. When we want to delete a leaf node *X*, we simply need to delete *X*'s parent's reference to *X*. For example, say that we wanted to delete the 7 node in the tree below:

<center>
<img src="/images/week-09/bst-delete-node-1.png"
    class="center"
    alt="A binary search tree. One of leaf nodes, which contains the key 7, is highlighted."
    style="width:500px;" />
</center>

To do so, we only need to set the 5 node's right child reference to `None`.

## Case 2: the node to delete has one child

When the node to delete (*X*) has one child, we take the parent's reference to *X* and make it instead point to *X*'s child. For example, if we wanted to delete the 13 node, then we would change the child pointer of the parent (the 9 node) so that it references the 10 node:

<center>
<img src="/images/week-09/bst-delete-node-2.png"
    class="center"
    alt="A binary search tree. One of the nodes, which has a key 13 and only has one child, is highlighted."
    style="width:500px;" />
</center>

## Case 3: the node to delete has two children

When deleting a node with two children, we need to be careful. Once the node is deleted, we need the BST to still obey the search-tree property for all nodes and subtrees.

To delete a node *X* with two children:

1. Find the smallest (minimum) node in *X*'s right subtree. Call this node *Y*.
2. Replace *X*'s key and value with the key and value from *Y*.
3. Delete the original *Y*.

For example, if we wanted to delete the 3 node, we would first replace it with the 4 node (since the 4 node is the smallest in the 3 node's right subtree). Then, we delete the original 4 node:

<center>
<img src="/images/week-09/bst-delete-node-3a.png"
    class="center"
    alt="A binary search tree. One of the nodes, which has a key 13 and only has one child, is highlighted."
    style="width:750px;" />
</center>

In this case, the original 4 node had no children, and so it was easy to delete -- you could consider an example of a Case 1 deletion. However, it's also possible that the smallest node in the right subtree has a child. For example, if we wanted to delete the root (the 8 node), then we would replace it with the 9 node. When deleting the original 9 node, it is a Case 2 deletion, and we therefore set the new 9's right child to be the 13 node:

<center>
<img src="/images/week-09/bst-delete-node-3b.png"
    class="center"
    alt="A binary search tree. One of the nodes, which has a key 13 and only has one child, is highlighted."
    style="width:750px;" />
</center>

<aside>
<b>Check your understanding</b>
<p>In the two Case 3 examples above, the smallest node in the right subtree had either no children or one child. Why is it not possible for the smallest node in the right subtree to have two children?</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> If the smallest node in the right subtree (<i>Y</i>) has two children, that necessarily means it has a left child. However, if <i>Y</i> has a left child, then that child must be less than <i>Y</i> -- meaning <i>Y</i> is not the smallest in the right subtree!</p>
</details>
</aside>

<aside>
<b>Check your understanding</b>
<p>When deleting a node with two children, we chose to find the smallest node in the subtree. However, there is another, equivalent option available. What could we do instead?
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> We could find the <i>largest</i> (maximum) node in the <i>left</i> subtree.</p> The rest of the algorithm would stay the same!
</details>
</aside>
