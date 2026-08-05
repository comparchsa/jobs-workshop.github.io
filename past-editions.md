---
title: Past Editions
subtitle: Previous editions of the workshop.
permalink: /past-editions/
---

{% assign past_count = site.data.past_editions | size %}

{% if past_count > 0 %}
{%- for e in site.data.past_editions %}
<article class="edition">
  <h2>{{ site.data.workshop.name }} {{ e.year }}</h2>
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
  {%- if e.url and e.url != "" %}
  <p class="mb-0"><a href="{{ e.url }}">{{ e.year }} workshop site</a></p>
  {%- endif %}
</article>
{%- endfor %}
{% else %}
<div class="empty-state">
  <h3>This is the first edition</h3>
  <p>Previous editions will be listed here as the workshop recurs.</p>
</div>
{% endif %}
