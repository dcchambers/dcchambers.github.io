---
layout: page
---

{{ site.author.bio }}

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
