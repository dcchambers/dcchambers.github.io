---
title: "All Blog Posts"
permalink: /blog
layout: page
---

<ul>
  {% for post in site.categories.blog %}
  <li><span style="font-family: monospace; font-size:0.8em">{{ post.date | date: "%Y %m %d" }}</span> - <a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
