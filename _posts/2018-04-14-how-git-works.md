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
two different commits in this repository. We're going to look at the difference
between commit `d8ee32d55db5ba04456d7ac214e7f02d3151081c` and commit
`f7fababd22ea85dba012c69aebac0067769b1208`. Here's the output from `git-log`
so you can see what we're working with.
```
$ git log
commit f7fababd22ea85dba012c69aebac0067769b1208
Author: Dakota Chambers <dakotachambers@gmail.com>
Date:   Sat Apr 14 14:47:02 2018 -0500

    Change grammar in 'Understanding Diff' section.

commit d8ee32d55db5ba04456d7ac214e7f02d3151081c
Author: Dakota Chambers <dakotachambers@gmail.com>
Date:   Sat Apr 14 14:46:08 2018 -0500

    Start writing how-git-works post.
```
To see what change I made between those commits, I can use `$ git diff`!
:bulb: when working with the uniquely identifying SHA-1 HASH of each commit, you
don't have to use the whole thing. Often times the first 6 characters of each
HASH value is enough.
```
$ git diff d8ee32 f7faba
diff --git a/_posts/2018-04-14-how-git-works.md b/_posts/2018-04-14-how-git-works.md
index 49076cc..633c386 100644
--- a/_posts/2018-04-14-how-git-works.md
+++ b/_posts/2018-04-14-how-git-works.md
@@ -14,7 +14,7 @@ files. Linux actually has a *diff* utility that can tell you the difference
 between two files. It works by examining each *line* individually. Here's a
 quick example.

-Let's assume file1 contains:
+Let's assume that file1 contains:
 ` ` `
 This is a file!
 Hello world!
```

Normally, your git-diff will be color coded for easier reading. It will look
something like this:
![](/assets/images/git-diff-screenshot.png)

Whoa, this looks a lot scarier! Let's break it down...there's only a few things
we care about for this example. The first part
```
--- a/_posts/2018-04-14-how-git-works.md
+++ b/_posts/2018-04-14-how-git-works.md
```
is basically a unified diff header. Essentially, the `---` is the old file and
the `+++` is the new file. The next part
```
@@ -14,7 +14,7 @@
```
gives us information about what lines were changes and what the diff is showing.
You can ignore the @ signs, those are just markers.
* `-14,7` is short hand for representing the changes in the first file. In the
file, the diff starts on line 14, and it is 7 lines long. The actual *diff* isn't
7 lines long, but it's showing 7 lines from the file.
* `+14,7` is short hand that represents the changes to the second file. Again,
the diff is showing a "chunk" that starts on line 14 and is 7 lines long.

The most important part what comes after that section. It is showing the contents
of both files. Anything without a `-` or `+` in front of it is the same in both
files, while any line with those markers present is a line that was changed.
The `-` is a line that was removed from the first file, and the `+` is a line that
was added in the second file.
```
-Let's assume file1 contains:
+Let's assume that file1 contains:
```
Because diff works on a line-by-line basis, it views these two lines as totally
different even though I only added a single word. So this is saying that I deleted
a line containing `Let's assume file1 contains:` and aded a line that contains
`Let's assume that file1 contains:`. The words below the `-`/`+` section are just
some more contents of the file to help give context.

And that's how `diff` works! The first step in understanding Git/version control
is to know that they operate by tracking changes in files.

## Snapshots, not Differences
