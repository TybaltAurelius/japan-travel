---
title: Our Japan Trips
layout: about
permalink: /trips.html
---

<div class="row">
{% assign custom_order = "Fall 2023,Spring 2024,Fall 2025,Spring 2026" | split: "," %}

{% assign all_trips = site.data.collections | map: "trip" | uniq %}
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
  {% assign trip_objects = site.data.collections | where: "trip", trip | sort: "date" | reverse %}
  {% if trip_objects.size > 0 %}
    <div class="col-md-3 mb-4">
      <a href="{{ '/browse.html' | relative_url }}#{{ trip | uri_escape }}" class="text-decoration-none text-dark">
        <div class="card h-100 text-center">

          {% comment %} Carousel for trip thumbnails {% endcomment %}
          <div id="carousel-{{ trip | slugify }}" class="carousel slide" data-bs-ride="carousel">
            <div class="carousel-inner">
              {% for obj in trip_objects limit:5 %}
                {% if obj.thumbnail %}
                  <div class="carousel-item {% if forloop.first %}active{% endif %}">
                    <img src="{{ obj.thumbnail | relative_url }}" class="d-block w-100" style="height:150px; object-fit:cover;" alt="{{ trip }}">
                  </div>
                {% endif %}
              {% endfor %}
            </div>
            {% if trip_objects.size > 1 %}
              <button class="carousel-control-prev" type="button" data-bs-target="#carousel-{{ trip | slugify }}" data-bs-slide="prev">
                <span class="carousel-control-prev-icon" aria-hidden="true"></span>
                <span class="visually-hidden">Previous</span>
              </button>
              <button class="carousel-control-next" type="button" data-bs-target="#carousel-{{ trip | slugify }}" data-bs-slide="next">
                <span class="carousel-control-next-icon" aria-hidden="true"></span>
                <span class="visually-hidden">Next</span>
              </button>
            {% endif %}
          </div>

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
