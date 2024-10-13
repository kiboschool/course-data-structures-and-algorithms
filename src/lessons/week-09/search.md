# Search in BSTs

We mentioned in the previous lesson that ordering keys using the search-tree property allows us to write efficient tree algorithms. The foremost example of this is searching for the node with a given key (also known as a *lookup* or a *get*).

Since a BST is a dictionary, we often want to know: what is the item (or value) associated with a given key `k`? The search algorithm pseudocode is as follows:

* If `k` is equal to the root node's key, return the root node's item
* Else if `k` is less than the root node's key, search in the left subtree
* Else (`k` is greater than the root node's key), search in the right subtree

This logic can be applied recursively at each level of the tree. Since we know the ordering of the keys, we can ignore entire subtrees where `k` could not possibly be! This allows the search algorithm to follow a single path, starting from the root node and ending at the node with the key `k` (if it exists).

## Implementing search in a BST

Watch the video below to see the definition of a `LinkedBST` class that we will use for illustrating a binary search tree, as well as the implementation of the `search()` method:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/5Fp3dRUBSMg"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

<aside>
<b>Check your understanding</b>
<p>Why can searching for a node in a BST generally be more efficient than searching for a node in a regular (non-search) binary tree?</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> In a regular binary tree, we have no indication where the node with the requested value might be. Therefore, we generally have to search all of the nodes! In a BST, however, we can direct our search down a single path of the tree. We will more formally discuss the efficiency of BST algorithms in a couple of lessons.
</details>
</aside>
