---
layout: page
permalink: /publications/
title: Publications
nav: true
nav_order: 2
---

<div class="publications">
  <h3>International Conferences</h3>
  {% bibliography --group_by none --query @*[pubtype=international-conference]* %}

  <h3>Domestic Conferences</h3>
  {% bibliography --group_by none --query @*[pubtype=domestic-conference]* %}
</div>
