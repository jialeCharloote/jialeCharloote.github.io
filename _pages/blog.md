---
layout: default
permalink: /blog/
title: Blog
nav: true
nav_order: 2
pagination:
  enabled: true
  collection: posts
  permalink: /page/:num/
  per_page: 5
  sort_field: date
  sort_reverse: true
  trail:
    before: 1
    after: 3
---

{% assign blog_name_size = site.blog_name | size %}
{% assign blog_description_size = site.blog_description | size %}

{% if blog_name_size > 0 or blog_description_size > 0 %}
  <p class="lead">{{ site.blog_name }}</p>
  <p>{{ site.blog_description }}</p>
{% endif %}

{% if site.display_tags and site.display_tags.size > 0 or site.display_categories and site.display_categories.size > 0 %}
  <p class="lead">
  {% for tag in site.display_tags %}
    <a href="{{ tag | slugify | prepend: '/blog/tag/' | relative_url }}">{{ tag }}</a>
    {% unless forloop.last %} &bull; {% endunless %}
  {% endfor %}
  {% if site.display_categories.size > 0 and site.display_tags.size > 0 %} &bull; {% endif %}
  {% for category in site.display_categories %}
    <a href="{{ category | slugify | prepend: '/blog/category/' | relative_url }}">{{ category }}</a>
    {% unless forloop.last %} &bull; {% endunless %}
  {% endfor %}
  </p>
{% endif %}

{% assign featured_posts = site.posts | where: "featured", "true" %}
{% if featured_posts.size > 0 %}
  <h2 class="mb-4">Featured</h2>
  <div class="row row-cols-1 row-cols-md-2">
  {% for post in featured_posts %}
    {% assign read_time = post.content | number_of_words | divided_by: 180 | plus: 1 %}
    {% if post.external_source != blank %}
      {% assign read_time = post.feed_content | strip_html | number_of_words | divided_by: 180 | plus: 1 %}
    {% endif %}
    <div class="col mb-4">
      <div class="card h-100">
        {% if post.thumbnail %}
          <img src="{{ post.thumbnail | relative_url }}" class="card-img-top" alt="">
        {% endif %}
        <div class="card-body">
          <h5 class="card-title">
            {% if post.redirect == blank %}
              <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
            {% elsif post.redirect contains '://' %}
              <a href="{{ post.redirect }}" target="_blank" rel="noopener">{{ post.title }} <i class="fas fa-external-link-alt"></i></a>
            {% else %}
              <a href="{{ post.redirect | relative_url }}">{{ post.title }}</a>
            {% endif %}
          </h5>
          <p class="card-text">{{ post.description }}</p>
          <p class="text-muted small">{{ read_time }} min read &middot; {{ post.date | date: "%Y" }}</p>
        </div>
      </div>
    </div>
  {% endfor %}
  </div>
  <hr class="my-5">
{% endif %}

{% if page.pagination.enabled %}
  {% assign postlist = paginator.posts %}
{% else %}
  {% assign postlist = site.posts %}
{% endif %}

{% for post in postlist %}
  {% assign read_time = post.content | number_of_words | divided_by: 180 | plus: 1 %}
  {% if post.external_source != blank %}
    {% assign read_time = post.feed_content | strip_html | number_of_words | divided_by: 180 | plus: 1 %}
  {% endif %}
  <div class="card mb-4">
    {% if post.thumbnail %}
      <img src="{{ post.thumbnail | relative_url }}" class="card-img-top" alt="">
    {% endif %}
    <div class="card-body">
      <h5 class="card-title">
        {% if post.redirect == blank %}
          <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
        {% elsif post.redirect contains '://' %}
          <a href="{{ post.redirect }}" target="_blank" rel="noopener">{{ post.title }} <i class="fas fa-external-link-alt"></i></a>
        {% else %}
          <a href="{{ post.redirect | relative_url }}">{{ post.title }}</a>
        {% endif %}
      </h5>
      <p class="card-text">{{ post.description }}</p>
      <p class="text-muted small">
        {{ read_time }} min read &middot; {{ post.date | date: "%B %d, %Y" }}
        {% if post.external_source %} &middot; {{ post.external_source }}{% endif %}
        {% if post.tags.size > 0 %} &middot;
          {% for tag in post.tags %}
            <a href="{{ tag | slugify | prepend: '/blog/tag/' | relative_url }}">{{ tag }}</a>{% unless forloop.last %} {% endunless %}
          {% endfor %}
        {% endif %}
        {% if post.categories.size > 0 %} &middot;
          {% for category in post.categories %}
            <a href="{{ category | slugify | prepend: '/blog/category/' | relative_url }}">{{ category }}</a>{% unless forloop.last %} {% endunless %}
          {% endfor %}
        {% endif %}
      </p>
    </div>
  </div>
{% endfor %}

{% if page.pagination.enabled %}
{% include pagination.liquid %}
{% endif %}
