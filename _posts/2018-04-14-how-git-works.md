---
title: How Git Works
---

So far this week we've talked about what Git is and how to use it. If you're
anything like me, you want to know how things work under the hood.

## Understanding Diff

You have to know what a *diff* is to understand how version control systems work.
A *diff* is essentially just a difference between two things. In the case of Git
and many other version control systems, a *diff* is the difference between two
files. Linux actually has a *diff* utility that can tell you the difference
between two files. It works by examining each *line* individually. Here's a
quick example.

Let's assume that file1 contains:
```
This is a file!
Hello world!
End of file.
```
and file2 contains:
```
This is a file!
Goodbye, world.
End of file.
```
If you run `$ diff file1 file2` you will get a result that looks like:
```
2c2
< Hello world!
---
> Goodbye, world.
```
Here's what that means:
* The first line, `2c2`, gives us an overview of what happened.
  *  The `c` means that a line was *changed*.
  *  The number before the `c`, a `2` in this case, is the line in the *first
  file* that corresponds to the change.
  * The number after the `c`, also a `2`, is the line in the *second file* that
  has changed.
* The `<` denotes the line(s) in the first file.
* The `>` denotes the line(s) in the second file.
* the `---` separates the contents from the first and second files.

If we were to delete line 2 in the second file, so that it's contents just look
like:
```
This is a file!
End of file.
```
the diff would look like this:
```
2d1
< Hello world!
```
* Again, the first line `2d1` gives us a snapshot of the difference.
  * The `d` means a line was deleted.
  * the `2` means line number 2 in file1 was the edited (deleted) file.
  * The `1` means that in file2, the change happened after line number 1. Or,
  after deletion, the line counter went back to line number 1.
* The `< Hello world!` is the line from file1 that was deleted.
* Nothing was changed or added in `file2`, so there are no `---` and `>` markings.

:warning: The first part, `2c2`, `2d1`, etc can often times be ignored - these are
mostly intended for use by the linux tool `patch`.

---

`git-diff` works a little bit differently than the `diff` tool and the output is
different, but the basic idea of a *diff* is the same. Here's an example from
two different commits in this repository:
