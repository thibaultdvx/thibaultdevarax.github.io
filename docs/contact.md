---
layout: default
title: Contact
---
<!-- {% assign grouped_by_letter = "" %}

{% for labo in site.labos %}
    {% assign first_letter = labo.name | slice: 0,1 | upcase %}
    
    {% capture existing_group %}{{ grouped_by_letter | split: first_letter | last }}{% endcapture %}
    
    {% if existing_group contains ":" %}
        {% assign updated_group = existing_group | append: "," | append: labo.name %}
        {% assign grouped_by_letter = grouped_by_letter | replace: existing_group, updated_group %}
    {% else %}
        {% assign grouped_by_letter = grouped_by_letter | append: first_letter | append: ":" | append: labo.name | append: ";" %}
    {% endif %}
{% endfor %}

{% assign groups = grouped_by_letter | split: ";" %}

{% for group in groups %}
    {% assign parts = group | split: ":" %}
    {% assign letter = parts[0] %}
    {% assign names = parts[1] | split: "," %}
    
    <h2>{{ letter }}</h2>
    <ul>
        {% for name in names %}
            <li>{{ name }}</li>
        {% endfor %}
    </ul>
{% endfor %} -->
{% assign sorted_labos = site.labos | sort: "name" %}
{% assign current_letter = "" %}

{% for labo in sorted_labos %}
    {% assign first_letter = labo.name | slice: 0,1 | upcase %}

    {% if first_letter != current_letter %}
        {% unless forloop.first %}</ul>{% endunless %}
        <h2>{{ first_letter }}</h2>
        <ul>
        {% assign current_letter = first_letter %}
    {% endif %}

    <li>{{ labo.name }}</li>

    {% if forloop.last %}</ul>{% endif %}
{% endfor %}