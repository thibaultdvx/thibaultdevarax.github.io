---
layout: about
title: Contact
---
<ul>
{% for item in site[labos] %}
    <li><a href="{{ item.url }}">{{ item.title }}</a></li>
{% endfor %}
</ul>