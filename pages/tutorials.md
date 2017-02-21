---
layout: default
title: Tutorials
permalink: /tutorials/
---

{% include tutorialNav.html %}
{% assign tutorials = (site.posts | where: "layout" , "tutorial") %}
{% for tutorial in tutorials %}
<div class="tutorial">
  <h2><a href="{{ tutorial.url }}">{{ tutorial.title }}</a></h2>
  <div class="post-meta">
      {{ tutorial.date | date: "%b %-d, %Y" }}
      {% if tutorial.author %} • Written by {{ tutorial.author }} {% endif %} • Spark Framework Tutorials
   </div>
  <p>{{ tutorial.summary }}</p>
</div>
{% endfor %}
