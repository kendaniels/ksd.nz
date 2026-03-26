---
layout: default
title: Projects
permalink: /projects/
---

<p class="section-heading">Projects</p>

<ul class="post-list">
  {% assign sorted_projects = site.projects | sort: "date" | reverse %}
  {% for project in sorted_projects %}
  {% if project.published == false or project.published == "false" %}{% continue %}{% endif %}
  <li class="post-list-item">
    <a href="{{ project.url | relative_url }}">{{ project.title }}</a>
    <span class="project-desc">{{ project.description }}</span>
  </li>
  {% endfor %}
</ul>
