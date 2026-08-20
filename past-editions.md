---
title: Past Editions
subtitle: Previous editions of the JOBS workshop.
description: >-
  Earlier editions of the JOBS workshop, starting with JOBS 2024 at MICRO-57
  in Austin, Texas.
permalink: /past-editions/
---

{% assign past_count = site.data.past_editions | size %}

{% if past_count > 0 %}
{%- for e in site.data.past_editions %}
<article class="edition">
  <h2>
    {% if e.url and e.url != "" %}
      <a href="{{ e.url }}">{{ site.data.workshop.name }} {{ e.year }}</a>
    {% else %}
      {{ site.data.workshop.name }} {{ e.year }}
    {% endif %}
  </h2>
  <div class="edition-meta">
    <span>{{ e.conference }}</span>
    <span>{{ e.date }}</span>
    <span>{{ e.location }}</span>
  </div>
  {%- if e.summary %}
  <p>{{ e.summary }}</p>
  {%- endif %}
  {%- assign highlight_count = e.highlights | size -%}
  {%- if highlight_count > 0 %}
  <ul>
    {%- for h in e.highlights %}
    <li>{{ h }}</li>
    {%- endfor %}
  </ul>
  {%- endif %}

</article>
{%- endfor %}
{% else %}
<div class="empty-state">
  <h3>No past editions yet</h3>
  <p>Previous editions will be listed here as the workshop recurs.</p>
</div>
{% endif %}
