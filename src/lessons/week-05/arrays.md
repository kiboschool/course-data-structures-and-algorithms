# Arrays

Up to this point, we have used Python lists as our main data structure. Lists may seem like a simple collection of data, but there's actually a simpler sequential data structure available for us to study: the *array*.

An array is a fixed-length data sequence that contains elements of a single type. The elements of an array are stored contiguously in memory (i.e., in adjacent memory locations). A sample array of four-byte integers (and some sample memory addresses) is shown below:

<br>
<center>
<img
  src="/images/week-06/array.png"
  alt="A visualization of an array as as sequence of ten boxes with integers inside, representing ten locations in memory. Each memory location has a memory address label."
  style="width:350px;" />
</center>

> **Aside.** Although Python doesn't have a built-in array type like some other languages (e.g., Java and C++), there is an `array` library:
>
>```python
>import array
>arr = array.array('i', [1, 2, 3]) # creates an array of three integers
>print(arr)
>```
>
>However, we will not be using the `array` package in this class.

## Accessing items in an array

A useful property of arrays is that they allow efficient *random access* of elements. In other words, we can access any element `i` of an array in `O(1)` time. Typically, programming languages use notation like `arr[i]` to get element `i` of an array named `arr`.

Note the requirement that the array only contains elements of a single type. This is actually what makes it possible for accessing `arr[i]` to be an `O(1)` operation. If we know the memory address of the start of the array and also know the size of each element, then we can use arithmetic to quickly compute the location of element `i` in memory:

```
memory_address(arr[i]) = memory_address(arr) + (i * array_item_size)
```

For example, each element in the above array is a four-byte integer, so we can quickly compute the memory address of the element at index 6:

```
memory_address(arr[6]) = 1040 + (6 * 4)
memory_address(arr[6]) = 1064
```

If the elements were of different types, they might be different sizes (e.g., eight-byte floating point numbers, 1 byte ASCII characters, etc.), and therefore we wouldn't be able to quickly compute the memory address of `arr[i]`.

## Adding items to an array

The main disadvantage of arrays is that they are fixed-length, so they cannot be easily resized. If you need to store more elements than the capacity of an array would allow, you would need to allocate a new, larger array and copy over all of the elements from the old array.

<aside>
<b>Check your understanding</b>
<p>What is the time complexity of resizing an array as described above (copying over all of the elements of the old array to a new, larger array)?</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> The process of copying over the elements from the old array to the new array requires iterating over the entirety of the old array, making it an <code>O(n)</code> algorithm. (Here we are assuming that the process of allocating a new chunk of memory is <code>O(1)</code>.)</p>
</details>
</aside>

## Python lists vs. arrays

You might at this point be thinking that arrays sound very similar to Python *lists*. They are indeed similar, but not exactly the same. Arrays are a more general concept, and are used across different programming languages. Python lists are -- of course -- specific to Python, and are actually a data structure that is implemented using arrays!

There are a couple of differences between arrays and Python lists:

* Python lists can contain different data types
* Python lists are extendable -- with a caveat!

### Lists can contain different data types

In Python, you can create lists that have different types of data:

```python
lst = ['hello', 1, False, 'world', 5.0]
```

But if lists use arrays under the hood, and arrays can only hold a single type of data, how is this possible? The trick is that in Python, all data types are objects. Therefore, Python lists are really arrays of *references to objects*:

<center>
<img
  src="/images/week-06/array-of-objects.png"
  alt="An array of references to Python objects of various types, including a string, an integer, a boolean, and a float."
  style="width:350px;" />
</center>

Each reference to an object is the same size, so we can still use simple arithmetic to compute the memory address of location `i` in a Python list.

### Lists are "extendable"

Python lists can seemingly grow indefinitely. If we start with a collection of data in a list, we can later add elements to the list using `append()`:

```python
lst = [1, 2, 3]
lst.append(4)
lst.append(5)
...

lst.append(99)
```

But again -- how can this be true? If Python lists are implemented using arrays, and arrays have a fixed length, then how can we grow lists indefinitely?

The answer is that occasionally, `append()` needs to resize the underlying array in order to add another element. For example, if we create a Python list with three elements:

```python
lst = [1, 2, 3]
```

Under the hood, Python might actually create an array that has enough capacity for *six* elements:

```python
lst = [1, 2, 3]    # stored in an array [1, 2, 3, , , ]
```

The program would then be able to make three calls to `append()` before the underlying array is full. But on the fourth call to `append()`, the underlying array would need to be resized (e.g., by doubling its length) in order to accomodate the new element:

```python
lst.append(4)     # array now [1, 2, 3, 4, , ]
lst.append(5)     # array now [1, 2, 3, 4, 5, ]
lst.append(6)     # array now [1, 2, 3, 4, 5, 6]
lst.append(7)     # array now [1, 2, 3, 4, 5, 6, 7, , , , , ]
```

<aside>
<b>Check your understanding</b>
<p>What's the time complexity of the <code>append()</code> method on Python lists? Consider the different possible cases.</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> If the underlying array has capacity for more elements, then the append operation is <code>O(1)</code>. However, if the array needs to be resized to accommodate the new element, then the append operation is <code>O(n)</code>.</p>
</details>
</aside>
