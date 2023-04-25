# String Recursion

Last week, we learned that recursion is a powerful programming technique, and we used it to solve *numerical* problems: finding the nth Fibonacci number, calculating the factorial function, etc. This week, we will use recursion on lists and strings to solve more complex problems.

Just like numerical recursion, string recursion involves breaking down a problem into smaller subproblems and solving them recursively. We can think of strings as collections of `n` characters, and can make the problem smaller at each step by solving a problem of size `n - 1`, then solving a problem of `n - 2`, etc., all the way down to a base case.

In this lesson, we will explore three common applications of string recursion in Python: printing a string, finding the length of a string, and appending a character to a string.

## Printing a String

Let's use recursion to print a string, one character at a time. Thinking recursively, we can define the problem of printing a string as follows:

```
print(string of length n) = print(one character), then print(string of length n - 1)
```

Here's a recursive function that does this:

```python
def print_string(s):
    if len(s) == 0:
        return
    else:
        print(s[0])
        print_string(s[1:])
```

Notice a few things:

* The base case occurs when the function is given the empty string (`''`). In that case, there's nothing left to print, so we can simply return.
* We make a recursive call to `print_string()` with everything but the *first* character using a slice, `s[1:]`.
* The function has no return value. Recursive functions may or may not have a return value. In this case, `print_string()` can accomplish its task without returning a specific value.

<aside>
<b>Check your understanding</b>
<p>How could you change this function to print the string backwards?</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> To print the string backwards, you could reverse statements in the recursive case as follows:</p>
<pre><code class="language-python">def print_string(s):
    if len(s) == 0:
        return
    else:
        print_string(s[1:])
        print(s[0])</code></pre>
<p>Because the recursive call is now placed first, each invocation of this function (until the base case) will first make a recursive call before doing anything else. The characters don't get printed in each stack frame until we reach the base case and start returning back through the recursive calls.</p>
<p>To picture this, try stepping through the execution using Python Tutor:</p>
<iframe width="800" height="500" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=def%20print_string%28s%29%3A%0A%20%20%20%20if%20len%28s%29%20%3D%3D%200%3A%0A%20%20%20%20%20%20%20%20return%0A%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20print_string%28s%5B1%3A%5D%29%0A%20%20%20%20%20%20%20%20print%28s%5B0%5D%29%0A%20%20%20%20%20%20%20%20%0Aprint_string%28'kibo'%29&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=0&heapPrimitives=nevernest&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>
</details>
</aside>

## Finding the length of a string

Watch the following video to learn how to write a recursive function that calculates the length of a string.

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/RRK0gd77Ln0"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

In contrast to `print_string()` above, the `recursive_str_len()` function that was written in the video returns a number. This return value is built up through the return statements in the series of recursive calls.

## Replacing a character in a string

Watch the following video to see how to write a recursive function that replaces a character in a string.

> Insert video.

## Efficiency

Note that for each of the above examples -- printing a string, finding the length of a string, and replacing characters in a string -- we needed to recurse over the length of the string. This is analogous to using a `for` loop to iterate over the characters of the string. Therefore, all three of these algorithms are `O(n)`.
