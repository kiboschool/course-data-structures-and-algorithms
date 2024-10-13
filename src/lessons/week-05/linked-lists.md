# Linked Lists

*Linked lists* are a fundamental alternative to arrays for building data structures. Instead of storing the items of the collection contiguously in a fixed amount of memory (as in arrays), a linked list stores the collection in separate *nodes*:

<center>
<img
  src="/images/week-06/linked-list-1.png"
  alt="A variable named llst on the stack referencing a node object on the heap. The node object contains two fields: an integer 14, and a reference to another node object. The second node object contains an integer 91 and a reference to yet another node object. The third node object contains an integer 45 and the value None instead of a reference to another node object."
  style="width:500px;" />
</center>

Each node is an object that contains two items: a value (in the example above, an integer value) and a "next" pointer -- i.e., a reference to the next node in the list. The last node in the list has a next pointer value of `None`.

The linked list as a whole is represented by a variable (`head` in the example above) that holds a reference to the first node in the list -- the "head" of the linked list.

## Linked lists in memory

The nodes of the linked lists don't need to be stored consecutively in the heap region of memory. In fact, they can be stored at mostly arbitrary memory locations. This is the reason that each node needs to store the memory address of the next node in the list. To illustrate this concept, here's another view of the same linked list, but instead of using arrows to represent memory addresses, we will write the (made up) memory addresses:

<center>
<img
  src="/images/week-06/linked-list-2.png"
  alt="The same linked list as above, except instead of arrows connecting the nodes of the linked list, the diagram shows the memory addresses. The stack variable llst holds the value 712, which is where the first node in the list is stored in memory. The first node's next field holds the value 590, which is where the second node in the list is stored, etc."
  style="width:500px;" />
</center>

This is in contrast to arrays, which as we learned in the previous lesson, store elements in consecutive memory locations:

<center>
<img
  src="/images/week-06/array-4.png"
  alt="A diagram of a variable referencing an array. The stack variable contains the memory address of the array, which is the value 500, which is the memory address of the array overall. Each element of the array is at a consecutive index: the first element is at memory address 500, the second element of the array is at memory address 504, etc."
  style="width:350px;" />
</center>

This difference in memory representation between arrays and linked lists has profound effects on how they are used.

## Features of linked lists

Because each linked list is composed of a sequence of separate nodes, they can grow indefinitely (provided there is enough memory) -- they don't need to be resized when they reach capacity, as arrays do.

In addition, it's easy to insert or delete an item in a linked list, since there is no need to "shift over" items when you do so. Instead, the list can be modified by just altering the references in the list. For example, to add the 23 node to the list, we can simply alter the next pointer of the 91 node:

<center>
<img
  src="/images/week-06/linked-list-3.png"
  alt="A before and after diagram of a node being added to a linked list. In the before pane, there is a linked list with three elements: a 14, a 91, and a 45. In the after pane, the 91 node's next pointer has been changed to reference a new node that contains a 23. The next pointer of the 23 then references the 45 node. In effect, the 23 node has been inserted as the third node in the list."
  style="width:500px;" />
</center>

However, linked lists also have some disadvantages. Since they are not stored in memory contiguously, they do not provide random access. In order find element `i` in the list, the list must be traversed starting from the head. This makes fetching element `i` an `O(n)` operation. In addition, the links themselves between nodes take up memory.

## Arrays vs. linked lists

Often, we need to choose a data structure based on whether it is implemented using an array or a linked list. In those situations, it's helpful to compare and contrast the two choices as follows:

* Arrays provide the ability to access elements in `O(1)` time, but it's expensive to insert an item in the middle of an array (since elements need to be shifted over) and to increase the size of an array (both `O(n)` operations).
* Linked lists provide the ability to indefinitely extend the collection, but require `O(n)` time to access an element.

In general, arrays are preferred when the data structures is being used to do mostly *read* operations -- i.e., the data structure doesn't frequently change. For a data structure that often needs to change, it might be better to use a linked list.

## Summary

Watch the below video to see a summary of linked lists:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/_jQhALI4ujg"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>


