# Practice: Recursion I

---

> 💡 This is your chance to put what you've learned into action.
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

## 1. Recursion and the stack

Consider the below definition of the Fibonacci function:

```python
def fibonacci(n):
    if n < 2:
        return 1
    return fibonacci(n - 1) + fibonacci(n - 2)
```

1. What is the *fourth* function call made to the `fibonacci()` function when executing `fibonacci(4)`? Consider `fibonacci(4)` to be the first function call in the process.

2. How many stack frames are on the stack during the fourth function call of `fibonacci()` from (1)? Exclude any stack frames that may have been on the stack before `fibonacci(4)` was called.

3. What is the *fifth* function call made to the `fibonacci()` function when executing `fibonacci(4)`? Consider `fibonacci(4)` to be the first function call in the process.

4. How many stack frames are on the stack during the fifth function call of `fibonacci()` from (3)? Exclude any stack frames that may have been on the stack before `fibonacci(4)` was called.

<details><summary>Solution video.</summary>

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/cDCXBkEQ88Y"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

</details>

## 2. Tracing a recursive function

Consider the following recursive algorithm:

```python
def mystery(x, y)
    if x * y == 0:
        return x
    else:
        return y + mystery(x - 1, y - 2)
```

1. Trace the execution of `mystery(5, 6)` using one of the techniques from the lessons, including drawing a call tree or runtime stack, or by writing down the sequence of recursive calls and return values.

2. What value is ultimately returned by `mystery(5, 6)`?

3. How many stack frames are on the stack when the base case is reached? Exclude from your count any stack frames that may have been on the stack before `mystery(5, 6)` was called.

4. Is it possible for this function to produce infinite recursion? If not, explain why. If yes, give example values of `x` and `y` that would lead to infinite recursion.

<details><summary>Solution Video</summary>

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/CKYSX4ccxxo"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

</details>

## 3. Implementing various recursive functions

▶️ [Access the practice exercise on GitHub Classroom](https://classroom.github.com/a/FEDpOlIQ)

Watch the video below to see the full solution.

Make sure you give yourself enough time to solve the practice without watching the video. It is really important for your learning.

<details><summary>Solution Video</summary>

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/qgsojrZq5Vc"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

</details>

## 4. Recursively printing a file

▶️ [Access the practice exercise on GitHub Classroom](https://classroom.github.com/a/h5NW84O5)

Watch the video below to see the full solution.

Make sure you give yourself enough time to solve the practice without watching the video. It is really important for your learning.

<details><summary>Solution Video</summary>

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/cQGmmEulBYg"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

</details>

## 5. Recursively walking a directory tree

▶️ [Access the practice exercise on GitHub Classroom](https://classroom.github.com/a/4I0VS5ya)

Watch the video below to see the full solution.

Make sure you give yourself enough time to solve the practice without watching the video. It is really important for your learning.

<details><summary>Solution Video</summary>

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/CaWxDx0S670"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

</details>
