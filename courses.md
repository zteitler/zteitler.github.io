---
layout: page
title: Courses
permalink: /courses
---

# Courses

{% capture newLine %}
{% endcapture %}

{% assign semesters = "Spring,Summer,Fall" | split:"," | reverse -%}
{%- assign years = site.courses | group_by: "year" | sort:"name" | reverse -%}
{% for year in years %}
  {% for semester in semesters -%}
    {%- assign courselist = site.courses | where:"year", year.name | where:"semester", semester | sort: "coursenumber" -%}
    {% if courselist.size > 0 %}
      {% for course in courselist %}
        {% if forloop.first == true %}
*{{ semester }} {{ year.name }}*
        {%- else %}
&nbsp;
        {%- endif -%}

        {%- if course.courseprefix -%}
          {%- assign printprefix = course.courseprefix -%}
        {%- else -%}
          {%- assign printprefix = "Math" -%}
        {%- endif %}

        {%- if course.coursenumber == "*" -%}
          {%- assign printcoursenumber = "" -%}
        {%- elsif course.combinedsection -%}
          {%- capture printcoursenumber -%}
            {{- printprefix }} {{ course.coursenumber -}}/{{- course.combinedsection -}},
          {%- endcapture %}
        {%- else -%}
          {%- capture printcoursenumber -%}
            {{- printprefix }} {{ course.coursenumber -}},
          {%- endcapture %}
        {%- endif -%}

        {{ newLine -}}
        : {{ printcoursenumber }} [{{ course.title }}]({%- if course.siteurl -%}{{ course.siteurl }}{%- else -%}{{ course.url }}{%- endif -%})


      {% endfor %}

    {% endif %}

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
