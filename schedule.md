---
title: Schedule
description: >-
  The JOBS 2026 program — two panels, a keynote, a mini-workshop on crafting your platform, and a networking
  Coffee Break. 8:00 AM to 12:00 PM on Sunday 1 November 2026.
permalink: /schedule/
---

{% assign w = site.data.workshop %}

<p class="text-muted">
  <time datetime="{{ w.date_iso }}">{{ w.date_human }}</time>
  &middot; {{ w.time_human }} ({{ w.timezone }})<br>
  {{ w.venue_name }}, {{ w.city }} &middot; Room {{ w.venue_room }}
</p>

{% if w.schedule_note and w.schedule_note != "" %}
<div class="note">
  <p>{{ w.schedule_note }}</p>
</div>
{% endif %}

<ol class="timeline">
{%- for slot in site.data.schedule %}
  <li class="slot slot--{{ slot.kind | default: 'session' }}">
    <div class="slot-time">
      {%- if slot.start and slot.start != "" -%}
      <time datetime="{{ w.date_iso }}T{{ slot.start }}">{{ slot.start }}</time>
      {%- if slot.end and slot.end != "" %}<span class="slot-end"><span class="visually-hidden"> to </span><time datetime="{{ w.date_iso }}T{{ slot.end }}">{{ slot.end }}</time></span>{% endif %}
      {%- endif -%}
    </div>
    <div class="slot-body">
      {%- if slot.kind and slot.kind != "" and slot.tag != "none" %}
      <span class="chip chip--{{ slot.kind }}">{{ slot.tag | default: slot.kind }}</span>
      {%- endif %}
      <h2>{{ slot.title }}</h2>
      {%- if slot.description and slot.description != "" %}
      <p>{{ slot.description }}</p>
      {%- endif %}
      {%- assign people_count = slot.people | size -%}
      {%- if people_count > 0 %}
      <ul class="people">
        {%- for person in slot.people %}
        <li>
          {% include avatar.html person=person %}
          <span class="person-lines">
            {%- if person.url and person.url != "" -%}
            <a class="person-name" href="{{ person.url }}">{{ person.name }}</a>
            {%- else -%}
            <span class="person-name">{{ person.name }}</span>
            {%- endif -%}
            {%- if person.role %}<span class="person-role">{{ person.role }}</span>{% endif %}
            {%- if person.affiliation %}<span class="person-affil">{{ person.affiliation }}</span>{% endif %}
          </span>
        </li>
        {%- endfor %}
      </ul>
      {%- endif %}
    </div>
  </li>
{%- endfor %}
</ol>
