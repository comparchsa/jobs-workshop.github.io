---
title: Venue
subtitle: The workshop is held inside the MICRO-59 conference venue.
permalink: /venue/
---

{% assign w = site.data.workshop %}

<ul class="venue-facts">
  <li><span class="fact-label">Date</span>{{ w.date_human }}</li>
  <li><span class="fact-label">Time</span>{{ w.time_human }} ({{ w.timezone }})</li>
  <li><span class="fact-label">Venue</span>{{ w.venue_name }}</li>
  <li><span class="fact-label">Room</span>{{ w.venue_room }}</li>
</ul>

{{ w.venue_address }} — see the
[{{ w.conference_name }} venue and hotel page]({{ w.venue_info_url }}).

The room is assigned by the {{ w.conference_name }} organizers and is usually
published shortly before the conference. It will appear above and on the
[MICRO-59 workshops page]({{ w.conference_workshops_url }}).

<iframe class="map-frame"
        src="{{ w.venue_map_embed }}"
        title="Map of Syngrou Avenue, Athens, showing the conference venue location"
        loading="lazy"
        referrerpolicy="no-referrer-when-downgrade"></iframe>

<p><a href="{{ w.venue_map_url }}">Open this location in a larger map</a></p>

## Getting there

The hotel is on Syngrou Avenue, the main road between central Athens and the
coast — roughly 15 minutes by taxi from Syntagma Square and about 45 minutes
from Athens International Airport (ATH).

- **From the airport:** metro Line 3 (blue) to Syntagma, then a taxi or bus down
  Syngrou. A direct taxi is simpler with luggage and has a fixed daytime flat
  rate into central Athens.
- **By tram:** the lines along Syngrou stop close to the hotel.
- **On foot:** the Acropolis Museum and Koukaki are a 15–20 minute walk north.

See the MICRO-59 [travel information]({{ w.conference_url }}attend/travelinfo.php)
and [getting around Athens]({{ w.conference_url }}attend/traveltips.php) pages
for more detail.

## Registration

The workshop is included with {{ w.conference_name }} registration; there is no
separate workshop fee. Rates and deadlines are on the
[MICRO-59 registration page]({{ w.conference_registration_url }}), and the
conference hotel block is on the
[venue and hotel page]({{ w.venue_info_url }}).

## Accessibility and dietary requirements

Email [{{ w.contact_email }}](mailto:{{ w.contact_email }}) with what you need.
Requests made at least two weeks ahead are easiest to arrange, but ask even if
you are later than that.
