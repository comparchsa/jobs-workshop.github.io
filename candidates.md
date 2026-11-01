---
title: JOBS Candidates
subtitle: 
description: >-
  How to register as a JOBS 2026 job candidate, and the list of candidates
  attending this edition. Open to PhD students and postdocs in computer
  architecture who are on the market.
permalink: /candidates/
header_cta: true
---

{% assign w = site.data.workshop %}
{% assign candidates = site.data.candidates %}
{% assign candidate_count = candidates | size %}

To advertise yourself on this page, please register as a JOBS candidate above. The candidate list will remain online after the conference. 

If you are recruiting and attending MICRO-59, please come meet candidates during the
Coffee Break at 10:00 am, and the mini-workshop session at 11:30 am (see [schedule]({{ '/schedule/' | relative_url }})). 

Candidates are listed alphabetically by last name; the order is not a ranking.

To update or remove an entry, please contact the organizers at
{% include contact.html %}.

{% if candidate_count > 0 %}
{%- comment -%}
tabindex="0" is what makes this scrollable box reachable with the keyboard —
without it a keyboard-only visitor cannot scroll sideways to the CV column on
a narrow screen. role="region" + aria-label give it a name once it is
focusable, so it is announced rather than landed on silently.
{%- endcomment -%}
<div class="table-scroll" tabindex="0" role="region"
     aria-label="Job candidates, scrollable table">
  <table class="candidates">
    <caption class="visually-hidden">Job candidates for {{ w.name }} {{ w.edition }}</caption>
    <thead>
      <tr>
        <th scope="col">Candidate</th>
        <th scope="col">Affiliation</th>
        <th scope="col">Research areas</th>
        <th scope="col">Looking for</th>
        <th scope="col">Graduation</th>
        <th scope="col">Materials</th>
      </tr>
    </thead>
    <tbody>
    {%- for c in candidates %}
      <tr>
        <td>
          {%- if c.website and c.website != "" -%}
          <a class="candidate-name" href="{{ c.website }}">{{ c.name }}</a>
          {%- else -%}
          <span class="candidate-name">{{ c.name }}</span>
          {%- endif -%}
          {%- if c.role and c.role != "" %}<span class="candidate-role">{{ c.role }}</span>{% endif %}
        </td>
        <td>{{ c.affiliation }}</td>
        <td>
          {%- if c.areas and c.areas.size > 0 -%}
          <ul class="tag-list">
            {%- for a in c.areas %}<li class="area area--{{ a | slugify }}">{{ a }}</li>{% endfor %}
          </ul>
          {%- else -%}&mdash;{%- endif -%}
        </td>
        <td>
          {%- if c.market and c.market != "" %}<span class="candidate-market">On the market: {{ c.market }}</span>{% endif -%}
          {%- if c.seeking and c.seeking.size > 0 -%}
          <ul class="tag-list">
            {%- for s in c.seeking %}<li class="pill">{{ s }}</li>{% endfor %}
          </ul>
          {%- endif -%}
        </td>
        <td class="nowrap">{% if c.grad and c.grad != "" %}{{ c.grad }}{% else %}&mdash;{% endif %}</td>
        <td>
          {%- if c.cv and c.cv != "" -%}
          <ul class="materials">
            <li><a href="{{ c.cv }}">CV<span class="visually-hidden"> for {{ c.name }}</span></a></li>
            {%- if c.research_statement and c.research_statement != "" %}
            <li><a href="{{ c.research_statement }}">Research<span class="visually-hidden"> statement for {{ c.name }}</span></a></li>
            {%- endif %}
            {%- if c.teaching_statement and c.teaching_statement != "" %}
            <li><a href="{{ c.teaching_statement }}">Teaching<span class="visually-hidden"> statement for {{ c.name }}</span></a></li>
            {%- endif %}
          </ul>
          {%- else -%}&mdash;{%- endif -%}
        </td>
      </tr>
    {%- endfor %}
    </tbody>
  </table>
</div>
{% else %}
<div class="empty-state">
  <p>Registered candidates will be listed here.</p>
</div>
{% endif %}