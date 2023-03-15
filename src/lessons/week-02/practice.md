# Practice: Algorithm Analysis and Sorting

---

> 💡 This is your chance to put what you’ve learned into action.
>
> Try solving these practice challenges to check that you understand the concepts.
> No submission is necessary for practice exercises.

## Why practice?

Practice coding helps you become a great coder. These practice problems aren't
graded, but that doesn't mean they aren't important.

You should aim to practice a lot, especially with unfamiliar concepts. Spread practice over multiple days to take advantage of the _spacing effect_, which helps you retain new knowledge.

<details><summary>More about practice</summary>

Practice helps you understand what you know, and what you don't know. It can be easy to trick yourself into thinking you understand something when you
do not -- or that you don't understand when you do. Practicing by writing code
or debugging code will help you find out what you really understand, and where
you are still confused.

Practice helps build confidence in your coding. The more programs you write, and
the more problems you solve, the more you learn that you are a capable coder and
problem-solver.

Practice doesn't always feel good - sometimes you'll be stumped! But, practice
shouldn't feel super frustrating either. If you find yourself getting angry at
yourself or the code, it's a good time to take a break and ask for help.

The **solutions** to each challenge are available, and you can view a video of the solution below each challenge.

* Try to go through the whole challenge without using the solution.
* If you can’t do the challenge without looking the solution, it means you don’t understand the material well enough yet.
* Try the next practice challenges without looking at the solution. If you need more practice challenges, reach out on Discord.

</details>

<aside>

**If you get stuck**
1. Read the instructions again.
2. Remember **G**o **C**limb **K**ibo - first Google, then ask the Community on Discord, then reach out to Kibo instructional team.

</aside>

## 1. Sorting lists using various sorts

Consider the following list:

```txt
[19, 81, 67, 21, 86, 42, 6, 30, 16]
```

1. Sort the list using selection sort. Show the contents of the list after each pass of the outer loop.
2. Sort the list using insertion sort. Show the contents of the list after each pass of the outer loop.
3. Sort the list using radx sort. Show the contents of the list after each round of bucketing.

Watch the video below to see the full solution.

Make sure you give yourself enough time to solve the practice without watching the video. It is really important for your learning.

<details><summary>Solution video.</summary>

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/a-gw1DBUDrg"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

</details>

## 2. Deriving big-O running time

Suppose you want to count the number of duplicate items in a list. For example, if given the list `[4, 1, 9, 1, 1, 4, 6, 8]`, there would be three duplicates: two extra 1s and one extra 4.

Consider the following algorithm to count the number of duplicates:

```python
def num_dups_1(lst):
    num_dups = 0
    for i in range(len(lst)):
        for j in range(i + 1, len(lst)):
            if lst[i] == lst[j]:
                num_dups += 1
                break
    return num_dups
```

This algorithm looks at every element of the list and considers all elements to its right. If it finds a duplicate, it adds one to the count. To avoid double-counting duplicates, it will `break` the inner loop once a duplicate is found and continue on to the next element of the outer loop.

  1. What's the worst case big-O time efficiency of `num_dups_1()` in terms of the length of the list? What's the big-O space efficiency?

Here's an alternative way of implementing this algorith, which first sorts the input using radix sort:

```python
def num_dups_2(lst):
    sorted_lst = radix_sort(lst)
    num_dups = 0
    for i in range(1, len(lst)):
        if lst[i] == lst[i - 1]:
            num_dups += 1
    return num_dups
```

This version of the algorithm first sorts the list using radix sort, and then uses a `for` loop to count the number of duplicates as it iterates over the sorted list.

  2. What's the worst-case big-O time efficiency of `num_dups_2()` in terms of the length of the list? What's the big-O space efficiency? Be sure to include the time and space efficiencies of radix sort as discussed in this week's lessons as a part of your answer.

  3. According to your analysis, which version of the algorithm is more efficient?

<details><summary>Solution Video</summary>

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/x_bpoJ4-zVk"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

</details>

## 3. Searching for duplicates using binary search 

> [Access the exercise via GitHub Classroom here.](https://github.com/kiboschool/duplicate-count)

Watch the video below to see the full solution.

Make sure you give yourself enough time to solve the practice without watching the video. It is really important for your learning.

<details><summary>Solution Video</summary>

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/2KTb3EXPI1M"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

</details>

## 4. Experimentally deriving the running time of insertion sort

> [Access the exercise via GitHub Classroom here.](https://github.com/kiboschool/insertion-analysis)

Watch the video below to see the full solution.

Make sure you give yourself enough time to solve the practice without watching the video. It is really important for your learning.

<details><summary>Solution Video</summary>

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/m9ZUtpZ0Af4"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

</details>

## 5. Optimizing selection sort

> [Access the exercise via GitHub Classroom here.](https://github.com/kiboschool/selection-sort-opt)

Watch the video below to see the full solution.

Make sure you give yourself enough time to solve the practice without watching the video. It is really important for your learning.

<details><summary>Solution Video</summary>

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/YkCZ4yLwt_E"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

</details>
