
# Software

{% for post in site.software %}
1. [{{ post.title }}]({% if post.siteurl %}{{ post.siteurl }}{% else %}{{ post.url }}{% endif %})  
    {{ post.excerpt | remove: '<p>' | remove: '</p>' }}
{% endfor %}
