---
title: Our Japan Trips
layout: about
permalink: /trips.html
---

<div class="row">
{% assign trips = 
  "Fall 2023:japan_m_00251,Spring 2024:japan2024_s_0098,Fall 2025:japan2025_s_0319,Spring 2026:demo004" | split: "," %}

{% for trip_pair in trips %}
  {% assign parts = trip_pair | split: ":" %}
  {% assign trip_name = parts[0] %}
  {% assign object_id = parts[1] %}
  
  <div class="col-md-3 mb-4">
    <a href="{{ '/browse.html' | relative_url }}#{{ trip_name | uri_escape }}" class="text-decoration-none text-dark">
      {% include feature/card.html 
        header="Explore {{ trip_name }} Trip" 
        text="Click to view all items for {{ trip_name }}" 
        objectid="{{ object_id }}" 
        width="100" 
        centered=true %}
    </a>
  </div>
{% endfor %}
</div>
