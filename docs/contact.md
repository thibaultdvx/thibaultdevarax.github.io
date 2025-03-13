---
layout: about
title: Contact
---
<ul>
{% for item in site.labos %}
    <li><a href="{{ item.url }}">{{ item.name }}</a></li>
{% endfor %}
</ul>