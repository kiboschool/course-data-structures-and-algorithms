# Tracing Recursive Functions

Tracing recursive functions can be an effective technique for understanding their behavior and identifying bugs.

## Using print statements

One common approach to tracing recursive functions is to use print statements to output the input arguments and intermediate results at each step of the recursion. For example, consider the following recursive function that calculates the factorial of a positive integer:

```python
def factorial(n):
    if n == 0:
        result = 1
    else:
        sub_result = factorial(n - 1)
        result = n * sub_result
    return result
```

To trace this function using print statements, we can add statements to output the input argument and the intermediate result at each step of the recursion. We can also add an `indent` parameter, which we can use to change the level of indentation of the print statement to more clearly illustrate the nested recursive calls:

```python
def factorial(n, indent):
    print(indent + f"factorial({n})")
    if n == 0:
        result = 1
    else:
        sub_result = factorial(n - 1, indent + '  ')
        result = n * sub_result
    print(indent + f"result = {result}")
    return result
```

Note that with each recursive call, the level of indentation is increased (`indent + '  '`). The level of indentation increases the length of the whitespace string to more clearly show which recursive calls are nested within each other.

This approach can be useful for small and simple functions, but may be cumbersome for complex recursion.

Try stepping through this code as `factorial(5, '')` executes (`''` is the initial level of indentation):

<iframe width="800" height="500" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=def%20factorial%28n,%20indent%29%3A%0A%20%20%20%20print%28indent%20%2B%20f%22factorial%28%7Bn%7D%29%22%29%0A%20%20%20%20if%20n%20%3D%3D%200%3A%0A%20%20%20%20%20%20%20%20result%20%3D%201%0A%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20sub_result%20%3D%20factorial%28n%20-%201,%20indent%20%2B%20'%20%20'%29%0A%20%20%20%20%20%20%20%20result%20%3D%20n%20*%20sub_result%0A%20%20%20%20print%28indent%20%2B%20f%22result%20%3D%20%7Bresult%7D%22%29%0A%20%20%20%20return%20result%0A%20%20%20%20%0Afactorial%285,%20''%29&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=0&heapPrimitives=nevernest&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>

## Using diagrams

You may have noticed in the previous example in Python Tutor that the runtime stack changed as the recursion executed. It can indeed be helpful to visualize the stack as the recursion executes -- this can help us understand that each call to the recursive function has its own stack frame and state. It also illustrates that after the base case is reached, all of the recursive calls must be "returned through" in order for the recursive process to complete.

Watch the following video to see an example of tracing a recursive function with a stack diagram:

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/mJU1xtGVqFY"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

## Tracing example

Below is another example of a recursive function, that counts up from `a` to `b`:

<iframe width="800" height="500" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=def%20count%28a,%20b%29%3A%0A%20%20%20%20if%20a%20%3E%3D%20b%3A%0A%20%20%20%20%20%20%20%20print%28a%29%0A%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20print%28a%29%0A%20%20%20%20%20%20%20%20count%28a%20%2B%201,%20b%29%0A%20%20%20%20%20%20%20%20%0Acount%281,%205%29&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=0&heapPrimitives=nevernest&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>

Try tracing the execution of `count(1, 5)`. You should see the output as:

```
1
2
3
4
5
```

Now consider the following modification, which swaps the two lines in the `else` clause:

<pre><code class="language-python">def count(a, b):
    if a >= b:
        print(a)
    else:
        # below statements are reversed
        <b>count(a + 1, b)</b>
        <b>print(a)</b>
</code>
</pre>

What do you think will be the output of `count(1, 5)` with this modification? To figure it out, try drawing the runtime stack while tracing the execution of the code. Is anything different about the output? If needed, try putting the code into <a ref="https://pythontutor.com/visualize.html#mode=display">Python Tutor</a>.

<aside>
<b>Check your understanding</b>
<p>What's the output of <code>count(1, 5)</code> using the modified version of the algorithm?</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> The output is reversed:</p>
<p><pre><code>5
4
3
2
1
</code>
</pre>
</p>
<p>This happens because the recursive call now happens <i>before</i> the print statement, so there are no values printed until the base case is reached. Then, the values continue to be printed as stack frames are removed from the stack. Since the stack frames are removed from the stack in the <i>reverse order</i> from which they were added, the count is reversed!
</details>
</aside>
