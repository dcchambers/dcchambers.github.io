---
title: Git for Sysadmins
---

Congratulations! You survived [Git 101](/2018/04/09/git-101.html). :tada:

I'm sure you noticed that it focused on using Git from the perspective of a
software developer. A common problem with most Git documentation and tutorials
online is that they tend to be intended only for developers. Most of the
documentation aimed at System Administrators is focused around administrating
a Git server, not about really *using Git* for system administration tasks. This
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
When I was still working as a Linux System Administrator at the
[Center for High Throughput Computing](http://chtc.cs.wisc.edu/) at the
University of Wisconsin, we used [Puppet](https://puppet.com/) as our server
configuration management tool.
