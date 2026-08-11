---
layout: default
title: Photos
heading: Photos
permalink: /photos.html
intro: "A collection of albums from over the years. More to be added as they're unearthed from various hard drives and shoeboxes."
---
<h1 class="page-heading">{{ page.heading }}</h1>
<p class="page-intro">{{ page.intro }}</p>

<div class="album-grid">
{% assign albums = site.albums | sort: 'order' %}
{% for a in albums %}
  <a href="{{ a.link | relative_url }}" class="album-card">
    <div class="album-thumb">
      <img src="{{ a.thumb | relative_url }}" alt="{{ a.title }}" loading="lazy">
    </div>
    <div class="album-info">
      <h3 class="album-title">{{ a.title }}</h3>
      <p class="album-meta">{{ a.meta }}</p>
    </div>
  </a>
{% endfor %}
</div>
