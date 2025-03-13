---
layout: about
title: Contact
---
{% assign grouped_by_letter = "" %}

{% for labo in site.labos %}
    {% assign first_letter = labo.name | slice: 0,1 | upcase %}
    
    {% capture existing_group %}{{ grouped_by_letter | split: first_letter | last }}{% endcapture %}
    
    {% if existing_group == "" %}
        {% assign grouped_by_letter = grouped_by_letter | append: first_letter | append: ":" | append: labo.name | append: ";" %}
    {% else %}
        {% assign grouped_by_letter = grouped_by_letter | replace: first_letter | append: ":" | append: existing_group | append: "," | append: labo.name | append: ";" %}
    {% endif %}
{% endfor %}
