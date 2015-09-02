---
layout: tutorial_main
title: Tutorials
permalink: /tutorials/
---

<div class="posts">
{% for post in site.categories.tutorials %}
  <div class="post">
    <h2><a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a></h2>
    <div class="post-meta">
        {{ post.date | date: "%b %-d, %Y" }}
        {% if post.author %} • Written by {{ post.author }} {% endif %} • Spark Framework Tutorials
     </div>
    <p>{{ post.summary }}</p>
  </div>
{% endfor %}
</div>
