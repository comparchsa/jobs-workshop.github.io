---
title: Schedule
subtitle: Talks, panels, and a Coffee Break, in the MICRO-59 morning workshop slot.
description: >-
  The JOBS 2026 programme — two panels on research careers and the mechanics
  of the job search, a talk on how hiring decisions get made, and a networking
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
      <span class="chip chip--{{ slot.kind | default: 'session' }}">{{ slot.kind | default: 'session' }}</span>
      <h2>{{ slot.title }}</h2>
      {%- if slot.description %}
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
            {%- if person.affiliation %}<span class="person-affil">{{ person.affiliation }}</span>{% endif %}
            {%- if person.role %}<span class="person-role">{{ person.role }}</span>{% endif %}
          </span>
        </li>
        {%- endfor %}
      </ul>
      {%- endif %}
    </div>
  </li>
{%- endfor %}
</ol>

The workshop sits in the first of the two MICRO-59 workshop blocks on
November 1. Lunch follows at 12:00, and afternoon workshops start at 1:00 PM.
The full list of MICRO-59 workshops and tutorials is on the
[conference site]({{ w.conference_workshops_url }}).
