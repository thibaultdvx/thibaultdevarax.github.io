---
layout: page
title: Posts
---
{% include search-lunr.html %}

{%- for category in site.categories -%}
  <h3>{{ category }}</h3>
  {%- for post in site.categories[category] -%}
    <article class="post-item">
      <h4 class="post-item-title">
        <a href="{{ post.url }}">{{ post.title | escape }}</a>
      </h4> 
    </article>
  {%- endfor -%}
{%- endfor -%}

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