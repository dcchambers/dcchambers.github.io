---
title: Celebrate Valentine's Day with Bash!
---

If you're using a modern terminal emulator with unicode support
(for example, the default Gnome terminal shipped with Ubuntu)
you can add Emoji to your bash prompt.

If you've never changed your bash prompt, it probably looks something like this:
* `username@hostname ~ $`

You can customize your prompt within your `.bashrc` file!

Feeling lonely today? Can't wait to get home to a loved one? Add a [heart](https://emojipedia.org/heavy-black-heart/)
:heart: emoji to your bash prompt for a cheerful reminder.

## Change your Bash Prompt

Your bash prompt is set with the `$PS1` variable in your `.bashrc` file.

1. Open up `~/.bashrc` with your favorite editor.
2. Comment out the existing `$PS1=...` line
3. Add the following: `PS1='\[\e[35m\]❤\[\e[m\]  \w $ '`
  - The `\[\e[35m\] ... \[\e[m\]` text sets the color to magenta/pink.
4. Reload your bash profile with the command: `$ source ~/.bashrc`
5. Your prompt should now have a colorful heart! Hurray!
![](/assets/images/bash-heart.png)
