---
layout: page
title: Unfiltered Thoughts
permalink: /blog/
---

<ul class="post-list">
  {%- for post in site.posts -%}
  <li>
    <a class="post-link" href="{{ post.url | relative_url }}">
      {{ post.title | escape }}
    </a>
    <span class="post-date">{{ post.date | date: "%B %-d, %Y" }}</span>
  </li>
  {%- endfor -%}
</ul>