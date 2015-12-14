---
layout: page
title: Entrepreneurial
permalink: /entrepreneurial/
group: "navigation"
---

### Here you will find posts of mine that are related to my own entrepreneurial adventures or other peoples projects that I find particularly interesting
<ul class="post-list">
{% for post in site.categories.entrepreneurial %}
  <li>
    <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>

    <h2>
      <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
    </h2>
  </li>
{% endfor %}
</ul>