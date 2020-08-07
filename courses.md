---
layout: page
title: Courses
permalink: /courses
---

# Courses

{% assign prevyear = "X" %}
{% assign lower = "January 1, 2016" | date: '%s' %}

{% for post in site.categories.courses %}
  {% assign postdate = post.date | date: '%s' %}
  {% if postdate >= lower %}

{% assign postyear = post.date | date: "%Y" %}
{% if postyear != prevyear %} *{{ postyear }}* {% assign prevyear = postyear %} {% else %} &nbsp; {% endif %}

: [{{ post.title }}]({% if post.siteurl %}{{ post.siteurl }}{% else %}{{ post.url }}{% endif %}) {{ post.excerpt | remove: '<p>' | remove: '</p>' }}

  {% endif %}
{% endfor %}

([View all past courses](/allcourses))
