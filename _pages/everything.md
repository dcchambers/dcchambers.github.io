---
title: "All Posts"
permalink: /everything
layout: page
---

<ul>
  {% for post in site.posts %}
  <li>
    <span style="font-family: monospace; font-size:0.8em">{{ post.date | date: "%Y %m %d" }}</span> - <a href="{{ post.url }}">{{ post.title }}</a>
    {% if post.categories contains 'linkblog' %}<a href="{{ post.link }}"><i class="fa-solid fa-link"></i></a>{% endif %}
  </li>
  {% endfor %}
</ul>
