---
layout: page
author_profile: true
---

Hey there, I'm Dakota!

I am a software engineer and tech lead at [Zendesk](https://www.zendesk.com) working on the Engineering Productivity - Deploy Platform team.
We build tools for configuring and deploying software to millions of customers around the world.

When I'm not in front of a computer I enjoy running, biking, reading, baking sourdough bread and pizza, and drinking coffee.
I live in Wisconsin with my wife, two young kids, and dog.

---

- My [omg.lol](https://dakota.omg.lol/) page has a list of places you can find me online.
- Check out my [`/now` page]({% link _pages/now.md %}) to see what I'm doing _right now_.
- Check out my [`/uses` page]({% link _pages/uses.md %}) to see things I use every day.

---

## Recent Posts

<ul>
  {% for post in site.posts limit:10 %}
  <li>
    {{ post.date | date: "%-d %B %Y" }} - <a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

---

See [Everything]({% link _pages/everything.md %}) or [Just Blog Poosts]({% link _pages/blog.md %}).
