---
layout: default
title: Raccoon's Trash Can
---

___

Hi! I’m a raccoon, and this is my trash can. It’s full of my thoughts about the mess of being human :]

Check out __[about me](about-me)__ section to find out who I am‼️

Want a random quote from my collection? See my [**random quote page**](random-quotes)

Remember to [**“Immerse your soul in love”**](https://youtu.be/LCJblaUkkfc?t=227)                                                                                          
*-* Street Spirit (Fade Out), Radiohead  - The Bends, 1995

You can reach out to me via [**email**](mailto:ash.pacelt@gmail.com) 

---

**Latest posts:**

<ul class="blog-posts" markdown="1">
  {% for post in site.posts limit:4 %}
    <li>
      <span>
        <i>
          <time datetime="{{ post.date | date_to_xmlschema }}">
            {{ post.date | date: "%d %B, %Y" }}
          </time>
        </i>
      </span>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>

---

Subscribe to my [**RSS feed**](https://raccoonfangz.github.io/feed.xml) :D
