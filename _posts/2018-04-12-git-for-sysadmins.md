---
title: Git for Sysadmins
last_modified_at: 2018-04-16
---

Congratulations! You survived [Git 101](/2018/04/09/git-101.html). :tada: :tada:

I'm sure you noticed that it focused on using Git from the perspective of a
software developer. A common problem with most Git documentation and online tutorials
is that they are often written with one audience in mind: developers. Most of the
documentation aimed at System Administrators is focused around *administrating
a Git server*, not about actually *using Git* for system administration tasks. This
post is going to focus on **practical ways you can use Git with System
Administration tasks.**

It turns out that Git and other version control systems can be just as useful
for System Administrators as they are for Developers. My background is in Linux
System Administration - so my knowledge and advice is focused on that area. I am
sure that many principles could easily apply to Windows administration as well.
If you had to distill sysadmin tasks to a bare minimum, a lot of the work that
is done is creating, editing, and maintaining various *plain-text* configuration
files and scripts.

What system works great with plain-text files? *Git, of course!*

## Practical Sysadmin Uses for Git

### Puppet/Salt/Ansible/Chef Configuration
Automation is essential for survival in modern enterprise. There are simply too
many tasks to be done manually and too many servers to manage individually.
Configuration Management tools allow us to stay on top of an ever-growing list
of responsibilities and manage hundreds or thousands of servers with a
relatively small technical team. As companies move to *the cloud* and fully
embrace the *software-defined data center*, configuration management tools
become even more important. As we start to treat servers like cattle and less
like pets, we need a way to rapidly provision and configure new servers. It's
great that we don't have to care about keeping a specific physical server alive
any more - but all this virtualization and shuffling around data means that we
need to be able to spin up servers and configure them faster than ever.

![](/assets/images/puppet_logo.png)

