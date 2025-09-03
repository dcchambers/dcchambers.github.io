---
title: "All Posts"
permalink: /everything
layout: page
author_profile: true
---

<ul>
  {% for post in site.posts %}
  <li>
    {{ post.date | date: "%-d %B %Y" }} - <a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
