# An Alternative to Loops

So far, we have used loops to process data structures such as Python lists and dictionaries. But that's not the only way! We can also use an approach known as *recursion*.

We'll define recursion as a programming technique in the next lesson. For now, let's just get our brains working recursively.

## Counting your position in a queue

Imagine that you're in a queue for a sporting event, and want to know what your position is in the queue. Maybe the venue has only a limited number of seats, and you're wondering whether you'll be able to get a seat.

One approach to finding out your position in the queue would be to simply count the number of people in front of you. For each person in the queue, you add one to a running sum. Once you've counted all the people in the queue, add one more to the sum to get your position in the queue.

This technique is analogous to using a loop to iterate over some data, and it works great. But let's try thinking about this problem a little bit differently.

Instead of counting all of the people yourself, you realize that if you knew the position in the queue of the person in front of you, you could just add one to calculate your *own* position in the queue. Genius!

<center>
<img
    src="/images/week-03/line-1.svg"
    class="center"
    alt="People queuing for a concert. You are at the end of the queue. Kisha is in front of you, and Amari is in front of Kisha. There are many unnamed people in front of Amari. At the front of the queue is Zuri, and second in the queue is Emmanuel."
    style="width:500px;" />
</center>

You ask Kisha what her position in the queue is. She's almost as far back as you are, so she in turn asks Amari what his position in the queue is. Amari asks the person in front of him, so on and so forth, until we reach the beginning of the queue. There, Emmanuel asks Zuri what her position in the queue is. Zuri knows for a fact that she is first in the queue, so she tells Emmanuel that she is in position 1.

<center>
<img
    src="/images/week-03/line-2.svg"
    class="center"
    alt="The same queue of people as before, but annotated with Zuri telling Emmanuel that she is in position one."
    style="width:500px;" />
</center>

Emmanuel takes this information and adds one to the count, so that he can tell the person behind him that he is in position 2 in the queue. Each person repeats this process, until eventually Kisha tells you that she is in position 536 in the queue. You take this information and add one to the count to get your final answer: you are in position 537!

<center>
<img
    src="/images/week-03/line-3.svg"
    class="center"
    alt="The same queue of people as before, but annotated with each person telling the person behind them what position they are in the queue."
    style="width:500px;" />
</center>

This is a recursive solution to the problem. Let's now more carefully define what we mean by recursion.

## What is recursion?

Here's one definition of recursion:

> ***Definition.***
>
> *Recursion* is a problem solving technique in which you define a problem in terms of a simpler version of itself.

In the above example, we were able to define the "position in queue" problem in terms of a smaller version of tiself:

**Recursive case**
```
position_in_queue(me) = position_in_queue(person in front of me) + 1
```

Through repeatedly applying this logic throughout the queue, we eventually found that `position_in_queue(person in front of me)` was 536, leaving us with an easy calculation to find that `position_in_queue(me)` is 537.

Another way of thinking about this approach is that we took a problem of size `n` (there are `n` people in the queue), and decomposed it into a problem of size (`n - 1`).

Technically, we actually only applied this logic for everyone in the queue *except the person at the front of the queue*. In that case, the problem was simple enough for us to solve without needing to do any extra work. For the first person in the queue, we know that:

**Base case**
```
position_in_queue(first person in queue) = 1
```

This is known as the *base case* -- the case for which the problem is small enough or simple enough that we can define the answer without needing to break the problem down recursively. For all of the other people in the queue, we used the *recursive case* formula defined above.

## Other applications of recursion

There are many natural applications of recursion in the world around us. For example, geometric patterns can be defined in terms of smaller version of themselves, such as Sierpinski's triangle:

<center>
<img
    src="/images/week-03/tri.svg"
    class="center"
    alt="Sierpinski's triangle, a geometric shape of triangles defined in terms of smaller triangles."
    style="width:400px;" />
</center>

Some tasks, such as climbing a ladder, can be defined in terms of recursion: climbing to rung `n` of a ladder is equivalent to climbing to rung `n - 1` and then climbing one additional rung.

Some mathematical formulas, such as the Fibonacci sequence or the factorial function, are defined recursively. For example, the factorial function (`n!`) is defined as:

```
n! = n * (n - 1)!
```

<aside>
<b>Check your understanding</b>
<p>What is missing from the definition of the factorial function above?</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> The above definition only provides the recursive case, but we also need a base case. For the factorial function, we can define `1! = 1`. (In some contexts, you can also say `0! = 1`.) The factorial function is not defined for negative numbers.</p> 
</details>
</aside>

In the next lesson, we will learn how we can use recursion as a programming technique.
