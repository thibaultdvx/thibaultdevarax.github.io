---
layout: about
title: Contact
---
{% assign grouped_by_letter = {} %}

{% for labo in site.labos %}
    {% assign first_letter = labo.name | slice: 0,1 | upcase %}
    
    {% if grouped_by_letter[first_letter] %}
        {% assign grouped_by_letter = grouped_by_letter | merge: { first_letter => grouped_by_letter[first_letter] | push: labo } %}
    {% else %}
        {% assign grouped_by_letter = grouped_by_letter | merge: { first_letter => [labo] } %}
    {% endif %}
{% endfor %}

{% for letter in grouped_by_letter %}
    <h2>{{ letter[0] }}</h2>
    <ul>
        {% for labo in letter[1] %}
            <li>{{ labo.name }}</li>
        {% endfor %}
    </ul>
{% endfor %}
