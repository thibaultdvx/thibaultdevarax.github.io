---
layout: page
title: Posts
permalink: /posts/
---

{% for category in site.categories %}
  {% assign category_name = category[0] %}
  <li>
    <a href="/category/{{ category_name | slugify }}/">{{ category_name | replace: "-", " " }}</a>
  </li>
{% endfor %}

{%- for post in site.posts -%}
  {%- capture current_year -%}{{ post.date | date: "%Y" }}{%- endcapture -%}
  {%- unless current_year == previous_year -%}
    <h2>{{ current_year }}</h2>
    {%- assign previous_year = current_year -%}
  {%- endunless -%}
  <article class="post-item">
    <h3 class="post-item-title">
      <a href="{{ post.url }}">{{ post.title | escape }}</a>
    </h3> 
  </article>
{%- endfor -%}