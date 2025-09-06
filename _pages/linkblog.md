---
layout: page
title: Linkblog
permalink: /linkblog
---

This is my linkblog! It's a list of interesting links that I want so share, and maybe comment on.

<ul>
  {% for post in site.categories.linkblog %}
  <li>
    <span style="font-family: monospace; font-size:0.8em">{{ post.date | date: "%Y %m %d" }}</span> - <a href="{{ post.url }}">{{ post.title }}</a> <a href="{{ post.link }}"><i class="fa-solid fa-link"></i></a>
  </li>
  {% endfor %}
</ul>
