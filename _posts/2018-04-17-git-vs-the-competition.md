---
title: Git vs. The Competition
last_modified_at: 2018-04-18
tags: git
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

We learned in [How Git Works](/2018/04/15/how-git-works.html) that Git stores
all of its objects (commits, etc) in a simple hashed key-value database. This
means that the data in these objects is *immutable*. In other words, it can't
be changed. Because of this, Git history is very safe! Even if you think you've
accidentally deleted a commit, it's probably stilled stored in the *reflog*. The
reflog is the Reference Log - and it keeps track of every single Git reference
you've made. Thanks to the reflog it's hard to accidentally destroy data in Git.

:bulb: You can use `git reflog` similar to the `log` command to look at a
history of your actions in a repository.

### Rewriting History

One of the most powerful things Git lets you do is rewrite history. You can
change the order of commits, change commit messages, combine commits or split
one into multiple commits, and even remove commits completely. The distributed
nature of Git allows you to do this locally before pushing your commits and
sharing them with others. And because Git is built to be safe, even when
re-writing history its hard to truly destroy any data.
* Modify the most recent commit with `$ git commit --amend`.
  * Forget to add a file in a commit? Make your change, add it with `$ git add`,
  and then `git commit --amend --no-edit`. The `--no-edit` flag tells Git to not
  change the commit message.
  * :warning: Again, because Git is picky about protecting the history, amended
  commits are actually *new* commits. Be careful about amending a commit others
  might be working from.
* `$ git rebase` is perhaps one of the best features of Git when compared to other
dVCS (such as Mercurial). `rebase` allows you to move commits around. Use the
`-i` flag to run `rebase` in interactive mode to selectively decide what history
to edit.

:star: Thanks to the wonder that is **reflog**, you can edit git history without
fear. Reflog contains information about the old states of branches, even after
"rewriting" history - and allows you to go back to those states if desired.

## Social Coding

It's impossible to understate the impact that *social coding* sites like Github
and Gitlab have had on modern software development. Open Source projects are
more popular than ever, and these platforms allow people to collaborate in ways
never thought possible only a few years ago. The best part? Almost all of them
use Git. Github is by far the most popular, but the other big players in the
field, including Gitlab and Bitbucket, all support Git as the primary VCS.

There are also more tools than ever, both for enterprise and personal use, to
enhance your software development experience using Git. There are awesome GUI
tools for interacting with your Git repo, including favorites like
[Kraken](https://www.gitkraken.com/) and [Tower](https://www.git-tower.com/mac/).
Integrate your Github account to your [Trello task boards](https://blog.trello.com/github-and-trello-integrate-your-commits).
Work with your Gitlab repo directly in [Slack](https://docs.gitlab.com/ee/user/project/integrations/gitlab_slack_application.html).
Do [code reviews](https://github.com/features/code-review),
[track issues](https://guides.github.com/features/issues/),
[manage releases](https://help.github.com/articles/creating-releases/),
[and more, directly in Github.](https://github.com/features) Gitlab, Bitbucket,
and the other guys all have similar options.

## The Competition

There are many version control systems, but only a few I would consider as a
realistic alternative to Git.

### Mercurial

Mercurial (hg) is probably the most well-known and popular Git alternative. Like
Git, it is a distributed VCS. Also like Git, it was created as an answer to
Bitkeeper removing its free license in 2005. While the Linux Kernel project
ultimately went with Git, Mercurial has proved to be a capable and popular VCS
on its own.
* While Git history is safe, Mercurial history is sacred. Mercurial treats its
history as unchangeable, and that offers a sense of security to some developers.
* Mercurial also has first-class Windows support and operates virtually the same
in every environment you can run it.
* Mercurial's command line tools are pretty damn sleek. Git's commands are
powerful and open ended - allowing you to do a lot but being less obvious about
how to get stuff done right away. Mercurial's commands are the opposite - they
do one thing, but they do it well.

* Mercurial is significantly slower than Git, and repos are considerably less
efficient with storage concerns. Not a problem for many people, but potentially
problematic for large projects.
* Mercurial's inability to rewrite history can be limiting when cleaning up a
messy history (after a night of testing the
[Balmer Peak Hypothesis](https://xkcd.com/323/), maybe?) or doing other work
typical in a Git workflow.

If for some reason you couldn't use Git, Mercurial is the first (and possibly
only) alternative I would recommend.

### Team Foundation Server

Team Foundation Server isn't actually a VCS - it's Microsoft's all-in-one
solution for the software development life cycle. It does have the ability to
use Git for version control, but Microsoft would prefer you use the included
[Team Foundation Version Control (TFVC)](https://docs.microsoft.com/en-us/vsts/tfvc/overview?view=vsts).

TFVC is a centralized version control system, similar to Apache's Subversion. As
a result, it doesn't have any benefits of using a dVCS. Developers only have
one version of a file on their machine at a time, and project history is stored
only on the remote server. As a result, offline work is limited.

I might recommend TFS if you're developing on the Windows platform or using
Visual Studio. Use Git if you can - it's got so many advantages over TFVC.

### Bazaar

[Bazaar](http://bazaar.canonical.com/en/) is Canonical's dVCS solution. It has
all the usual advantages of a dVCS that both Git and Mercurial have. Bazaar does
have one feature that makes it unique - *bound branches*. A bound branch checks
that you're up-to-date with a remote repo *before* making a commit. This can
prevent issues like merge conflicts. A useful, but ultimately not *entirely
necessary* feature. Like Mercurial, Bazaar also runs natively on Windows.

While Bazaar has some neat features, I don't think it has enough extra going on
for it to recommend it over Git or Mercurial for most people. Especially since
development has slowed to a crawl - the last major stable release was over two
years ago in February of 2016.

### Everything Else

As I mentioned - there are a lot of different version control systems. Far more
than I have experience with or could even name. We can't discuss them all, but
here's a couple of the most commonly sought-after alternatives.

#### The Old Guard

CVS and SVN had their time in the sun - and that time is gone. Distributed
version control simply has too many advantages to continue to use these
dinosaurs of the VCS world.

#### Fossil

I don't have any experience with Fossil - but it seems to be gaining a small
resurgence of popularity lately. It does seem to have some
[neat features](https://www.fossil-scm.org/xfer/doc/trunk/www/fossil-v-git.wiki).
It's distributed, open-source, and in active development. Might be worth looking
at!

#### Perforce (Helix Core)

Perforce is ten years older than Git and still has a strong following in certain
enterprise industries. The kicker: it's not free. For *most* people, I can't
recommend Perforce/Helix Core. It might be looking into if you've got a
particularly large repo or want good Enterprise Windows support. It's also got
better GUI support out-of-the box and natively supports Windows. I suspect most
teams would be able to switch to Git/Mercurial without issue, though.

----

Well, that sums up Git vs. the Competition. Ultimately, there's a ton of choices
out there. Git is my VCS of choice, but I use Mercurial at work in addition to
Git (damn you legacy projects!), and it serves us well. If you're trying to
decide on a tool, do your research to learn the benefits of each. In general,
I think Git has just about everything most teams need to be successful.

This wraps up my [miniseries on Git](/2018/04/07/git-week.html). I hope you've enjoyed reading
about one of the most influential software development tools of the 21st Century!
If you're getting tired of Git-related posts, thanks for sticking with me. I've
got some fresh content in the pipeline!
