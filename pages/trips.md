---
title: Our Japan Trips
layout: about
permalink: /trips.html
---

<div class="row">
{% assign trips = "Fall 2023:japan_m_00251,Spring 2024:japan2024_s_0098,Fall 2025:japan2025_s_0319,Spring 2026:japan_m_00065" | split: "," %}

{% for trip_pair in trips %}
  {% assign parts = trip_pair | split: ":" %}
  {% assign trip_name = parts[0] %}
  {% assign object_id = parts[1] %}

  {% assign card_header = "Explore " | append: trip_name | append: " Trip" %}
  {% assign card_text = "Click to view all items for " | append: trip_name %}

  <div class="col-md-3 mb-4">
    <a href="{{ '/browse.html' | relative_url }}#{{ trip_name | uri_escape }}" class="text-decoration-none text-dark">
      {% include feature/card.html 
         header=card_header
         text=card_text
         objectid=object_id
         width="100"
         centered="true" %}
    </a>
  </div>
{% endfor %}
</div>
