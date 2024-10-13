# Insertion in BSTs

Now that we have seen how to search in a BST, let's think about how to construct a BST. In other words, how is a (key, value) pair inserted into a tree?

Here's the pseudocode for the algorithm to insert a new (key, value) pair `(k, v)`:

* Search for `k` in the BST. If it already exists, return without modifying the tree.
* If we don't find a node with key `k`, then the last node in the search will become the parent <b>P</b> of the new node <b>N</b>.
    * If `k` is less than <b>P</b>'s key, then <b>N</b> will become <b>P</b>'s new left child.
    * Otherwise (`k` is greater than <b>P</b>'s key) <b>N</b> will become <b>P</b>'s new right child.

After the insertion algorithm completes, the BST will maintain the search-tree property!

> Note: different BST variants may handle the case of `k` already existing differently. For example, they may choose to overwrite the value associated with `k`, or may maintain a *list* of values for each key.

<aside>
<b>Check your understanding</b>
<p>Consider the below binary search tree:</p>
<center>
<img src="/images/week-09/binary-search-tree.png"
    class="center"
    alt="A binary search tree. The root node is 8. Its left and right children are 3 and 9, respectively. The 3 node's left and right children are 1 and 5, respectively. The 5 node's left and right children are 4 and 7, respectively. The 9 node's right child is 13. The 13 node's left child is 10."
    style="width:225px;" />
</center>
How would the tree change after inserting a new node with key 11?
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> By following the algorithm, we would first search for where 11 would be found in the tree if it existed. Starting from the root, 11 is greater than 8, so we go right. 11 is also greater than 9, so we go right again to the 13. 11 is lesser than 13, so we go left to the 10. 11 is greater than 10, so we create a new node to contain the 11 and make it the 10's right child.
</details>
</aside>

## Implementing insertion in BSTs

Watch the video below to see how to implement the insertion algorithm on a BST:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/BxPEEm3rRos"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

<aside>
<b>Check your understanding</b>
<p>Last week, we said that most of the binary tree methods we implement would be recursive. However, the <code>insert()</code> method written in the video was iterative. Why is that?
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> In a regular (non-search) binary tree, most algorithms require us to process <i>every</i> node in the tree, which means we must traverse up and down the tree to enter the different subtrees. This is most easily achieved by using recursive calls and the runtime stack. However, with BSTs, algorithms often focus on a particular <i>path</i> of the tree, which doesn't require going back "up" in the tree, and so it can easily be performed either iteratively or recursively.</p>
</details>
</aside>
