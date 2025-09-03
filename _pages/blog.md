---
title: "All Blog Posts"
permalink: /blog
layout: page
author_profile: true
---

<ul>
  {% for post in site.categories.blog %}
  <li>
    {{ post.date | date: "%-d %B %Y" }} - <a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
