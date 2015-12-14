---
layout: page
title: General
permalink: /general/
group: "navigation"
---

### Here you will find posts of mine that don't necessarily fit any other category and may or may not be just general ranting.
<ul class="post-list">
{% for post in site.categories.general %}
  <li>
    <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>

    <h2>
      <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
    </h2>
  </li>
{% endfor %}
</ul>