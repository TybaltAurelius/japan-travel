---
title: Our Japan Trips
layout: about
permalink: /trips.html
---

<div class="row">
{% assign trips = "Fall 2023,Spring 2024,Fall 2025,Spring 2026" | split: "," %}
{% for trip in trips %}
  <div class="col-md-3 mb-3">
    <div class="card h-100 text-center">
      <div class="card-body">
        <h5 class="card-title">Explore {{ trip }} Trip</h5>
        <p class="card-text">Click below to see all pics and videos for the {{ trip }} Trip</p>
        <a href="{{ '/browse.html' | relative_url }}#{{ trip | uri_escape }}" class="btn btn-primary">
          View {{ trip }} Trip
        </a>
      </div>
    </div>
  </div>
{% endfor %}
</div>
