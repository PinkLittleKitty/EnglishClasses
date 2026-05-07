---
layout: default
title: Archivo
---

<h1>Archivo de Clases</h1>
<p>Todos los temas vistos, organizados cronológicamente.</p>

<div class="archive">
  {% for post in site.posts %}
    {% capture currentyear %}{{ post.date | date: "%Y" }}{% endcapture %}
    {% if currentyear != prevyear %}
      {% unless forloop.first %}</ul></div>{% endunless %}
      <div class="archive-group">
        <h2 class="archive-group-title">{{ currentyear }}</h2>
        <ul class="post-list-custom">
    {% endif %}
    
    <li>
      <a href="{{ post.url | relative_url }}" class="post-card" style="padding: 1rem; margin-bottom: 1rem;">
        <span class="post-card-meta">
          {{ post.date | date: "%B %d" }}
          {% if post.tags %}
            {% for tag in post.tags %}
              {% capture tag_class %}tag-{{ tag | slugify }}{% endcapture %}
              <span class="tag-badge {{ tag_class }}" style="margin-left: 8px;">{{ tag }}</span>
            {% endfor %}
          {% endif %}
        </span>
        <h3 class="post-card-title" style="font-size: 1.2rem; margin-bottom: 0;">{{ post.title | escape }}</h3>
      </a>
    </li>

    {% capture prevyear %}{{ currentyear }}{% endcapture %}
    {% if forloop.last %}</ul></div>{% endif %}
  {% endfor %}
</div>