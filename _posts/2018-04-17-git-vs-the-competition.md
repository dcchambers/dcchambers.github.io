---
title: Git vs. The Competition
---

If you have been following along during [Git Week 2018](/2018/04/07/git-week.html),
you know that Git isn't your only choice for version control. There are plenty of
other options out there. Are they worth looking at? Git has a few features that
set it apart from many other version control systems. In the final article for
Git Week 2018 (a little late - sorry! :frowning:), we'll look at how Git is
different and how it stacks up to the competition.

## Git is Distributed

One of the most important things about Git is that it is a **distributed**
version control system. Today, that doesn't make it very unique. Any VCS I would
recommend using is a dVCS. At the time of Git's inception, though, distributed
version control systems were not all too common.

CVS (Concurrent Versions System) and SVN (Subversion) are two older and at one
time, very common *centralized* version control systems. In this model, the
systems use a centralized client-server model where a team of developers use a
single shared repository on a remote server.

Distributed version control systems like Git are better than centralized version
control systems for a couple of reasons.
* When a developer *clones* the repository, they have a copy of the entire project
including every file and the complete history on their local machine.
  * This allows Git to work fast for most actions because everything Git needs
  is already available on the local machine - it doesn't need to contact a
  remote server.
  * Allows developers to safely work offline, making branches and commits without
  ever needing to contact a remote server until you want to push or pull.
  * It also provides a convenient distributed back-up system for your source
  code. Git **is not** a proper back-up system, which you should still implement,
  but it's better than nothing.
The only real disadvantage to a distributed system is that repos with lots of
large (binary) files can take a long time to download and will consume a large
amount of disk space. However, disk and bandwidth are dirt cheap compared to the
potential costs of *not* using a dVCS.

## Git is Safe
