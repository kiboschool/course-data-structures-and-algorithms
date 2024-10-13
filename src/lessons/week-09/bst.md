# Binary Search Trees

Last week, we learned about binary trees. We will now spend some time talking about a specific type of binary tree: a *binary search tree*.

A binary search tree (BST) is a binary tree in which every node has a key `k`, and where the keys are ordered according to the *search-tree property*:

> **Search-tree property**
>
> For each node `k` (`k` is the key):
> * All nodes in `k`'s left subtree are < `k`
> * All nodes in `k`'s right subtree are > `k`

Here's a visualization of the search-tree property:

<center>
<img src="/images/week-09/search-tree-property.png"
    class="center"
    alt="A visualization of the search tree property. A root node labeled k, with a left subtree triangle lableed as < k, and a right subtree triangle labeled as <= k."
    style="width:225px;" />
</center>

The tree below is a binary search tree, since each node obeys the search-tree property:

<center>
<img src="/images/week-09/binary-search-tree.png"
    class="center"
    alt="A binary search tree. The root node is 8. It's left subtree consists of keys that are all less than 8, and its right subtree contains keys that are all greater than 8. This property is true for every node in the tree. For example, the 8 node's left child is a 3. All nodes in the 3 node's left subtree have keys less than 3, and all nodes in the 3 node's right subtree have keys greater than 3."
    style="width:275px;" />
</center>

<aside>
<b>Check your understanding</b>
<p>Consider the above binary search tree. Which traversal technique would visit the nodes in <i>ascending</i> order by key, i.e., <code>1, 3, 4, 5, 7, 8, 9, 10, 13</code>? Pre-order, in-order, post-order, or level-order?</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> An <i>in-order</i> traversal always prints the keys of a binary search tree in ascending order.</p>
</details>
</aside>

Ordering the tree turns out to be very valuable, as it will allow us to write efficient tree algorithms. However, before we discuss this efficiency aspect, let's talk about another feature of BSTs: they are an example of a data *dictionary*.

## Data dictionaries

A dictionary is an ADT that stores (key, value) pairs, where each key can appear at most once. It supports the following operations:

* `insert(key, value)`: insert a new (key, value) pair
* `delete(key)`: given a key, delete the corresponding (key, value) pair
* `lookup(key)`: lookup the value associated with the given key

Other names for a data dictionary include a *map* (maps keys to values) and *associative array* ("array" of keys associated with values).

<aside>
<b>Check your understanding</b>
<p>What are some real-world examples of data dictionaries?</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> Anything that maps a key to a value is a dictionary. For example, a "dictionary" in the common sense of the word refers to a book that maps words to their definition. A phone book is another example; it maps names to phone numbers.</p>
</details>
</aside>

A binary search tree is an implementation of a dictionary. Each node in the tree has a key (recall: the BST is ordered by the keys) and also contains a value. Often, the values associated with each node are not shown, as in the case of the example BST from earlier in the lesson.

## Overview of BSTs

Watch the video below to see an overview of BSTs:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/pYT9F8_LFTM"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>
