---
layout: page
title: Publications
permalink: /publications
mathjax: true
---

# Publications

{% assign prevyear = "X" %}
{% assign lower = "January 1, 2016" | date: '%s' %}

{% for post in site.categories.publications %}
  {% assign postdate = post.date | date: '%s' %}
  {% if postdate >= lower %}

{% assign postyear = post.date | date: "%Y" %}
{% if postyear != prevyear %} *{{ postyear }}* {% assign prevyear = postyear %} {% else %} &nbsp; {% endif %}

: [{{ post.title }}]({% if post.siteurl %}{{ post.siteurl }}{% else %}{{ post.url }}{% endif %})
{% if post.courseprefix %}{{ post.courseprefix }} {% else %} Math {% endif %} {{ post.coursenumber }}, {{ post.semester }} {{ post.year }}

  {% endif %}
{% endfor %}

([View all publications](/allpublications))

Testing MathJax: $ xy = \frac{1}{4} (x+y)^2 - \dfrac{1}{4} (x-y)^2 $
