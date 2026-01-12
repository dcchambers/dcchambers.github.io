---
layout: page
---

{{ site.author.bio }}

---

- My [omg.lol](https://dakota.omg.lol/) page has a list of places you can find me online.
- Check out my [`/now` page]({% link _pages/now.md %}) to see what I'm doing _right now_.
- Check out my [`/uses` page]({% link _pages/uses.md %}) to see things I use every day.
- Check out my [list of lists]({% link _pages/lists.md %}).

## Recent Posts

<ul>
  {% for post in site.categories.blog limit:10 %}
  <li><span style="font-family: monospace; font-size:0.8em">{{ post.date | date: "%Y %m %d" }}</span> - <a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

See all [Blog Posts]({% link _pages/blog.md %}).

## Recent Links

<ul>
  {% for post in site.categories.linkblog limit:10 %}
  <li>
    <span style="font-family: monospace; font-size:0.8em">{{ post.date | date: "%Y %m %d" }}</span> - <a href="{{ post.url }}">{{ post.title }}</a>
    {% if post.categories contains 'linkblog' %}<a href="{{ post.link }}"><i class="fa-solid fa-link"></i></a>{% endif %}
  </li>
  {% endfor %}
</ul>

See all [Links]({% link _pages/linkblog.md %}).

---

See [Everything]({% link _pages/everything.md %}).
