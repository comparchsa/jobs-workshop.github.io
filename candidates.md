---
title: Job Candidates
subtitle: Students and postdocs presenting themselves to employers at MICRO-59.
description: >-
  How to register as a JOBS 2026 job candidate, and the list of candidates
  attending this edition. Open to PhD students and postdocs in computer
  architecture who are on the market.
permalink: /candidates/
---

{% assign w = site.data.workshop %}
{% assign candidates = site.data.candidates %}
{% assign candidate_count = candidates | size %}

Registration is completely open. All registered attendees who are on the job market and wish to be listed will be shown here.

This list is open to PhD students and postdocs in computer architecture and
adjacent areas who are on the market this cycle.

{% include cta.html %}

## Job Candidates

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
  <h3>Not Published Yet</h3>
  <p>Registered candidates will be listed here.</p>
</div>
{% endif %}

## Attending the Workshop

The workshop is open to all {{ w.conference_name }} registrants and is included
in workshops and tutorials registration at MICRO. Please indicate your interest in attending the JOBS workshop on the Whova registration form. See [Venue]({{ '/venue/' | relative_url }}) for the room,
travel, and registration details.

## Corrections and Removals

To correct or remove an entry, contact the organizers at
{% include contact.html %}. Removal requests are honoured without questions.

## For Employers

The candidate list stays online after the conference, and the CV links go
directly to the candidates. If you are recruiting and attending MICRO-59, the
Coffee Break at 10:00 is the point in the
[schedule]({{ '/schedule/' | relative_url }}) set aside for meeting candidates.
