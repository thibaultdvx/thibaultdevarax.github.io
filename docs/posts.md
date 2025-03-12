---
layout: page
title: Posts
permalink: /posts/
---

{% for post in page.posts %}
    {% capture year_of_current_post %}{{ post.date | date: "%Y" }}{% endcapture %}
    {% capture year_of_previous_post_in_set %}{{ page.posts[forloop.index].date | date: "%Y" }}{% endcapture %}

        {% if forloop.first %}
        <h2>{{ year_of_current_post }}</h2>
        <ul>
        {% endif %}

                <li><a href="{{ post.url }}">{{ post.title }}</a></li>

        {% if forloop.last %}
        </ul>
        {% else %}
        {% if year_of_current_post != year_of_previous_post_in_set %}
        </ul>

        <h2>{{ year_of_previous_post_in_set }}</h2>
        <ul>
        {% endif %}
        {% endif %}

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