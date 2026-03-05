---
title: Our Japan Trips
layout: about
permalink: /trips.html
---

{% assign trips = "Fall 2023,Spring 2024,Fall 2025,Spring 2026" | split: "," %}
<div class="row">
{% for trip in trips %}
  <div class="col-md-3">
    {% include feature/card.html 
        header="Explore Photos from the {{ trip }} Trip" 
        text="Click below to see all pics and videos for the {{ trip }} Trip" 
        href="/browse.html#{{ trip | uri_escape }}" 
        width="100" 
        centered=true %}
  </div>
{% endfor %}
</div>
