---
layout: default
title: Inicio
---

<div class="home-hero">
  <h1>Inicio</h1>
</div>

<ul class="post-list-custom">
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url | relative_url }}" class="post-card">
        <span class="post-card-meta">
          {{ post.date | date: "%B %d, %Y" }}
          {% if post.tags %}
            {% for tag in post.tags %}
              {% capture tag_class %}tag-{{ tag | slugify }}{% endcapture %}
              <span class="tag-badge {{ tag_class }}" style="margin-left: 8px;">{{ tag }}</span>
            {% endfor %}
          {% endif %}
        </span>
        <h2 class="post-card-title">{{ post.title | escape }}</h2>
        <div class="post-card-excerpt">
          {% if post.excerpt %}
            {{ post.excerpt | strip_html | truncatewords: 30 }}
          {% else %}
            {{ post.content | strip_html | truncatewords: 30 }}
          {% endif %}
        </div>
      </a>
    </li>
  {% endfor %}
</ul>