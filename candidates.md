---
title: Job Candidates
subtitle: Students and postdocs presenting themselves to employers at MICRO-59.
description: >-
  How to apply as a JOBS 2026 job candidate, and the list of candidates
  selected for this edition. Open to PhD students and postdocs in computer
  architecture who are on the market.
permalink: /candidates/
---

{% assign w = site.data.workshop %}
{% assign candidates = site.data.candidates %}
{% assign candidate_count = candidates | size %}

Job candidates apply through the workshop's submission site. The organizers
review the applications and select the candidates who will be listed here and
introduced during the workshop.

Applications are open to PhD students and postdocs in computer architecture and
adjacent areas who are on the market this cycle. Attending the workshop is not
a requirement for applying, and applying is not a requirement for attending.

{% include cta.html %}

## Selected candidates

{% if candidate_count > 0 %}
{%- comment -%}
tabindex="0" is what makes this scrollable box reachable with the keyboard —
without it a keyboard-only visitor cannot scroll sideways to the CV column on
a narrow screen. role="region" + aria-label give it a name once it is
focusable, so it is announced rather than landed on silently.
{%- endcomment -%}
<div class="table-scroll" tabindex="0" role="region"
     aria-label="Selected job candidates, scrollable table">
  <table>
    <caption class="visually-hidden">Selected job candidates for {{ w.name }} {{ w.edition }}</caption>
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
  <h3>Not published yet</h3>
  <p>Selected candidates will be listed here after the application deadline.</p>
</div>
{% endif %}

## Attending the workshop

The workshop is open to all {{ w.conference_name }} registrants and is included
in conference registration. There is no separate workshop fee and no RSVP —
turn up on the day. See [Venue]({{ '/venue/' | relative_url }}) for the room,
travel, and registration details.

## Corrections and removals

To correct or remove an entry, email
[{{ w.contact_email }}](mailto:{{ w.contact_email }}). Removal requests are
honoured without questions.

## For employers

The candidate list stays online after the conference, and the CV links go
directly to the candidates. If you are recruiting and attending MICRO-59, the
coffee break at 10:00 is the point in the
[schedule]({{ '/schedule/' | relative_url }}) set aside for meeting candidates.
