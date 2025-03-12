---
layout: page
title: Posts
---
{% include search-lunr.html %}

{%- for category in site.categories -%}
  <h3>{{ category }}</h3>
  {%- for post in site.categories[category] -%}
    <div class="tag-post-title">
        <h4><a href="{{ site.baseurl }}{{ post.url }}">{{post.title}}</a></h4>
    </div>
  {%- endfor -%}
{%- endfor -%}

{%- for post in site.posts -%}
  {%- capture current_year -%}{{ post.date | date: "%Y" }}{%- endcapture -%}
  {%- unless current_year == previous_year -%}
    <h2>{{ current_year }}</h2>
    {%- assign previous_year = current_year -%}
  {%- endunless -%}
  <div class="tag-post-title">
      <h4><a href="{{ site.baseurl }}{{ post.url }}">{{post.title}}</a></h4>
  </div>
{%- endfor -%}