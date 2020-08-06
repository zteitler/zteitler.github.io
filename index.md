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

# Recent activity

{% for post in site.posts limit: 6 %}

[{{ post.title }}]({% if post.siteurl %}{{ post.siteurl }}{% else %}{{ post.url }}{% endif %})  
{{ post.excerpt | remove: '<p>' | remove: '</p>' | strip }}  
<span class="post-meta"><span class="category_name">{{ post.categories }}</span> posted on {{ post.date | date: "%b %-d, %Y" }}</span>

{% endfor %}

**subscribe** via [rss]({{ site.baseurl }}/feed.xml)

# Links

[Boise State topology & algebra research](https://www.boisestate.edu/math/research/topology/) in the BSU math department  
[Boise math circles](https://www.boisestate.edu/math/circles/) math for secondary students  
