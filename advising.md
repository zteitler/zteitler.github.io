---
title: Advising
layout: page
---


{% capture newLine %}
{% endcapture %}

{% assign advisingtypes = site.data.advising | sort: "order" %}


{% for type in advisingtypes %}

{% assign students = type.students | sort: "year" | reverse %}

## {{type.header}}

{% if type.intro %}{{ type.intro | markdownify }}{% endif %}

{% for student in students %}
1.  **{{ student.name -}}**
    <br />
    {{ student.degree -}}
    {% if student.year %}, {{student.year | floor}}{% endif %}
    {% if student.expected %} (expected){% endif -%}
    
    {%- if student.advisor %}<br /> Advisor: {{student.advisor}}{% endif -%}
    
    {%- if student.coadvisor %}<br /> Co-Advisor: {{student.coadvisor }} {% endif -%}
    
    {%- if student.thesistitle -%}
    <br />
    {% if student.thesistype %} {{student.thesistype}}: {% else %} Thesis: {% endif %}
    {% if student.thesisurl %}[*{{ student.thesistitle }}*]({{student.thesisurl}}){% else %}*{{student.thesistitle}}*{% endif %}
    {%- endif -%}
    
    {%- if student.postdegree -%}
    <br /> After graduation: {{ student.postdegree }}
    {%- endif %}
    
{% endfor %}

{% endfor %}
