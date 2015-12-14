---
layout: page
title: Gaming
permalink: /gaming/
group: "navigation"
---

### Here you will find posts of mine about games I can currently playing/modding/breaking!
<ul class="post-list">
{% for post in site.categories.gaming %}
  <li>
    <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>

    <h2>
      <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
    </h2>
  </li>
{% endfor %}
</ul>