---
layout: default
title: Whisky
heading: "Ken's Whiskies"
permalink: /whisky.html
intro: "A personal selection. Heavily weighted towards Islay, which says everything you need to know."
extra_style: |
  .whisky-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 1.5rem; margin-top: 1.5rem; }
  .whisky-card { background: #fff; border: 1px solid var(--border); border-radius: 6px; overflow: hidden; transition: box-shadow 0.2s, transform 0.2s; }
  .whisky-card:hover { box-shadow: 0 4px 20px rgba(61, 43, 74, 0.12); transform: translateY(-2px); }
  .whisky-header { background: var(--heather); padding: 1.25rem 1.5rem; position: relative; }
  .whisky-region { font-family: var(--font-ui); font-size: 0.7rem; letter-spacing: 0.15em; text-transform: uppercase; color: var(--gold); margin-bottom: 0.3rem; }
  .whisky-name { font-family: var(--font-display); font-size: 1.3rem; font-weight: 600; color: var(--oatmeal); line-height: 1.2; }
  .whisky-age { font-family: var(--font-ui); font-size: 0.75rem; color: var(--oatmeal); opacity: 0.6; margin-top: 0.25rem; }
  .whisky-body { padding: 1.25rem 1.5rem; }
  .tasting-row { margin-bottom: 0.75rem; }
  .tasting-label { font-family: var(--font-ui); font-size: 0.65rem; letter-spacing: 0.12em; text-transform: uppercase; color: var(--gold); margin-bottom: 0.15rem; }
  .tasting-note { font-size: 0.88rem; color: #444; line-height: 1.55; font-family: var(--font-body); font-style: italic; }
  .whisky-bottle-placeholder { width: 70px; height: 110px; background: rgba(255,255,255,0.1); border: 2px dashed rgba(201, 169, 110, 0.4); border-radius: 6px; display: flex; align-items: center; justify-content: center; margin-top: 0.85rem; transition: background 0.2s; overflow: hidden; }
  .whisky-bottle-placeholder:hover { background: rgba(255,255,255,0.15); }
  .whisky-bottle-placeholder span { font-size: 1.6rem; opacity: 0.5; }
  .whisky-bottle-placeholder img { width: 100%; height: 100%; object-fit: contain; }
  .whisky-peat { display: inline-flex; align-items: center; gap: 0.4rem; margin-top: 0.75rem; font-family: var(--font-ui); font-size: 0.7rem; letter-spacing: 0.05em; color: var(--slate); }
  .peat-dots { display: flex; gap: 3px; }
  .peat-dot { width: 8px; height: 8px; border-radius: 50%; background: var(--border); }
  .peat-dot.filled { background: var(--heather); }
---
<h1 class="page-heading">{{ page.heading }}</h1>
<p class="page-intro">{{ page.intro }}</p>

<div class="whisky-grid">
{% assign whiskies = site.whiskies | sort: 'order' %}
{% for w in whiskies %}
  <div class="whisky-card">
    <div class="whisky-header">
      <div class="whisky-region">{{ w.region }}</div>
      <div class="whisky-name">{{ w.name }}</div>
      <div class="whisky-age">{{ w.age }} · {{ w.abv }}</div>
      <div class="whisky-bottle-placeholder">
        {% if w.image and w.image != "" %}
        <img src="{{ w.image | relative_url }}" alt="{{ w.name }}">
        {% else %}
        <span>🥃</span>
        {% endif %}
      </div>
    </div>
    <div class="whisky-body">
      <div class="tasting-row">
        <div class="tasting-label">Nose</div>
        <div class="tasting-note">{{ w.nose }}</div>
      </div>
      <div class="tasting-row">
        <div class="tasting-label">Palate</div>
        <div class="tasting-note">{{ w.palate }}</div>
      </div>
      <div class="tasting-row">
        <div class="tasting-label">Finish</div>
        <div class="tasting-note">{{ w.finish }}</div>
      </div>
      <div class="whisky-peat">
        <span>Peat</span>
        <div class="peat-dots">
          {% for i in (1..5) %}
          <div class="peat-dot{% if i <= w.peat %} filled{% endif %}"></div>
          {% endfor %}
        </div>
      </div>
    </div>
  </div>
{% endfor %}
</div>
