---
title: Why You Should Write in Markdown
---
Subtitle: Beyond the Gitub README. ?

>*What is this Markdown nonsense and why should I care? I'll give up .doc when
you pry it from my cold, dead hands.*

\- An actual quote I made up just for this blog post.

John Gruber of [Daring Fireball](https://daringfireball.net) fame had a problem.
After years of writing and reading HTML, he found himself sporadically inserting
HTML tags into his everyday writing. His WYSIWYG text editor wasn't responding
to his creative desires. His emails were boring, unformatted text blobs. Yet he
was able to get by. That was, at least, until *the incident*. One day John
stumbled upon an ancient HTML document...a document that contained
[a secret](https://en.wikipedia.org/wiki/P_versus_NP_problem) every computer
scientist, mathematician, and amateur programmed wants to know. But this
document was marred by thousands of now obsolete HTML tags and other garbage
associated with the ancient language. Parsing the contents proved challenging,
but he began to uncover the secrets until he made a critical mistake. Due to
something we now call *tag fatigue*, John unknowingly skipped over a small line
and missed a crucial sentence explaining the timed self-destructing nature of
the document. He was exhausted from a day of decrypting the ancient language and
went to sleep, only to return the next morning and find the entire file wiped
from existence. Had John not suffered that *tag fatigue* he might have hurriedly
copied the file, snapped a photo, or pushed on into the wee hours of the night.
In a fit of rage John cried out, cursing the Computer Gods. The Gods answered,
and told John the path to true righteousness was through a language he would
create. On what we now call the First Day, John named his creation Markdown.

At least that's how I imagined it happened.

### So, What is Markdown?

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

### Plain Text is King.

[^1]: [Daring Fireball](https://daringfireball.net/projects/markdown/syntax)
[^2]: Okay, there's a time and a place for everything.

---
* Plaintext is king.
  * Take your words with you - no vendor lock in!
  * Use Version Control
  * Convert to many different formats
  * Focus on the content, not the styling.
* Your choice of editor
  * Write anywhere: notepad, etc.
  * Editors like VIM or Atom
  * IDEs like IntelliJ
  * Web Editors
* Easily convert to HTML, but it's much easier to read than HTML
  * Responsive design with things like Jekyll.
* Add images, links, other content easily.
* LaTeX Equations
  * Why not write all in LaTeX? Markdown is more transportable!
* Open standard
* Use Cases
  * Beyond the README.
    * Most people are familiar with Markdown via github README files.
    * Potential for much more.
  * Static Web Pages
  * Blog Posts
  * Documentation
  * Academic Papers
    * LaTeX
* In-line HTML when Markdown fails you.
  * Markdown + HTML + LaTeX = Super Powers
