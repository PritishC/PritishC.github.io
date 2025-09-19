---
layout: page
permalink: /publications/
title: publications
description: A list of selected publications.
years: [2025, 2023]
nav: true
nav_order: 1
---
<!-- _pages/publications.md -->
<div class="publications">

{%- for y in page.years %}
  <h2 class="year">{{y}}</h2>
  {% bibliography --file papers --group_by year --group_order descending %}
{% endfor %}

</div>
