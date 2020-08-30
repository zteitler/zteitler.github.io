---
layout: page
---

<img style="float:right;margin-left:10px" src="{{ site.baseurl }}/assets/img/me_2012_08_17.png" alt="Zach Teitler" />

Department of Mathematics  
Boise State University  
1910 University Dr  
Boise, ID 83725-1555  

{{ site.email }}  
Office MB 233A


<div style="clear:both"></div>

# Current courses

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

{% assign currentcourses = site.courses | where:"shortsemester", currentshortsemester | sort:"coursenumber" %}

{% for course in currentcourses %}
[{{ course.title }}]({% if course.siteurl %}{{ course.siteurl }}{% else %}{{ course.url }}{% endif %})
{% if course.courseprefix %}{{ course.courseprefix }} {% else %} Math {% endif %} {{ course.coursenumber }}, {{ course.semester }} {{ course.year }}
{% endfor %}


# Recent publications

{% for pub in site.publications limit: 6 %}

[{{ pub.title }}]({% if pub.siteurl %}{{ pub.siteurl }}{% else %}{{ pub.url }}{% endif %})
{{ pub.excerpt | remove: '<p>' | remove: '</p>' | strip }}
{% comment %}
<span class="post-meta"><span class="category_name">{{ pub.categories }}</span> posted on {{ pub.date | date: "%b %-d, %Y" }}</span>
{% endcomment %}

{% endfor %}


# Links

[Boise State Topology & Algebra Research](https://www.boisestate.edu/math/research/topology/) in the BSU math department

[Boise Math Circles](https://www.boisestate.edu/math/circles/) Math for teachers and for secondary students
