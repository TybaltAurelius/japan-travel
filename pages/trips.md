---
title: Our Japan Trips
layout: about
permalink: /trips.html
---

<div class="row">
{% assign custom_order = "Fall 2023,Spring 2024,Fall 2025,Spring 2026" | split: "," %}

{% assign all_trips = site.collections.objects | map: "trip" | uniq %}
{% assign trips = "" | split: "" %}

{%- comment -%} Sort trips according to custom_order {%- endcomment -%}
{% for trip_name in custom_order %}
  {% if all_trips contains trip_name %}
    {% assign trips = trips | push: trip_name %}
  {% endif %}
{% endfor %}

{%- comment -%} Add any remaining trips not in custom_order {%- endcomment -%}
{% for trip_name in all_trips %}
  {% unless trips contains trip_name %}
    {% assign trips = trips | push: trip_name %}
  {% endunless %}
{% endfor %}

{%- for trip in trips -%}
  {% assign trip_object = site.collections.objects | where: "trip", trip | sort: "date" | reverse | where_exp: "o", "o.thumbnail" | first %}
  {% if trip_object %}
    <div class="col-md-3 mb-4">
      <a href="{{ '/browse.html' | relative_url }}#{{ trip | uri_escape }}" class="text-decoration-none text-dark">
        <div class="card h-100 text-center">
          {% if trip_object.thumbnail %}
            <img src="{{ trip_object.thumbnail | relative_url }}" class="card-img-top" alt="{{ trip }}">
          {% endif %}
          <div class="card-body">
            <h5 class="card-title">{{ trip }} Trip</h5>
            <p class="card-text">Click to view all items from this trip.</p>
          </div>
        </div>
      </a>
    </div>
  {% endif %}
{% endfor %}
</div>
