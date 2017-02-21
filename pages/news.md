---
layout: default
title: News
permalink: /news/
---

# News 

{% comment %}
{% assign news = (site.posts | where: "category" , "news") %}
{% for post in news %}
  <div class="post">
    <h2><a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a></h2>
    <div class="post-meta">
        {{ post.date | date: "%b %-d, %Y" }}
        {% if post.author %} • Written by {{ post.author }} {% endif %} • Spark Framework Tutorials
     </div>
    <p>{{ post.summary }}</p>
  </div>
{% endfor %}
{% endcomment %}
