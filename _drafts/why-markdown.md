---
title: Why You Should Write in Markdown
---
Subtitle: Beyond the Gitub README. ?

>*What is this Markdown nonsense and why should I care? I'll give up .doc when
you pry it from my cold, dead hands.*

\- An actual quote I made up just for this blog post.

John Gruber of [Daring Fireball](https://daringfireball.net) fame created
Markdown in a fit of rage following an attempt to parse the contents of an
HTML document. ... Or at least that's how I imagined it happened.

From the inventor himself, *"The idea for Markdown is to make it easy to read,
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
* The markdown is easier to read because there are no jarring brackets/tags.


[^1]: https://daringfireball.net/projects/markdown/syntax

---
* Plaintext is king.
  * Take your words with you - no vendor lock in!
* Your choice of editor
  * Write anywhere: notepad, etc.
  * Editors like VIM or Atom
  * IDEs like IntelliJ
  * Web Editors
* Focus on the content, not the styling.
* Easily convert to HTML, but it's much easier to read than HTML
  * Responsive design with things like Jekyll.
* Convert to many different formats
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
