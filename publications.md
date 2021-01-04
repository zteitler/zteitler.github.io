
# Publications

{% assign thisyear = "now" | date: "%Y" | plus: 0 %}
{% assign prevdisplaydate = "X" %}
{% assign pubsbydate = site.publications | sort: "pubdate" | reverse %}
{% assign numpubs = pubsbydate | size %}

{% for post in pubsbydate %}

{% assign thisyearplusone = thisyear | plus: 1 %}
{% if post.pubdate < thisyearplusone %}
  {% assign displaydate = post.pubdate | floor %}
{% else %}
  {% assign displaydate = "∞" %}
{% endif %}

{% if displaydate != prevdisplaydate %} *{{ displaydate }}* {% assign prevdisplaydate = displaydate %} {% else %} &nbsp; {% endif %}

: [{{ numpubs }}] [{{ post.title }}]({% if post.siteurl %}{{ post.siteurl }}{% else %}{{ post.url }}{% endif %})  
{{ post.excerpt | remove: '<p>' | remove: '</p>' }}

{% assign numpubs = numpubs | minus:1 %}
{% endfor %}
