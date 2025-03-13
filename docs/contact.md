---
layout: about
title: Contact
---
{% assign sortedLabos = site.labos | sort: 'name' %}
<ul>
{% for item in sortedLabos %}
    <li><a href="{{ item.url }}">{{ item.name }}</a></li>
{% endfor %}
</ul>