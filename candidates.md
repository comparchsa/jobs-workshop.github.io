---
title: Job Candidates
subtitle: Students and postdocs presenting themselves to employers at MICRO-59.
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
<div class="table-scroll">
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

## Corrections and removals

To correct or remove an entry, email
[{{ w.contact_email }}](mailto:{{ w.contact_email }}). Removal requests are
honoured without questions.

## For employers

The candidate list stays online after the conference, and the CV links go
directly to the candidates. If you are recruiting and attending MICRO-59, the
coffee break at 10:00 is the point in the
[schedule]({{ '/schedule/' | relative_url }}) set aside for meeting candidates.
