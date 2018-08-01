---
title: On Keeping Notes
---

I made a tiny script for keeping simple text-based notes.
You might find it useful too.  
Introducing: [Note Keeper](https://github.com/dcchambers/note-keeper)

---

I am a devout member of the [bullet journal](http://bulletjournal.com/) cult.
But I tend to be picky about what I write down in my journal and, let's be
honest, it's often faster to type than to write, especially when you're already
sitting in front of a keyboard or you have to copy/paste a long string of
nonsensical characters.

I've gone through a couple of iterations of note taking processes when working.
I work almost exclusively in Linux these days and am regularly working from the
command line. My work-flow is pretty much a shell + tmux + a hundred different
command line applications.

Here's a note-taking system I use with a tiny shell script to make simple
notes (TODO lists, copy/paste clipboard, poems, etc).

This is how I used to keep notes:
* Keep a master notebook at ~/notebook.md
* Switch to my NOTES window in tmux.
* Open up the notebook with vim.
* Write whatever I need.
* Switch back to my working window in tmux.

[![asciicast](https://asciinema.org/a/194447.png)](https://asciinema.org/a/194447)

And this is how I keep notes now:
* Use my `note` script to open up a new note at ~/notes/year/month/day.md.

[![asciicast](https://asciinema.org/a/194428.png)](https://asciinema.org/a/194428)

---

Originally, I had simply aliased the `note` command to create and edit a new
markdown note in a certain location. I decided to expand upon that idea...

That became [Note Keeper](https://github.com/dcchambers/note-keeper) - a tiny
shell script for keeping notes. It's pretty basic right now.
You can:
* Create notes
* Edit notes
* Print a note

Planned additions:
* Destroy a note
* Print information about a note
* Encrypt a secret note
* Directly/immediately append a string to the end of a note

---

Use *Note Keeper* to make TODO lists, create ASCII art, write poems, or as a
copy/paste clipboard.
* Note Keeper will automatically create a `$day.md` markdown note for you
* It will organize it in a sane way (in the directory `~/notes/$year/$month/`)
* It will open the note up for editing in Vim.
* Simply install the script and type `note` on your command line.
* Probably[^1] compatible with Mac OS and most Linux distributions.

Check out the source code on :octocat: [Github.](https://github.com/dcchambers/note-keeper)  
Currently v0.1 :tada: :wink:

[^1]: Tested on Mac OS High Sierra and Ubuntu 16.04 LTS.
