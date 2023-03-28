# Units of space and time

Now that we know algorithmic efficiency is measured along the axes of space and time, it's also helpful to know how these resources are measured.

## Measuring time

In the password-guessing example, we took a computationally intensive problem and thought about how long it would take to complete, which allowed us to measure the result in terms of *quadrillions* of years. However, time-based measurements of computer operations are typically on a much smaller scale:

<br>

| **Unit**         | **Value**               | **Example**                         |
|------------------|-------------------------|-------------------------------------|
| Second (s)       | 1 second                | Downloading a medium-sized PDF file |
| Millisecond (ms) | 10<sup>-3</sup> seconds | Opening a PDF file on your computer |
| Microsecond (us) | 10<sup>-6</sup> seconds | Response time for an LCD monitor    |
| Nanosecond  (ns) | 10<sup>-9</sup> seconds | CPU executing 100 instructions      |

In other words, the following are equivalent:

```
1 ns = 10^-9 seconds
1 us = 10^-6 seconds = 1,000 ns
1 ms = 10^-3 seconds = 1,000 us = 1,000,000 ns
1 s = 1,000 ms = 1,000,000 us = 1,000,000,000 ns
```

The amount of time it takes for a process to complete is called its *latency*. We give some example latency measurements at the end of this lesson.

<aside>
<b>Check your understanding</b>
<p>How many milliseconds is 300 seconds?</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> There are 1,000 milliseconds in each second. <code>1,000 ms/s * 300 s = 300,000 ms</code></p>
</details>
</aside>

<aside>
<b>Check your understanding</b>
<p>How many microseconds is 10,000 nanoseconds?</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p><b>Answer.</b> There are 1,000 nanoseconds in each microsecond. <code>10,000 ns / 1,000 ns/us = 10 us</code></p>
</details>
</aside>

## Measuring space

We have specific units for measuring the amount of space that data takes up. The most basic unit to measure volume of data is the *bit* (**b**inary dig**it**) -- a 0 or 1. Groups of 8 bits are often referred to as a *byte*.

For example, the ASCII encoding of characters assigns 8 bits (1 byte) for each Latin alphabet character. The letter `'A'` has the binary encoding `01000001`.

Larger groups of bits and bytes use the metric prefixes. For example:

| **Name**      | **Value**             | **General terms**  | **Example**                            |
|---------------|-----------------------|--------------------|----------------------------------------|
| byte          | 1 byte                | One byte           | One ASCII character                    |
| Kilobyte (KB) | 10<sup>3</sup> bytes  | One thousand bytes | 2-3 paragraphs of text                 |
| Megabyte (MB) | 10<sup>6</sup> bytes  | One million bytes  | Picture taken by a smartphone          |
| Gigabyte (GB) | 10<sup>9</sup> bytes  | One billion bytes  | A movie downloaded to your device      |
| Terabyte (TB) | 10<sup>12</sup> bytes | One trillion bytes | 1,000 movies downloaded to your device |

⚠️  But be careful! Always be aware of whether you're measuring something in terms of *bits* or *bytes*. Typically, values measured in bits are represented with a lowercase "b" or "bits," e.g., 100 Kb or 100 Kbits. Values measured in bytes are usually represented with an uppercase "B" or "bytes," e.g., 100 KB or 100 Kbytes. If precision matters for your task, it's better to explicitly use "bits" or "bytes" to clearly communicate.

<aside>
<b>Check your understanding</b>
<p>
How many bytes are in 30 MB?
</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p>
<b>Answer.</b> There are 1,000*1,000 = 1,000,000 bytes in every MB. <code>1,000,000 B/MB * 30 MB = 30,000,000 bytes</code>
</p>
</details>
</aside>

<aside>
<b>Check your understanding</b>
<p>
How many KBits are in 2.5 MB?
</p>
<details>
<summary>
<i>Click to reveal the answer.</i>
</summary>
<p>
<b>Answer.</b> 2.5 MB = 2,500 KB. There are 8 bits in every bite. 2,500 KB * 8 bits/B = 20,000 Kbits.
</p>
</details>
</aside>

## Base 2 and base 10

As shown above, the prefixes "kilo," "mega," "giga," and "tera" correspond to powers of 10: 10<sup>3</sup>, 10<sup>6</sup>, 10<sup>9</sup>, and 10<sup>12</sup>. However, when we say that a computer has 8 GB of RAM, we actually do **not** mean that it has 8 x 10<sup>9</sup> bytes!

This is because volumes of memory and storage are conventionally measured in powers of 2 (binary), *not* powers of 10 (decimal). Quite luckily, some powers of 2 are almost equal to some powers of 10, so the difference is often insignificant. Units that are based on powers of 2 have slightly different prefixes:

| **Value (in bytes)**               | **Name**       | **Approximate Decimal Equivalent**  |
|------------------------------------|----------------|-------------------------------------|
| 1                                  | byte           | 1                                   |
| 2<sup>10</sup> = 1,024             | Kibibyte (KiB) | 10<sup>3</sup> = 1,000              |
| 2<sup>20</sup> = 1,048,576         | Mibibyte (MiB) | 10<sup>6</sup> = 1,000,000          |
| 2<sup>30</sup> = 1,073,741,824     | Gibibyte (GiB) | 10<sup>9</sup> = 1,000,000,000      |
| 2<sup>40</sup> = 1,099,511,600,000 | Tebibyte (TiB) | 10<sup>12</sup> = 1,000,000,000,000 |

Because the difference between, say, a KB and a KiB is so small, "KB" could be used to mean either one. Again: if precision matters, be overtly clear about which unit you're using.

To make matters even more confusing, telecommunications systems measure properties such as Internet bandwidth using the power of 10 system. A 1 Gbps connection means that 1 x 10<sup>9</sup> bits of information can be transmitted in one second.

Why the difference? Well, telecommunications and storage technologies evolved separately and without a consistent standard, leading to different conventions for units that continues today!

## Putting it all together

Now that we know about the memory hierarchy and the different ways of measuring space and time, we can ground our understanding of these concepts with some concrete numbers:

<p>

| **Process**                              | **Latency**                          | **Note**                                          |
|------------------------------------------|--------------------------------------|---------------------------------------------------|
| Reading data from cache                  | 1 ns                                 | E.g., fetching an integer variable's value        |
| Reading data from main memory            | 100 ns                               |                                                   |
| Reading 1 MB from main memory     | 250,000 ns = 250 us                  |                                                   |
| Reading 1 MB from disk           | 20,000,000 ns = 20,000 us = 20 ms    | 80x slower than main memory                       |
| Sending data  from US to Europe and back | 150,000,000 ns = 150,000 us = 150 ms | Just one packet! Downloading an entire file would take longer |
|                                          |                                      |                                                   |

Knowing these exact figures is not crucial to being able to write algorithms and use data structures. But it's helpful to know the scale at which we're working, and how the physical components of a computer will affect our programs.
