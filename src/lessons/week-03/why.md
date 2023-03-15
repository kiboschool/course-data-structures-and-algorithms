# Why Use Recursion?

So far, thinking about solving problems recursively may seem more difficult than using loops. However, there are many problems that are more naturally (and more elegantly) solved using recursion. You will soon find that certain algorithms (e.g., binary search) and certain data structures (e.g., linked lists and trees) are easier to think about recursively.

Searching through a file directory is one example of a problem that is more easily solved recursively. Watch the below video to see why trying to print all of the files and folders from your computer is not simple to do using loops:

> Insert video here showing loop printing only first level results, adding a second loop to print the next level of results, running into problem where we don't know how many nested loops we would need, etc.

<!--
Most modern operating systems have a hierarchical filesystem, in which directories (or folders) can have both files and other directories nested within them. For example, your computer may be organized as follows:

```
/
  Desktop/
    Classes/
      programming-1/
        notes.docx
        homework.pdf
      data-structures/
        notes-week1.docx
        interview-notes.docx
    Pictures/
      portrait.png
      signature.jpg
  Documents/
    Budgets/
      FY2021.xlsx
     FY2022.xlsx
    taxes.docx
  Downloads/
    cat_skateboarding.gif
```

Say that we wanted to print out all of the directories and files in our filesystem. A program that uses only loops might look something like the following:

```python
def print_filesystem(root_dir):
    # print all entries (files and folders)
    # in the directory
    for entry in root_dir:
        print(entry)
```

Given the root directory of the filesystem ('/'), this attempts to print out all files and folders within it. However, the output of this program is only:

```
Desktop/
Documents/
Downloads/
```

In other words, it doesn't look *inside* 
-->

We'll revisit this task of recursively printing out all of the files and folders in your computer as a practice exercise later this week.

Now that we know more about why recursion can be useful, let's learn the basics of how we can use recursion as a programming technique.
