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
  <table>
    <caption class="visually-hidden">Job candidates for {{ w.name }} {{ w.edition }}</caption>
    <thead>
      <tr>
        <th scope="col">Candidate</th>
        <th scope="col">Affiliation</th>
        <th scope="col">Looking for</th>
        <th scope="col">CV</th>
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
          {%- if c.research and c.research != "" %}<span class="candidate-research">{{ c.research }}</span>{% endif %}
        </td>
        <td>{{ c.affiliation }}</td>
        <td>{% if c.seeking and c.seeking != "" %}<span class="pill">{{ c.seeking }}</span>{% else %}&mdash;{% endif %}</td>
        <td>{% if c.cv and c.cv != "" %}<a href="{{ c.cv }}">CV<span class="visually-hidden"> for {{ c.name }}</span></a>{% else %}&mdash;{% endif %}</td>
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