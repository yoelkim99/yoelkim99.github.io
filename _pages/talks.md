---
layout: page
permalink: /talks/
title: Talks
nav: true
nav_order: 3
---

{% assign talks = site.data.talks | sort: 'date' | reverse %}
{% assign talk_years = talks | group_by_exp: 'talk', "talk.date | date: '%Y'" %}
{% assign slide_formats = 'pdf,pptx' | split: ',' %}

<div class="publications talks">
  {% for year in talk_years %}
    <h2 class="bibliography">{{ year.name }}</h2>
    <ol class="bibliography">
      {% for talk in year.items %}
        <li>
          <div class="title">{{ talk.title | escape }}</div>
          <div class="periodical">
            {{ talk.type | escape }}
            {% if talk.event != blank %}
              {% if talk.type != blank %} · {% endif %}
              {% if talk.url != blank %}
                <a class="talk-venue" href="{{ talk.url | escape }}">{{ talk.event | escape }}</a>
              {% else %}
                <span>{{ talk.event | escape }}</span>
              {% endif %}
            {% endif %}
          </div>
          <div class="periodical">
            <time datetime="{{ talk.date }}">{{ talk.date | date: '%b %-d, %Y' }}</time> · {{ talk.location | escape }}
          </div>
          {% if talk.pdf != blank or talk.pptx != blank %}
            <div class="links">
              {% for slide_format in slide_formats %}
                {% assign slide_file = talk[slide_format] %}
                {% if slide_file != blank %}
                  {% if slide_file contains '://' %}
                    {% assign slide_url = slide_file %}
                  {% else %}
                    {% assign slide_directory = slide_format | prepend: '/assets/' | append: '/' %}
                    {% assign slide_url = slide_file | prepend: slide_directory | relative_url %}
                  {% endif %}
                  <a href="{{ slide_url | escape }}" class="btn btn-sm z-depth-0" aria-label="Slides ({{ slide_format | upcase }}): {{ talk.title | escape }}">
                    Slides{% if talk.pdf != blank and talk.pptx != blank %} ({{ slide_format | upcase }}){% endif %}
                  </a>
                {% endif %}
              {% endfor %}
            </div>
          {% endif %}
        </li>
      {% endfor %}
    </ol>
  {% endfor %}
</div>
