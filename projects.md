---
layout: default
title: Projects
permalink: /projects/
---

{% assign published_projects = site.projects | where_exp: "p", "p.published != false and p.published != 'false'" | sort: "date" | reverse %}

<p class="section-heading">Projects</p>

<ul class="post-list">
  {% for project in published_projects %}
  <li class="post-list-item">
    <a href="{{ project.url | relative_url }}">{{ project.title }}</a>
    <span class="project-desc">{{ project.description }}</span>
  </li>
  {% endfor %}
</ul>
