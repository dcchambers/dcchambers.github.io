---
title: "A List of Lists"
permalink: /lists
layout: page
---

<ul>
  {% for list in site.lists %}
  <li><a href="{{ list.url }}">{{ list.title }}</a></li>
  {% endfor %}
</ul>
