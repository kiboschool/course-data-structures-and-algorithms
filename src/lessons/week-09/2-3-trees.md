# 2-3 Trees

Binary search trees generally provide logarithmic-time search, insertion, and deletion. However, as we saw in the previous lesson, BSTs can become unbalanced, which causes the efficiency of those algorithms to drop to linear time.

To prevent this issue, there are BST variants that guarantee that the tree stays balanced. There are many such *balanced BST* variants, but we will focus on just one: *2-3 trees*.

## 2-3 trees

A 2-3 tree ("two-three tree") is a tree in which:

* All nodes have subtrees of equal height (perfect balance)
* Each node is either:
    * A 2-node ("two-node"), which contains a data item and 0 or 2 children
    * A 3-node ("three-node"), which contains a data item and 0 or 3 children
* The keys form a search tree

For example, the following is a 2-3 tree:

<center>
<img src="/images/week-09/2-3-tree.png"
    class="center"
    alt="A 2-3 tree. Each node has either two keys or three keys. The tree is perfectly balanced."
    style="width:475px;" />
</center>

## Search in 2-3 trees

Watch the following video to see how to search for a key in a 2-3 tree:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/CSanG6-4YPM"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

## Insertion in 2-3 trees

Watch the following video to see how to insert a new key in a 2-3 tree:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/3bQc1t089FU"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

## Efficiency of 2-3 trees

Since a 2-3 tree is always perfectly balanced, it *always* has a height <code>h = ~log<sub>2</sub>n</code>. Therefore, search, insertion, and deletion are all `O(logn)` algorithms in the worst case -- there is no possibility for them to devolve into `O(n)`!
