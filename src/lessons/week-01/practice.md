# Practice: Goals and Building Blocks

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

## 1. Finding the Average of a List

▶️ [Access the practice exercise on GitHub Classroom](https://classroom.github.com/a/UBXIozxq)

Watch the video below to see the full solution.

Make sure you give yourself enough time to solve the practice without watching the video. It is really important for your learning.

<details><summary>Solution Video</summary>

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/HRxKUVTDVTU"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

</details>

## 2. Working with Units of Space and Time

A photographer has a collection of 10,500 photos. She learns from her camera's manual that each photograph taken by the camera is 2.5 MB. Each photo also has 250 KB of metadata that needs to be stored alongside the photo. She currently has the photos in a cloud storage account that allows her to have 100 GB of data. However, she is worried that she might be reaching the limit of the account and is considering storing the collection on her local computer instead.

1. How close is the photographer to filling up her cloud storage account?

2. The photographer's computer has 40 GB of available disk space. What percentage of her collection would she be able to store on her computer?

3. The photographer learns that it takes 2000 ms to download each photo from the cloud storage account to her computer. At that speed, how many minutes would it take to download the entire collection?

4. The photographer also learns that her Internet uplink speed is 512 Kbps. Approximately how long would it take for her to upload 10 photos to her cloud storage account?

5. After reading the documentation of her editing software, the photographer finds that the software can comfortably accommodate 0.25 GiB of photo data in main memory at a time, and doesn't need to take into account the metadata associated with the photos. Approximately how many photos can she edit simultaneously?

Open the spoiler below to see the full solution.

Make sure you give yourself enough time to solve the practice without looking at the solution. It is really important for your learning.

<details><summary>Solution</summary>

1. Since the application being used in this problem is storage, it’s probably better to assume that the units are in terms of base 2. In other words, we could say that 1 KB = 1024 B, etc. However, since we’re just looking for rough numbers, we can use the base 10 system, i.e. 1 KB = 1000 B.
If that’s the case, then 250 KB of metadata is equivalent to .25 MB. Let’s add that to the size of the photo itself to get 2.75 MB of data overall for each picture.
If the photographer has 10,500 photos, that’s 10,500 * 2.75 MB = 28,875 MB = 28.875 GB of data. Therefore, she has used less than 29% of the available space on her cloud storage account.

2. Since her photo collection would only take up 28.875 GB of storage, she would be able to store 100% of it with more than 10 GB of storage space left over.

3. To download all 10,500 photos, it would take 10,500 * 2000 ms = 21000000 ms = 21000 seconds = 350 minutes.

4. Let’s convert the Internet uplink speed to MBps so that we have units that can be directly calculated with a 2.75 MB photo. 512 Kbps = 64 KBps (since there are 8 bits in a byte). We then have 64 KBps = .064 MBps. Therefore, .064 MBps * 2.75 MB means that every photo can be uploaded in .176 seconds. To upload 10 photos would therefore take 1.76 seconds.

5. Since this problem specifically mentions GiB, let’s use base 2 units and assume that each photo is really 2.5 MiB. We don’t need to include the metadata. 0.25 GiB = 250 MiB, so the editing software can hold 250 MiB / 2.5 MiB = 100 photos at a time.

</details>

## 3. Tracing Memory Modifications

Consider the Python code below. Trace the execution of the code by creating a memory diagram showing the stack and the heap, or use Python Tutor. What is output the by the `print` statement? Only execute the code after you have attempted the exercise.

<iframe src="https://trinket.io/embed/python/3d20d411fa" width="100%" height="356" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>

Watch the video below to see the full solution.

Make sure you give yourself enough time to solve the practice without watching the video. It is really important for your learning.

<details><summary>Solution Video</summary>

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/QEcZdylRiKo"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

</details>

## 4. Tracing Memory Modifications with Functions

Consider the Python code below. Trace the execution of the code by creating a memory diagram showing the stack and the heap, or use Python Tutor. What is output the by the `print` statement? Only execute the code after you have attempted the exercise.

<iframe src="https://trinket.io/embed/python/5a6d5ad261" width="100%" height="356" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>

Watch the video below to see the full solution.

Make sure you give yourself enough time to solve the practice without watching the video. It is really important for your learning.

<details><summary>Solution Video</summary>

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/LD3Gmrb3Mao"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

</details>

## 5. Implementing a Dictionary ADT

▶️ [Access the practice exercise on GitHub Classroom](https://classroom.github.com/a/LR5HZIuC)

Watch the video below to see the full solution.

Make sure you give yourself enough time to solve the practice without watching the video. It is really important for your learning.

<details><summary>Solution Video</summary>

<div
  style="position: relative; padding-bottom: 56.25%; height: 0;">
  <iframe
    src="https://www.youtube.com/embed/CeBgqqI5tV0"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;">
  </iframe>
</div>

</details>
