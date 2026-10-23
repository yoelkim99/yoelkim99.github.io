---
layout: page
permalink: /talks/
title: Talks
description: Presentations at conferences, workshops, and graduate research events.
nav: true
nav_order: 3
---

{% assign talks = site.data.talks | sort: 'date' | reverse %}
{% assign talk_years = talks | group_by_exp: 'talk', "talk.date | date: '%Y'" %}

<div class="publications">
  {% for year in talk_years %}
    <h2 class="bibliography">{{ year.name }}</h2>
    <ol class="bibliography">
      {% for talk in year.items %}
        <li>
          <div class="title">{{ talk.title | escape }}</div>
          <div class="periodical">{{ talk.type | escape }} · <em>{{ talk.event | escape }}</em></div>
          <div class="periodical">
            <time datetime="{{ talk.date }}">{{ talk.date | date: '%b %-d, %Y' }}</time> · {{ talk.location | escape }}
          </div>
          {% if talk.pdf != blank %}
            <div class="links">
              {% if talk.pdf contains '://' %}
                {% assign pdf_url = talk.pdf %}
              {% else %}
                {% assign pdf_url = talk.pdf | prepend: '/assets/pdf/' | relative_url %}
              {% endif %}
              <a href="{{ pdf_url | escape }}" class="btn btn-sm z-depth-0" aria-label="Presentation PDF: {{ talk.title | escape }}">PDF</a>
            </div>
          {% endif %}
        </li>
      {% endfor %}
    </ol>
  {% endfor %}
</div>
