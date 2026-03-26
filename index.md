---
layout: default
title: Home
---

<p class="section-heading">Projects</p>

<ul class="post-list">
  {% assign project_count = 0 %}
  {% assign sorted_projects = site.projects | sort: "date" | reverse %}
  {% for project in sorted_projects %}
  {% if project.published == false or project.published == "false" %}{% continue %}{% endif %}
  {% if project_count >= 5 %}{% break %}{% endif %}
  <li class="post-list-item">
    <a href="{{ project.url | relative_url }}">{{ project.title }}</a>
    <span class="project-desc">{{ project.description }}</span>
  </li>
  {% assign project_count = project_count | plus: 1 %}
  {% endfor %}
</ul>

<p class="section-heading">Writing</p>

{% assign posts_by_year = site.posts | group_by_exp: "post", "post.date | date: '%Y'" %}
{% for year in posts_by_year %}
<p class="post-list-year">{{ year.name }}</p>
<ul class="post-list">
  {% for post in year.items %}
  <li class="post-list-item">
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%b %-d" }}</time>
  </li>
  {% endfor %}
</ul>
{% endfor %}
