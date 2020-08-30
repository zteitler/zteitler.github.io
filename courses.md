---
layout: page
title: Courses
permalink: /courses
---

# Courses

{% assign currentyear = "now" | date:"%Y" %}
{% assign last_day_of_spring = currentyear | append:"-05-15" | date:"%s" %}
{% assign last_day_of_summer = currentyear | append:"-08-15" | date:"%s" %}
{% assign currentdate = "now" | date:"%s" %}
{% if currentdate < last_day_of_spring %}
  {% assign currentsemester = "Spring" %}
  {% assign currentshortsemester = currentyear | append:"A" %}
{% elsif currentdate < last_day_of_summer %}
  {% assign currentsemester = "Summer" %}
  {% assign currentshortsemester = currentyear | append:"B" %}
{% else %}
  {% assign currentsemester = "Fall" %}
  {% assign currentshortsemester = currentyear | append:"C" %}
{% endif %}

### Current semester ({{ currentsemester }} {{ currentyear }}):


{% assign currentcourses = site.courses | where:"shortsemester", currentshortsemester | sort:"coursenumber" %}

{% for course in currentcourses %}
[{{ course.title }}]({% if course.siteurl %}{{ course.siteurl }}{% else %}{{ course.url }}{% endif %})
{% if course.courseprefix %}{{ course.courseprefix }} {% else %} Math {% endif %} {{ course.coursenumber }}
{% endfor %}

---

### Upcoming semesters:

In Spring 2021 I will be teaching (subject to change):
- Math 301, Introduction to Linear Algebra
- Math 414/514, Real Analysis
- Math 599, Graduate Seminar II: Professional Preparation

---

### Previous semesters:

#### At Boise State University (2010-present):

{% capture newLine %}
{% endcapture %}

{% assign semesters = "Spring,Summer,Fall" | split:"," | reverse -%}
{%- assign years = site.courses | group_by: "year" | sort:"name" | reverse -%}
{% for year in years %}
  {% for semester in semesters -%}
  {%- unless year.name == currentyear and semester == currentsemester -%}
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

  {% endunless %}
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



#### At Texas A&M University (2007-2010):
*Spring 2010*
: Math 152

*Fall 2009*
: Math 152

*Spring 2009*
: Math 152

*Fall 2008*
: Math 311 (Topics in Applied Math I)

*Spring 2008*
: Math 152 (Calculus II)

*Fall 2007*
: Math 141 (Business Math I)



#### At Southeastern Louisiana University (2005-2007):
*Spring 2007*
: Math 200
: Math 450 (Complex Variables)

*Fall 2006*
: Math 162 (Trigonometry)
: Math 201 (Calculus II)

*Spring 2006*
: Math 161
: Math 200

*Fall 2005*
: Math 161 (College Algebra)
: Math 200 (Calculus I)
