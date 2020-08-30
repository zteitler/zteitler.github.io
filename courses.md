---
layout: page
title: Courses
permalink: /courses
---

# Courses

{% assign semesters = "Spring,Summer,Fall" | split:"," %}
{% assign years = site.courses | group_by: "year" %}
{% for year in years %}
  {% for semester in semesters -%}
    {%- assign courselist = site.courses | where:"year", year.name | where:"semester", semester | sort: "coursenumber" -%}
    {%- if courselist.size > 0 -%}
      {% for course in courselist -%}
        {% if forloop.first == true -%}
          *{{ semester }} {{ year.name }}*
        {%- else -%}
          &nbsp;
        {% endif %}

: [{{ course.title }}]({% if course.siteurl %}{{ course.siteurl }}{% else %}{{ course.url }}{% endif %})
        {% if course.courseprefix %}{{ course.courseprefix }} {% else %} Math {% endif %} {{ course.coursenumber }}
      {% endfor %}
    {%- endif -%}
  {% endfor %}
{% endfor %}



{% comment %}

**OLD STUFFFFF**

{% assign prevyear = "X" %}

{% for course in site.courses %}
{% if course.year != prevyear %} *{{ course.year }}* {% assign prevyear = course.year %} {% else %} &nbsp; {% endif %}

: [{{ course.title }}]({% if course.siteurl %}{{ course.siteurl }}{% else %}{{ course.url }}{% endif %})
{% if course.courseprefix %}{{ course.courseprefix }} {% else %} Math {% endif %} {{ course.coursenumber }}, {{ course.semester }} {{ course.year }}

{% endfor %}

{% endcomment %}
