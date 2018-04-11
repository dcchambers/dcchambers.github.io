---
title: Git for Sysadmins
---

Congratulations! You survived [Git 101](/2018/04/09/git-101.html). :tada:

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
Automation is essential to survival in modern enterprise. There are simply too
many tasks to be done manually, and too many servers to manage individually.
Configuration Management tools allow us to stay on top of an ever-growing list
of responsibilities and manage hundreds or thousands of servers with a
relatively small technical team. As companies move to *the cloud* and fully
embrace the *software-defined data center*, configuration management tools
become even more important. As we start to treat servers like cattle and less
like pets, we need a way to rapidly provision and configure new servers. It's
great that we don't have to care about keeping a specific physical server alive
any more - but all this virtualization and shuffling around data means that we
need to be able to spin up servers and configure them faster than ever.

When I was still working as a Linux System Administrator at the
[Center for High Throughput Computing](http://chtc.cs.wisc.edu/) at the
University of Wisconsin, we used [Puppet](https://puppet.com/) as our server
configuration management tool.