When I was still working as a Linux System Administrator at the
[Center for High Throughput Computing](http://chtc.cs.wisc.edu/) at the
University of Wisconsin, we used [Puppet](https://puppet.com/) for our server
configuration management. Traditionally, Puppet uses a standard master and agent
method for configuring servers. You have a master Puppet server that holds all
of your Puppet code, and you push that out to Puppet agents running on
all of your other servers. In the "old school" Puppet model, you would compile
the puppet code on the master server with every change and to be sent out to
every server. This leads to one major bottleneck and point of failure in your
entire server management system - the Puppet master. This server can easily become
overloaded when managing thousands of agent servers, and serves as a single
breaking point.

It turns out, Git can be used with a tool like Puppet to add both speed and
reliability to your Puppet (or other CM tool) configuration! I won't go into the
details, but you can set up a *masterless Puppet* system using Git!
[Here's](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-masterless-puppet-environment-on-ubuntu-14-04)
a great article from Digital Ocean that goes into more details about that. It's
a little dated - targeting Ubuntu 14.04, but the basic idea and workflow will
work for any system. We used a self-hosted [Gitolite](http://gitolite.com/gitolite/)
server, but just about any modern Git setup will do. The basic idea behind a
"masterless" Puppet system is to keep all of your Puppet code in your git
repository, and then have each server checkout the code and compile it on the
server itself. This prevents your master server from getting overloaded when
handling requests from thousands of servers at a time, and reduces the dependence
on a single server. Yes, you're still reliant on a Git server, but it's easier
to support and scale that Git server than a high-traffic Puppet master server.
The distributed nature of Git makes backups and restores easier as well.

Another reason to keep your Configuration Management files in a Git repository
is for easy testing and contributions from multiple administrators. If you want
to test a new configuration, in a few keystrokes you can create a new branch,
modify the code you want, and push that specific branch to a server. There's no
need to include special language in the configuration code itself about only
modifying a certain server - because only the server you choose will update from
your test branch. Additionally, you can let multiple admins run wild writing
configuration code without worry about impacting or breaking the work others
have done. Just one of the many benefits of working in a distributed Git
environment! :smile:

### Power-Up your Scripts

Scripts are the super-weapons of any System Administrator worth his or her salt.
Whether it's Python, Bash, PowerShell, Perl, or whatever else you crazy kids are
using these days, there's no reason to not keep your scripts in a Git repository.
Why?

![](/assets/images/python_logo.png)

* (Unofficial) distributed back-ups.
  * A remote Git server is **not** a perfect back-up system, but it's a hell of
  a lot better than nothing. Keep everything you write pushed to a remote Git
  server on a daily basis and the day your laptop spontaneously combusts won't be
  *quite* as bad any more. You put a lot of work into writing scripts - store
  them properly!
* Facilitate re-use.
  * Keeping your scripts in a Git repository means you can easily pull them down
  to multiple Git servers and re-use something you have written. It's also an
  easy way to let other administrators on your team make use of the awesome work
  you have done. It's possible they are trying to solve the same problem as you
  and could make good use of your existing work.
* Facilitate cooperation and community.
  * One of the greatest unintended rewards from the Git movement is how
  it facilitates a strong sense of community. Use a Git platform with good
  community features like [Github](https://enterprise.github.com/home) or
  [Gitlab](https://about.gitlab.com/) and you can start working together in ways
  you've never previously imagined!
* Versioning, branches, and diffs.
  * As I pointed out in [Git 101](/2018/04/09/git-101.html), one of the primary
  uses of Git is versioning and revision control. You can use Git to keep
  multiple versions of a script, whether it be for testing, for different
  servers, or even for different operating systems. Additionally,
  being able to "go back in time" and view your script at different points in
  its history can help you understand what is happening or why you did something
  a certain way. Commit messages are another way of adding readability to your code.
  Look at the diff between different commits to see what you changed and why!
  Need to change the script but also keep a working version? Create a test
  branch!
* Make things easy for the new guy.
  * Handing off 'the keys' to the new guy is rarely a fun or easy thing. The
  reality is that most people will change jobs/companies every couple of years.
  If you're a good administrator, you will keep everything well documented for a
  smooth handoff when you leave and someone new comes in. Having all of your
  configuration files and scripts in a remote Git repository makes that process
  remarkably better. You don't have to worry about giving them a USB drive full
  of random files and scripts with no real documentation or explanation.

### Documentation

I am *sure* you read my post on [writing in Markdown](/2018/04/03/why-markdown.html).
If you do choose to keep notes and documentation in Markdown, you can readily
store those files in a Git repository. I've got some pretty opinionated thoughts
on technical documentation that I'll have to get to in another post, but I firmly
believe the key to good documentation is that the contents is properly indexed
and searchable. If you use a Git service like Github, your entire repository is
indexed for easy searching. Huzzah! There are many choices for documentation:
from wiki pages to directories full of spreadsheets and MS Word documents...and
some are much better choices than others.

I'm not sure if writing a bunch of documents and storing them in a Git repo is
the best choice for documentation, but it's certainly not the worst, and it's
absolutely better than keeping no documentation at all! I'm in favor of wiki-style
centralized documentation sources. A self-hosted [Mediawiki](https://www.mediawiki.org/wiki/MediaWiki)
site is a great choice if you're strapped for cash. Thanks to [Docker](https://www.docker.com/)
you can get a [Mediawiki instance](https://hub.docker.com/r/_/mediawiki/) running
over your lunch break. On the enterprise-y side of things, I really like
[Atlassian's Confuence Wiki](https://www.atlassian.com/software/confluence/why-wiki-collaboration-software).

I don't have any experience with it, but there's a pretty slick wiki called
[Gitit](https://github.com/jgm/gitit) that uses Git + Markdown files to manage
knowledge! This is an awesome approach for a lightweight Wiki because it doesn't
require running a full PHP/SQL setup like Mediawiki, and it doesn't have the
costs of an enterprise setup like Confluence.

You can also write documentation (or textbooks, guides, etc) with
[Gitbook](https://www.gitbook.com/)! You can tie Gitbook into a Github account
and write documentation in Markdown. This is one model that allows a team to
collaborate and for write simple, elegant documentation, that is also easy to
share with others.

### Prototyping and Data Visualizations

As a system administrator you might find yourself tasked with quickly deploying
prototypes of various applications or websites. You can use tools like Jekyll,
Markdown, and Git to build simple websites and dashboards. Need to throw
together a small presentation to argue for a larger department budget? Aggregate
your data in a git repository and use a number of tools to help visualize that
data.

Monitoring and logging have become essential tasks for system administrators.
There are many tools for the job these days, including some personal favorites
like [Grafana](https://grafana.com/) and [Icinga](https://www.icinga.com/). These
tools are great for tapping into live applications and services to monitor different
metrics. With a little bit of work, there's a massive number of tools available for
[visualizing data](https://github.com/topics/data-visualization). A Git
repository is a great natural place to store this data - especially if it's in
a plaintext form like CSV. Using a Git repo allows you to view changes in data
over time.

----

And there you have it. Just as promised, a couple of practical uses for Git as a system
administrator.

Coming up next, we'll open up the hood of our favorite tool and get our hands
dirty as we dig into some technical details to find out how Git really works. :wrench:
