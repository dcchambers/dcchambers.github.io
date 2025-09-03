---
layout: page
title: "Year In Review"
permalink: /year-in-review
---

<ul>
  {% for post in site.posts %}
    {% if post.tags contains 'year-in-review' %}
  <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endif %}
  {% endfor %}
</ul>
