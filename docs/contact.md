---
layout: about
title: Contact
---
{% assign grouped_labos = site.labos | group_by: "name" %}

{% assign sorted_labos = grouped_labos | sort: "name" %}

{% assign grouped_by_letter = {} %}

{% for labo in sorted_labos %}
    {% assign first_letter = labo.name | slice: 0,1 | upcase %}
    {% unless grouped_by_letter[first_letter] %}
        {% assign grouped_by_letter = grouped_by_letter | merge: { first_letter => "" } %}
    {% endunless %}
    {% assign grouped_by_letter = grouped_by_letter | merge: { first_letter => grouped_by_letter[first_letter] | append: labo } %}
{% endfor %}

{% for letter in grouped_by_letter %}
    <h2>{{ letter[0] }}</h2>
    <ul>
        {% for labo in letter[1] %}
            <li>{{ labo.name }}</li>
        {% endfor %}
    </ul>
{% endfor %}
