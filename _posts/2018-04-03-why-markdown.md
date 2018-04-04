---
title: Why You Should Write in Markdown
---

>*What is this Markdown nonsense and why should I care? I'll give up .doc when
you pry it from my cold, dead hands.*

\- An actual quote I made up just for this blog post.

John Gruber, of [Daring Fireball](https://daringfireball.net) fame, had a
problem. After years of writing and reading HTML, he found himself sporadically
inserting HTML tags into his everyday writing. His WYSIWYG text editor wasn't
responding to his creative desires. His emails were boring, unformatted text
blobs. Yet he was able to get by.  

That was, at least, until *the incident*. One day John stumbled upon an ancient
HTML document...a document that contained
[a secret](https://en.wikipedia.org/wiki/P_versus_NP_problem) every computer
scientist, mathematician, and amateur programmed wants to know. But this
document was marred by thousands of now obsolete HTML tags and other garbage
associated with the ancient language.  

Parsing the contents proved challenging, but he began to uncover the secrets
until he made a critical mistake. Due to something we now call *tag fatigue*,
John unknowingly skipped over a small line and missed a crucial sentence
explaining the timed self-destructing nature of the document. He was exhausted
from a day of decrypting the ancient language and went to sleep, only to return
the next morning and find the entire file wiped from existence. Had John not
suffered that *tag fatigue* he might have hurriedly copied the file, snapped a
photo, or pushed on into the wee hours of the night.  

In a fit of rage John cried out, cursing the Computer Gods. The Gods answered,
and told John the path to true righteousness was through a language he would
create. On what we now call the First Day, John named his creation Markdown.

At least that's how I imagined it happened.

## So, What is Markdown?

From the creator himself, *"The idea for Markdown is to make it easy to read,
write, and edit prose. HTML is a publishing format; Markdown is a writing
format."*[^1]

Let's take a look at this simple example. The first is valid HTML and the
second is valid Markdown. The generated content is identical.

```
A <i>quick</i> brown fox <del>hopped</del> jumped over the <b>lazy</b> dog.
```

```
A *quick* brown fox ~~hopped~~ jumped over the **lazy** dog.
```
A *quick* brown fox ~~hopped~~ jumped over the **lazy** dog.

* The HTML Markup takes 25% more characters (75 vs. 60) to represent the same
content.
* The markdown is (subjectively) easier to read because there are no jarring
brackets/tags.
* The displayed content is identical because Markdown is converted to HTML when
viewed in a web browser. That said, this proves you don't have to write/read
boring old HTML when writing and reading prose.

In essence, Markdown is a lightweight markup language that can be converted to
many other languages. It is a tool to create rich text content using plain text.
And you should be using it for all[^2] of your writing. Here's why.

## Plain Text is King.

Perhaps the most important feature of Markdown is that it is written in simple
plain text format. This means the characters that appear on your screen are
exactly the characters that your computer writes to the file on your hard
drive.[^3] Here's why that matters:

* Take your Words with you - no Vendor Lock-In!
  * If you find yourself writing important documents in .doc or some other
  proprietary format, you will find yourself *locked in* to that text editing
  environment. If you try to open that document with anything other than the
  supported, often non-free editor, it will look like gibberish. Anyone that
  wants to view or edit your file is going to need to use their software, and
  you will always need to if you want to open or edit your own file long into
  the future.
* Use Version Control for Back-Ups, Versioning, and Editing.
  * I'm sure you already know how amazing Git is. If not you'll have to wait for
  me to explain that in another blog post. The beauty of plain text is that it
  allows your files to work properly with version control. Version control works
  by looking at the *diffs* of various verions of a file. It's nearly impossible
  to track a file diff in a proprietary or binary format, but it's pretty simple
  with plain text documents! This means you can version control your documents
  the same way you would code.
    * You can use version control like Git as a distributed back up system.
    * As the name implies, use version control to create and maintain different
    versions of your writing. Want to start rewriting something while keeping an
    unchanged copy of the original? Easy! Just make a new branch and make your
    changes, while your original is always there for reference.
    * Version control is also great for editing. Let anyone view/edit your files
    without affecting the original by using a
    [git branching model.](http://nvie.com/posts/a-successful-git-branching-model/)
* Convert to Other Formats.
  * Markdown can be converted to pretty much any relevant format these days.
  While you write in plain text, there's no reason you have to read it that way!
  Convert your Markdown document to PDF, LaTeX, HTML, etc. There's a plethora of
  tools available, but one of my favorites is [Pandoc](https://pandoc.org/).
* Focus on the Content, not the Styling.
  * As I pointed out in my <sup>totally non-fiction</sup> account of the creation
  of Markdown earlier, the real beauty of Markdown and plain text is that it
  allows you, the writer, to focus on the content itself. Markdown lets you do
  simple but powerful styling without getting in your way. **Emphasize text** in
  a way that makes sense, not with tiresome HTML tags or the need to take your
  hands off the keys and click on the "bold" button in a WYSIWYG editor. To **bold**
  text in Markdown, simply surround the word(s) in a pair of asterisks. It looks
  great when formatted and it's easy to read as plain text.
  * Markdown supports a number of powerful styling tools, like Headers, text
  styling, images, automatic URLs, lines, tables, indented lists, and more. The
  best part is, because Markdown support in-line HTML, you can always add anything
  that it doesn't natively support (like <sup>superscripts</sup>) by throwing in
  the occasional HTML tag.
* Your Choice of Editor.
  * Write anything, anywhere, with virtually any tool. Use a classic editor like
  [Vim](https://www.vim.org/) or [Emacs](https://www.gnu.org/software/emacs/).
  Use a simple tool like Notepad. Use a modern editor such as
  [Atom](https://atom.io/) or [VS Code](https://code.visualstudio.com/). Use a
  full-blown IDE like [IntelliJ IDEA](https://www.jetbrains.com/idea/). Write
  directly on [the web](https://tobloef.com/markant/).
  [Collaborate in real-time](https://teletype.atom.io/).
  Do **what you want** because this is **your content**. Many editors have
  plugins or native support for previewing Markdown. There are also many powerful
  plugins to help you write better content. Spell-checking, tab completion, :smile:
  emoji support, and more.

## Create Beautiful Web Content, no HTML Needed.

This blog post is written in Markdown. You can even view the
[source code](https://github.com/dcchambers/dcchambers.github.io/blob/master/_posts/2018-04-03-why-markdown.md). This website was created using a static site generator called [Jekyll](https://jekyllrb.com/).
It turns a couple of YAML (*plain text* configuration files) and Markdown files
into a full-blown HTML website. There's a massive number of themes available,
and the capabilities are pretty much limited to the scope of your imagination.
The best part? Because the pages you create are written in Markdown, you still
have access to awesome content styling but retain the readability of plain text.

With tools Jekyll I can easily take a paper written in Markdown and convert it
into a responsive web page, ready for popular consumption by anyone with an
[internet-connected device](https://en.wikipedia.org/wiki/Global_Internet_usage).
I can then use a tool like Pandoc to convert my Markdown paper to PDF, print it,
and distribute it to those of us left in the stone age.

## LaTeX without LaTeX.

LaTeX is awesome. LaTeX is also the worst thing on earth. It's an incredibly
powerful typesetting tool that's also incredibly hard to read and write with a
learning curve so steep it makes Lombard Street look as flat as a pancake. It's
most commonly and famously used as the standard for writing academic papers.
Where LaTeX really shines is in creating complex mathematical formulas.

Why am I mentioning this in a paper on Markdown? Well, many Markdown interpreters
have in-line LaTeX support. This means you can use LaTeX to add math and other
complex items to your Markdown document!

For example, I've selected [kramdown](https://kramdown.gettalong.org/index.html)
as the Markdown "version" in this document. (Kramdown is actually a Markdown
"version" but rather a Ruby library for parsing and converting a superset of
Markdown, but that's pedantic. :wink: Kramdown, along with many other Markdown
varients, support LaTeX-like typesetting. Take a look at
[this excellent post](http://www.gastonsanchez.com/visually-enforced/opinion/2014/02/16/Mathjax-with-jekyll/)
for how to use LaTeX within Markdown via the [MathJax](https://www.mathjax.org/)
JS library.

That begs the question - why not just write everything in LaTeX?
* While LaTeX is ultimately more powerful for formatting and styling, the best
feature of Markdown is that it gets out of your way and lets you focus on writing.
Combine your Markdown document with a little in-line HTML and LaTeX, and you've
basically got content creation super powers!

## Use Cases for Markdown

Most people are familiar with Markdown from GitHub README files. It's awesome
that GitHub has chosen this as the default format for README files in Github
repositories, but it's a shame most people don't think to use Markdown for
anything more than that.

Here are some things you could use Markdown for:
* Personal Notes
* To-Do Lists
* Organized Lists/Outlines
* Static Web Pages
* Blog Posts
* Documentation
* Academic Papers[^4]
* Long-Form Journalism
* Technical Writing
* Fiction
* Emails
* And yes, awesomely-formatted README files.
<br><br>

[^1]: [Daring Fireball](https://daringfireball.net/projects/markdown/syntax)
[^2]: Okay, there's a time and a place for everything.
[^3]: Well, not *exactly*, per say. But let's pretend the computer writes unicode characters instead of 0s and 1s.
[^4]: When you solve P vs. NP you better write your paper in Markdown, lest you suffer the same fate as John. :smile:
