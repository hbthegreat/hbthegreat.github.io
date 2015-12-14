---
layout: page
title: Programming
permalink: /programming/
group: "navigation"
---

### Here you will find posts of mine that are related to Programming. Whether that be projects, educational posts, tech trials or just general rants about software.
<ul class="post-list">
{% for post in site.categories.programming %}
  <li>
    <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>

    <h2>
      <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
    </h2>
  </li>
{% endfor %}
</ul>