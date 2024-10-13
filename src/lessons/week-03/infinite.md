# Infinite Recursion

One potential pitfall when writing recursive functions is to ensure you're not calling the recursive function infinitely. This can happen if your base case is missing or incorrectly defined.

For example, this program attempts to count down from a given integer, two numbers at a time:

```python
def count_down_by_two(n):
    if n == 0:
        # base case
        print(n)
    else:
        print(n)
        count_down_by_two(n - 2)
```

Say that we call `count_down_by_two(8)`. Everything works as expected:

```
count_down_by_two(8):
  print(8)
  call count_down_by_two(6)

  count_down_by_two(6):
    print(6)
    call count_down_by_two(4)

    count_down_by_two(4):
      print(4)
      call count_down_by_two(2)

      count_down_by_two(2):
        print(2)
        call count_down_by_two(0)

        count_down_by_two(0):
          print(0)
          return (base case)
```

All of the recursive calls then return, and the overall output is:

```
8
6
4
2
0
```

Check your understanding of the execution of this code by stepping through it yourself using Python Tutor:

<iframe width="800" height="500" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=def%20count_down_by_two%28n%29%3A%0A%20%20%20%20if%20n%20%3D%3D%200%3A%0A%20%20%20%20%20%20%20%20%23%20base%20case%0A%20%20%20%20%20%20%20%20print%28n%29%0A%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20print%28n%29%0A%20%20%20%20%20%20%20%20count_down_by_two%28n%20-%202%29%0A%20%20%20%20%20%20%20%20%0Acount_down_by_two%288%29&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=0&heapPrimitives=nevernest&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>

But what if we call `count_down_by_two(5)`? Before playing the video below, try to predict what the result will be by tracing the execution of the `count_down_by_two()` function defined above. Only proceed to the video and code below after making your prediction.

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/DjtqFUuCWj4"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

Clearly, we need a more comprehensive base case -- one that is more robust to the different patterns of execution. Here's one way you could correct the issue (by using `<=` in the base case):

<pre><code class="language-python">def count_down_by_two(n):
    if <b>n <= 0</b>:
        # base case
        # if we've gone negative, just print 0 and stop
        print(0)
    else:
        print(n)
        count_down_by_two(n - 2)
</code>
</pre>

Now that we know a bit about writing recursive methods, let's learn about how to trace their execution to gain a better understanding of how they work.
