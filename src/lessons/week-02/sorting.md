# Sorting

This week we will mainly consider *sorting* algorithms -- algorithms that put a collection of numbers, strings, or some other data into *order*. For example, a sorting algorithm written in Python could accept a list of numbers such as `[5, 8, 2, 1, 9]` as input, and return the sorted version of the list: `[1, 2, 5, 8, 9]`.

Watch the following video, which provides an overview of the goal of sorting and compares a few sorting algorithms:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/watch?v=WaNLJf8xzC4"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

As mentioned by the video, books are a great example of something that can be sorted. In this class, for simplicity we will primarily focus on sorting integers.

<aside>
<b>Check your understanding</b>
<p>What are some examples of sorting in your day-to-day life?</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b>Most of us encounter many examples of sorting on a daily basis. For example, when you open your email, the messages are probably sorted in reverse chronological order. When you search for products to buy online, often they are sorted by how relevant the seller thinks they are to you -- or you may change the order to be sorted by lowest to highest cost. For a non-technical example, you may sort your clothes when folding your laundry: shirts go into one pile, socks go into another pile (perhaps further sorted by type or color), etc.</code></p>
</details>
</aside>

## Why sorting?

You may be wondering why we are choosing to focus on sorting algorithms. There are three main reasons:

1. Sorting algorithms are all around us in our daily lives.
2. Sorting algorithms are relatively easy to understand when learning how to analyze the efficiency of algorithms.
3. There are multiple simple versions of sorting algorithms that make it easy to compare and contrast their implementations and efficiencies.

Our discussion of sorting algorithms is motivated by our desire to learn about how to analyze the efficiency of algorithms.

## Operations, comparisons, and moves

Recall from last week that the time efficiency of an algorithm is the amount of computational time that an algorithm takes to complete its task. But what determines how long an algorithm takes to complete?

The computational time is determined by the number of *operations* that the algorithm performs. When a computer program is executed, the code of the program is broken down into a series of simple operations, for example: adding two numbers together, comparing two numbers, fetching a value from main memory, assigning a value to a variable, and many others. Taken together, these fundamental operations compose an entire computer program.

For sorting algorithms specifically, the number of overall operations is dominated by two specific operations: comparing elements of the list and moving elements of the list around to different positions. Therefore, we will focus our time analysis on the number of *comparisons* and *moves* that a sorting algorithm performs.

For example, this would be considered a comparison between two elements of a list:

```python
if lst[i] < lst[i - 1]:
```

And the following would be considered a move into one of the positions of the list:

```python
lst[i] = lst[i + 1]
```

In the next lesson, we will learn a sorting algorithm, count the number of comparisons and moves it performs, and use those metrics to determine what the running time of the algorithm is.

