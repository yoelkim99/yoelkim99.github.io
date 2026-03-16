---
layout: page
permalink: /publications/
title: publications
description: Selected publications and conference papers.
nav: true
nav_order: 2
---

<div class="publications">
  <h2>International Conferences</h2>
  {% bibliography --group_by none --query @*[pubtype=international-conference]* %}

  <h2>Domestic Conferences</h2>
  {% bibliography --group_by none --query @*[pubtype=domestic-conference]* %}
</div>
