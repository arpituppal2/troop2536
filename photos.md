---
layout: default
title: Photos
description: Photo galleries from Troop 2536 adventures and events.
---

<p class="page-lede">
  A few favorite shots from recent adventures. (All scout photos are published
  with parental permission, first names only.)
</p>

{% comment %}
  Galleries are automatic: each folder inside images/ becomes a gallery
  section below. Sort by reverse name so newer galleries (named with dates,
  like 2026-09-campout) float to the top. No page edit needed to add one.
{% endcomment %}

{% assign gallery_dirs = site.static_files | where_exp: "f", "f.path contains '/images/'" | map: "path" %}
{% assign gallery_names = "" | split: "" %}
{% for p in gallery_dirs %}
  {% assign parts = p | split: "/" %}
  {% assign gname = parts[2] %}
  {% unless gallery_names contains gname %}
    {% assign gallery_names = gallery_names | push: gname %}
  {% endunless %}
{% endfor %}
{% assign gallery_names = gallery_names | sort | reverse %}
{% assign any_gallery = false %}

{% for gname in gallery_names %}
  {% assign gdir = '/images/' | append: gname | append: '/' %}
  {% assign files = site.static_files
       | where_exp: "f", "f.path contains gdir"
       | where_exp: "f", "f.extname == '.jpg' or f.extname == '.jpeg' or f.extname == '.png' or f.extname == '.webp' or f.extname == '.gif' or f.extname == '.avif'" %}
  {% if files.size > 0 %}
    {% assign any_gallery = true %}
    <div class="gallery-band">
      <h2>{{ gname | replace_first: '-', ' · ' | replace: '-', ' ' }}</h2>
      <div class="gallery">
        {% for f in files %}
          <figure>
            <img src="{{ f.path | relative_url }}" alt="Troop 2536 photo from {{ gname | replace: '-', ' ' }}" loading="lazy">
          </figure>
        {% endfor %}
      </div>
    </div>
  {% endif %}
{% endfor %}

{% unless any_gallery %}
  <p>Galleries will appear here after the first photos are added — they're coming soon!</p>
{% endunless %}
