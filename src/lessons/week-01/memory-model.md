# Memory Model

We've now seen the importance of space in algorithms. Ideally, we want to limit how much space our programs use, and also optimize our programs so that they use the fast parts of the memory hierarchy. However, before we can do that, we have to know how Python programs store data. Let's take a moment to understand the *memory model* that Python uses.

## Everything is an object

In P2, you learned that *objects* are programming constructs that have some internal data (or *state*) and behavior. They allow us to group pieces of data together into a single entity, and associate functions with them. Functions that are internal to a specific object are referred to as *methods*.

In Python, *all* data is represented as objects. Simple values such as integers, floats, and booleans are all objects. Strings, lists, and dictionaries are all objects too. Everything is an object!

## The stack and the heap

When a Python program executes, all of its data (including variables and values) are stored in main memory. The memory that a Python program can use is split into multiple parts. We will focus on two of these parts: the runtime stack and the dynamic memory heap, often called just the *stack* and the *heap*.

### The stack

The *stack* is where local variables and function parameters are stored. When a function is called, a new stack *frame* is added to the stack. The stack frame includes enough room for all of the local variables and paramters that the function may use. When the function call returns, the stack frame is removed from the stack. For example, consider the following program:

```python
def adder(a, b):
    total = a + b
    return total

if __name__ == "__main__":
    x = 5
    sum = adder(x, x)
    print(sum)
```

This is what the stack would look like while the `adder()` function executes:

<center>
<img src="/images/week-01/stack.png"
     alt="A rectangle to represent stack memory, split between two stack frames: one for main and one for adder. Each stack frame contains the local variables that are inside the function."
     style="width:250px;" />
</center>

<figcaption align="center">Figure: Two stack frames and the local variables within them.</figcaption>

### The heap

Objects are stored in a region of memory known as the *heap*. Remember that all values in Python are objects, so all Python values are indeed stored on the heap. Objects remain on the heap until they are no longer used by the program. At that point, their memory is reclaimed through a process called garbage collection.

Putting the ideas of a stack and a heap together, we can draw diagrams for the memory layout of a Python program. Take for example this program:

```python
if __name__ == "__main__":
    a = 5
    greeting = "Hello, world!"
    print(greeting[:a])
```

When the `print()` statement executes, there are two variables on the stack (`a` and `greeting`), which reference two separate objects on the heap:

<center>
<img src="/images/week-01/stack-and-heap.png"
     alt="Memory divided into two parts: a stack region and a heap region. The stack region contains two variables, each of which holds a memory address of an object in the heap region."
     style="width:400px;" />
</center>

<figcaption align="center">Figure: Variables hold references to objects on the heap.</figcaption>

> Strictly speaking, even the string resulting from the expression `greeting[:a]` will be an object on the heap, but we omitted it for simplicity.

This shows us that a variable is simply a container for a reference to an object. In other words, the value inside of a variable is just the *memory address* of where an object resides on the heap. Often, we represent these types of references using arrows and abstract away the actual memory addresses:

<center>
<img src="/images/week-01/stack-and-heap-arrow.png"
     alt="The same as the previous image: two variables in the stack referencing two objects on the heap. This time, there are arrows pointing from each variable to an object instead of memory addresses."
     style="width:400px;" />
</center>

<figcaption align="center">Figure: References can be visualized as arrows.</figcaption>

## Mutability

In Python, there are two kinds of objects: *mutable* objects and *immutable* objects.

Immutable objects can not be modified by the program. All of Python's primitive data types are immutable: strings, integers, floats, booleans, and even tuples.

On the other hand, lists, dictionaries, and user-defined object types are mutable -- their contents can be modified.

So what happens when you need to, for example, change the value of a variable that holds an integer? Watch the video below to see how memory diagrams reflect how mutable and immutable objects behave.

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/pmfRfLiQY38"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

## Tracing code using diagrams

When trying to understand what a code fragment is doing, it can be useful to *trace* the code using diagrams. You can write the diagrams on paper by hand, or you can use tools to help you do the tracing, such as [Python Tutor](https://pythontutor.com/python-debugger.html#mode=edit).

Here's a fragment of code that modifies some lists and then prints them:

<iframe width="800" height="500" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=def%20lst_modify%28lst%29%3A%0A%20%20%20%20end%20%3D%20len%28lst%29%20-%201%0A%20%20%20%20temp%20%3D%20lst%5B0%5D%0A%20%20%20%20lst%5B0%5D%20%3D%20lst%5Bend%5D%0A%20%20%20%20lst%5Bend%5D%20%3D%20temp%0A%20%20%20%20%0Alst_a%20%3D%20%5B9,%208,%207,%206%5D%0Alst_b%20%3D%20%5B%5D%0A%0Afor%20item%20in%20lst_a%3A%0A%20%20%20%20lst_b.append%28item%29%0A%20%20%20%20%0Alst_modify%28lst_a%29%0A%0Aprint%28lst_a%29%0Aprint%28lst_b%29%0A&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=0&heapPrimitives=nevernest&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>

Watch the video below to see an example of how to trace through this code using Python Tutor.

> VIDEO. Demonstrate how to trace through some code that calls a function to modify a list.

<aside>
<b>Check your understanding</b>
<p>
Try tracing the following code fragment by drawing a picture. What is printed in the end? After you're done tracing the code, execute the code to see the output and reveal the solution to see memory diagrams.
</p>
<div style="position: relative;">
<iframe src="https://trinket.io/embed/python/02f632a680" width="100%" height="356" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>
</div>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p>
<b>Answer.</b>

```
[2, 2, 3]
[2, 2, 3]
[6, 5, 6]
```

After line 6, this is the picture in memory:

<img
    src="/images/week-01/memory-model-practice-1.png"
    class="center"
    alt="lst_x and lst_y reference the same list on the heap, while lst_z references a separate list"
    style="width:200px;" />

In other words, `lst_x` and `lst_y` reference the same list in memory on the heap. Therefore, changes made during the call to `modify(lst_x)` and `lst_y[0] = lst_y[1]` affect the same list. After line 9, this is the picture in memory:

<img
    src="/images/week-01/memory-model-practice-2.png"
    class="center"
    alt="After modifying both lst_x and lst_y, both changes are reflected in the same list in memory"
    style="width:200px;" />

The final modification changes `lst_z`, meaning that this is the final picture in memory:

 <img
    src="/images/week-01/memory-model-practice-3.png"
    class="center"
    alt="State of memory after changing lst_z"
    style="width:200px;" />
</p>
</details>
</aside>
