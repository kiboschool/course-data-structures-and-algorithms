# Tree Basics

Up to this point, the data structures that we have considered have been linear -- they have modeled data as being in a sequence. However, there can be non-linear relationships in data as well -- for example, some relationships in data are hierarchical.

Examples of hierarchical relationships include:

* Managers and employees in an organization
* Ancestors and descendants in a family tree
* Directories and files in filesystems

Hierarchical data can be represented using a *tree*. Watch the following video to learn about trees as a data structure:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/qH6yxkw0u78"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

To summarize:

* Trees are (typically) linked data structures composed of *nodes* and *edges* (also known as *links*).
* At the "top" of the tree, there is a *root* node.
* Each node has zero or more *child* nodes. Nodes that don't have any children are *leaf* nodes. Nodes that have at least one child are *interior* nodes.
* Each node (except for the root) has a *parent* node.
* Trees are naturally recursive data structures. Each tree is a root node connected to *subtrees* starting from the root node's children.
* The *depth* of a node is the number of links on the path from the root to the node. The *height* of a tree is the maximum depth among all nodes.
* A common type of tree is a *binary tree*, in which nodes have two child pointers to *left* and *right* children.

<aside>
<b>Check your understanding</b>
<p>Consider the following tree</p>
<center>
<img src="/images/week-08/tree.png"
    class="center"
    alt="A tree data structure with a 2 at the root node and 7 and 5 as its left and right children, respectively. The 7 has three children itself: 2, 10, and 6. The 6 further has two children itself: another 5 and an 11. Back up at the original 5 (which was a child of the root node), it itself has a 9 as a child, which in turn has a 4 as a child."
    style="width:250px;" />
</center>
<ol>
  <li>Which nodes are leaf nodes?</li>
  <li>What's the parent of the 6 node?</li>
  <li>What's the depth of the 9 node?</li>
  <li>What's the height of the tree?</li>
  <li>Which has more nodes: the 2's left subtree or the 2's right subtree?</li>
</ol>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b></p>
<ol>
  <li>The 2, 10, (lower) 5, 11, and 4 nodes.</li>
  <li>The 7 node.</li>
  <li>2</li>
  <li>3</li>
  <li>There are six nodes in the left subtree and three nodes in the right subtree.</li>
</ol>
</details>
</aside>
