---
title: Attend
subtitle: JOBS workshop is co-located with MICRO-59 conference.
description: >-
  JOBS 2026 is held at the InterContinental Athenaeum Athens, inside the
  MICRO-59 venue. Registration, venue details, and accessibility.
permalink: /venue/
header_cta: true
---

{% assign w = site.data.workshop %}

<ul class="venue-facts">
  <li><span class="fact-label">Date</span><time datetime="{{ w.date_iso }}">{{ w.date_human }}</time></li>
  <li><span class="fact-label">Time</span>{{ w.time_human }} ({{ w.timezone }})</li>
  <li><span class="fact-label">Venue</span>{{ w.venue_name }}</li>
  <li><span class="fact-label">Room</span>{{ w.venue_room }}</li>
</ul>


## Registration and Attending

The workshop is open to all {{ w.conference_name }} registrants. Please indicate your interest in attending the JOBS workshop on the Whova registration form. If you intend to participate as a JOBS candidate, please also fill out the [JOBS candidate registration form]({{ w.submission.url }}).

## Volunteering for the Mini-Workshop

We are looking for senior architects in industry and academia to provide feedback on CVs, elevator pitches, and teaching/research statements during our new Mini-Workshop session. 

If you are willing to offer your time and expertise, please reach out to the organizers at
{% include contact.html %}.

## Venue

Room information will be provided before the conference (see
[MICRO-59 workshops page]({{ w.conference_workshops_url }})).

<p><a href="{{ '/jobs-workshop-2026.ics' | relative_url }}" download>Add JOBS workshop to your calendar</a></p>

## Accessibility Requirements

Contact the organizers at {% include contact.html %} with your requirements as early as possible. We will work with the conference organizers to try to accommodate your requests.
