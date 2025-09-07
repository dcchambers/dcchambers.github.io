---
title: "Why I Love Obsidian: Hackability"
tags:
---

I use [Obsidian](https://obsidian.md/) as my primary note-taking tool.
There's so much I love about it:
It's fast.
It's local-first.
It's run by a small team with a focus on being a sustainable business.
It's got lots of plugins that extend functionality.
But by far the best feature is that it stores all data in plain text files.

This gives you so much power!
You can open your Obsidian notes in other text editors/software if you want.
It also means you can write scripts or use other programs to manipulate your notes.

I use metadata [properties](https://help.obsidian.md/properties) extensively in my notes for organization and other things.
I wanted to change a property that I have in many notes from one value to another.
Obsidian has no way to bulk update properties on all notes.
There may be a plugin to do this - but it's not needed.
Your "Obsidian Vault" is quite literally just plaintext markdown files in a directory on your computer.

There is this great little tool called [sed](https://www.gnu.org/software/sed/manual/sed.html).
You might have heard of it.
It's really good at one thing - replacing text in a file.
Or better yet, many files.

With a little command line magic following the standard [Unix philosphy](https://en.wikipedia.org/wiki/Unix_philosophy) I was able to easily bulk update all of those properties on hundreds of files.

```
find . -type f -exec sed -i 's/old-property/new-property/g' {} +
```

**P.S.** if you're on MacOS - you should install [gnu-sed](https://formulae.brew.sh/formula/gnu-sed) and use that instead of the BSD-variant included with MacOS.
It has some quirks and it works slightly differently than GNU sed.
A lot of the `sed` commands you find online won't work correctly on MacOS.

```
brew install gnu-sed
alias sed='gsed'
```
