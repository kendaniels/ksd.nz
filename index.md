---
layout: default
title: Home
---

{% assign published_projects = site.projects | where_exp: "p", "p.published != false and p.published != 'false'" | sort: "date" | reverse %}

<p class="section-heading">Projects</p>

<ul class="post-list">
  {% for project in published_projects limit:5 %}
  <li class="post-list-item">
    <a href="{{ project.url | relative_url }}">{{ project.title }}</a>
    <span class="project-desc">{{ project.description }}</span>
  </li>
  {% endfor %}
</ul>

{% if published_projects.size > 5 %}
<p class="view-all"><a href="{{ '/projects/' | relative_url }}">All projects &rarr;</a></p>
{% endif %}

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
