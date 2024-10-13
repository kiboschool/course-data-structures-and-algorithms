# Recursion in Python

We now turn our attention to using recursion in Python. Watch the following video to learn how to implement the factorial function both iteratively (using loops) and recursively in Python:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/wMNrSM5RFMc"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

To summarize, a recursive definition of factorial in Python could look like this:

```python
def factorial(n):
    if n < 2:
        # base case
        return 1
    else:
        # recursive case
        return n * factorial(n - 1)
```

During the video, the presenter claimed that recursion "does not scale up like iteration" and "requires more memory." Both of these statements are generally true. To see why, let's talk about how recursion works with respect to our memory model.

## Recursion in memory

Back in week 1, we defined the runtime stack as the part of main memory where local variables and function parameters are stored. We also had the following definition of a stack *frame*:

> ***Definition.***
>
> When a function is called, a new *stack frame* is added to the stack. The stack frame includes enough room for all of the local variables and parameters that the function may use. When the function call returns, the stack frame is removed from the stack.

Each time a recursive function calls itself, another frame is added to the stack. This continues until the base case is reached. In the case of the factorial function, this is what the stack would look like at the moment that the base case is reached:

<center>
<img
    src="/images/week-03/stack-factorial.png"
    class="center"
    alt="The runtime stack at the moment that factorial of zero is executed. The stack shows stack frames for factorial of 8, factorial of 6, factorial of 4, factorial of 2, and factorial of 0. Each stack frame has its own version of the variable n, which references a value on the heap."
    style="width:500px;" />
</center>

Notice that each stack frame contains its own `n` variable. We say that each function call has its own *state*, or variables that are local to its stack frame, which make the overall computation possible.

Once the base case (`factorial(0)`) is reached, it returns `1` to the previous function call (`factorial(2)`). In fact, each recursive call will receive a return value, multiply it by `n` (whatever `n` is in that stack frame), and return the result to the previous recursive caller.

<aside>
<b>Check your understanding</b>
<p>
Why is it necessary for each stack frame to have its own <code>n</code> variable?
</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p>
<b>Answer.</b> As the recursive calls return, they each need to multiply the result of the recursive call <code>factorial(n - 1)</code> by <code>n</code>. This <code>n</code> is different for each invocation of <code>factorial()</code>.
</p>
</details>
</aside>

Every time the recursion function is called, a new frame is added to the stack, and each one of these frames takes up memory. Contrast this with a loop-based approach, which can often use a single loop index variable (such as `i`). For this reason, recursion can indeed be more expensive in terms of space than iteration. We'll discuss this (in)efficiency in terms of big-O notation in a later lesson.
