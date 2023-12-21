---
layout: page
title: Teaching
---

# Teaching

{% assign currentyear = "now" | date:"%Y" %}
{% assign last_day_of_spring = currentyear | append:"-05-15" | date:"%s" %}
{% assign last_day_of_summer = currentyear | append:"-08-15" | date:"%s" %}
{% assign currentdate = "now" | date:"%s" %}
{% if currentdate < last_day_of_spring %}
  {% assign currentsemester = "Spring" %}
  {% assign currentsemesterabbrev = "A" %}
{% elsif currentdate < last_day_of_summer %}
  {% assign currentsemester = "Summer" %}
  {% assign currentsemesterabbrev = "B" %}
{% else %}
  {% assign currentsemester = "Fall" %}
  {% assign currentsemesterabbrev = "C" %}
{% endif %}
{% assign currentshortsemester = currentyear | append:currentsemesterabbrev %}

{% capture newLine %}
{% endcapture %}

### Office hours

I am here to support your learning.
I encourage you to meet with me when you feel that you need support or assistance.

In Spring 2024 I will be available:

**Office hours:**
: Tuesdays 10:00am-1:00pm

**Additional appointments:**
: Email me to set up an appointment on other days or times

Office hours will be in-person in my office, or on Zoom if requested.

---

### Current semester ({{ currentsemester }} {{ currentyear }}):

{% assign currentcourses = site.courses | where:"shortsemester", currentshortsemester | sort:"coursenumber" %}

{% for course in currentcourses %}
[{{ course.title }}]({% if course.siteurl %}{{ course.siteurl }}{% else %}{{ course.url }}{% endif %})
{% if course.courseprefix %}{{ course.courseprefix }} {% else %} Math {% endif %} {{ course.coursenumber }}
{% endfor %}

---

### Upcoming semesters:

{% assign semesters = "A,B,C" | split:"," -%}
{%- assign years = site.courses | group_by: "year" | sort:"name" | reverse -%}
{% for year in years %}
  {% for semesterabbrev in semesters -%}
  {%- case semesterabbrev -%}
    {%- when "A" -%}
      {%- assign semester="Spring" -%}
    {%- when "B" -%}
      {%- assign semester="Summer" -%}
    {%- when "C" -%}
      {%- assign semester="Fall" -%}
    {%- else -%}
      {%- assign semester="Other" -%}
  {%- endcase -%}
  {%- if year.name >= currentyear -%}
  {%- if year.name > currentyear or semesterabbrev > currentsemesterabbrev -%}
    {%- assign thissemester = year.name | append:semesterabbrev -%}
    {%- assign courselist = site.courses | where:"shortsemester", thissemester | sort: "coursenumber" -%}
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

  {%- endif -%}
  {%- endif -%}
  {% endfor %}

{% endfor %}

Upcoming courses are tentative (subject to change).


---

### Previous semesters:

#### At Boise State University (2010-present):

{% assign semesters = "A,B,C" | split:"," | reverse -%}
{%- assign years = site.courses | group_by: "year" | sort:"name" | reverse -%}
{% for year in years %}
  {% for semesterabbrev in semesters -%}
  {%- case semesterabbrev -%}
    {%- when "A" -%}
      {%- assign semester="Spring" -%}
    {%- when "B" -%}
      {%- assign semester="Summer" -%}
    {%- when "C" -%}
      {%- assign semester="Fall" -%}
    {%- else -%}
      {%- assign semester="Other" -%}
  {%- endcase -%}
  {%- if year.name <= currentyear -%}
  {%- if year.name < currentyear or semesterabbrev < currentsemesterabbrev -%}
    {%- assign thissemester = year.name | append:semesterabbrev -%}
    {%- assign courselist = site.courses | where:"shortsemester", thissemester | sort: "coursenumber" -%}
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

  {%- endif -%}
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
