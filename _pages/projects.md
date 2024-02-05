---
layout: page
title: professional experience
permalink: /professional experience/
description: 
nav: true
nav_order: 3
display_categories: [work, fun]
horizontal: false
---

<!-- pages/professional experience.md -->
<div class="prfessional experience">
{% if site.enable_prfessional experience_categories and page.display_categories %}
  <!-- Display categorized prfessional experience -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_prfessional experience = site.prfessional experience | where: "category", category %}
  {% assign sorted_prfessional experience = categorized_prfessional experience | sort: "importance" %}
  <!-- Generate cards for each prfessional experience -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="grid">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = site.projects | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="grid">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
