---
layout: page
mathjax: true
---

#### Professor, [Department of Mathematics](https://www.boisestate.edu/math/), [Boise State University](https://www.boisestate.edu/)


<img style="float:right;margin-left:10px" src="{{ site.baseurl }}/assets/img/me_2012_08_17.png" alt="Zach Teitler" />

Department of Mathematics  
Boise State University  
1910 University Dr  
Boise, ID 83725-1555, USA  

<zteitler@boisestate.edu>  
Office: [MB 233A](https://maps.boisestate.edu/?id=715#!m/89068)  
Phone: +1-208-426-1086  
Fax: +1-208-426-1356  

Pronouns: he/him/his  


<div style="clear:both"></div>



## [Teaching](/teaching)

I teach a range of courses,
mostly proof-based (or "pure math") courses for undergraduate and graduate math majors.
I also frequently teach multivariable calculus and introduction to proofs,
and occasionally other classes: differential equations, linear algebra, and so on.

### Student times

I am here to support your learning.
I encourage you to meet with me when you feel that you need support or assistance.

In Fall 2021 I will be available:

**Student drop-in hours:**
: Thursdays 10:30am-12:30pm

**Student appointment hour:**
: Thursdays 12:30pm-1:30pm (email me to set up an appointment within this hour in 15-minute segments)

**Additional appointments:**
: Email me to set up an appointment on other days or times

Student times will be remote via Zoom
using my **office zoom link** (listed in Canvas, or email me for the link).


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
  {% assign nextshortsemester = currentyear | append:"C" %}
{% else %}
  {% assign currentsemester = "Fall" %}
  {% assign currentshortsemester = currentyear | append:"C" %}
{% endif %}

{% assign currentcourses = site.courses | where:"shortsemester", currentshortsemester | sort:"coursenumber" %}

{% if currentcourses.size > 0 %}

### {{ currentsemester }} {{ currentyear }}, current courses
  
  {% for course in currentcourses %}
  [{{ course.title }}]({% if course.siteurl %}{{ course.siteurl }}{% else %}{{ course.url }}{% endif %})
  {% if course.courseprefix %}{{ course.courseprefix }} {% else %} Math {% endif %} {{ course.coursenumber }}
  {% endfor %}
  
{% else %}
  
### {{currentsemester }} {{ currentyear }}, no courses
  
{% endif %}

{% if currentsemester == "Summer" %}

  {% assign nextcourses = site.courses | where:"shortsemester", nextshortsemester | sort:"coursenumber" %}
  
  {% if nextcourses.size > 0 %}
  
### Fall {{ currentyear }}, upcoming courses
  
  {% for course in nextcourses %}
  [{{ course.title }}]({% if course.siteurl %}{{ course.siteurl }}{% else %}{{ course.url }}{% endif %})
  {% if course.courseprefix %}{{ course.courseprefix }} {% else %} Math {% endif %} {{ course.coursenumber }}
  {% endfor %}
  
  {% endif %}

{% endif %}



{% comment %}
I wonder if I can add upcoming courses here?
Or would that be too much info? They are listed on the Teaching page, maybe that's enough.
{% endcomment %}

### [Previous and upcoming courses](/teaching)




## [Research](/research)

My area of research is
[commutative algebra](https://en.wikipedia.org/wiki/Commutative_algebra)
and [algebraic geometry](https://en.wikipedia.org/wiki/Algebraic_geometry)
([MSC](https://mathscinet.ams.org/mathscinet/msc/msc2020.html) 13 and 14).

I study algebraic geometry with actual polynomials,
especially **Waring rank**.
{% comment %}
I am interested in a range of problems involving commutative algebra and
algebraic geometry, usually with a combinatorial or computational flavor,
such as:
computing rank (especially **Waring rank**), [**secant varieties**](https://en.wikipedia.org/wiki/Secant_variety),
and [Hilbert functions](https://en.wikipedia.org/wiki/Hilbert_series_and_Hilbert_polynomial);
arrangements (of [hyperplanes](https://en.wikipedia.org/wiki/Arrangement_of_hyperplanes),
[lines](https://en.wikipedia.org/wiki/Arrangement_of_lines), points, etc);
[**multiplier ideals**](https://en.wikipedia.org/wiki/Multiplier_ideal) (computation, applications to commutative algebra);
and computer experimentation in mathematics.
{% endcomment %}

### Recent publications

{% assign pubs_sorted = site.publications | sort:"pubdate" | reverse %}
{% for pub in pubs_sorted limit: 6 %}

[{{ pub.title }}]({% if pub.siteurl %}{{ pub.siteurl }}{% else %}{{ pub.url }}{% endif -%})
{%- if pub.journal %}, {{ pub.journal }}{% endif %}, {{ pub.pubdate | floor }}
{{ pub.excerpt | remove: '<p>' | remove: '</p>' | strip }}
{% comment %}
<span class="post-meta"><span class="category_name">{{ pub.categories }}</span> posted on {{ pub.date | date: "%b %-d, %Y" }}</span>
{% endcomment %}

{% endfor %}




## [Advising](/advising)

Graduate and undergraduate students I have advised.


## [TATERS](https://sites.google.com/boisestate.edu/taters/)

I am a co-organizer of the [Topics in Algebra, Topology, Etc., Research Seminar: TATERS](https://sites.google.com/boisestate.edu/taters/).  
See also the [Set Theory Seminar](https://www.boisestate.edu/math/research/seminars/settheory/),
the [Mathematics Department Colloquium](https://www.boisestate.edu/math/research/colloquium/),
and the [Computing Colloquium](https://www.boisestate.edu/computing/colloquium/).


## [Boise Math Circles](https://www.boisestate.edu/math/circles/)

A math community for teachers and for secondary students


## [Events](/events)

Research workshops and conference special sessions that I have organized, co-organized,
or been involved in.


<br style="margin-bottom:1ex" />


[Weekly schedule](/weekly) | [Travel](/travel)



[Boise State Topology & Algebra Research](https://www.boisestate.edu/math/research/topology/) in the BSU math department

[BSU Academic Calendars](https://www.boisestate.edu/registrar/boise-state-academic-calendars/)

[BSU Math Master's Theses](https://scholarworks.boisestate.edu/math_gradproj/) |
[BSU Math Senior Theses](https://scholarworks.boisestate.edu/math_undergraduate_theses/) |
[BSU Math Senior Showcase](https://scholarworks.boisestate.edu/math_senior_showcase/)

[About me](/about)

[Links](/links)
