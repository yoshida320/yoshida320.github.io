---
layout: page
permalink: /presentations/
title: presentations
nav: true
nav_order: 3
description:
---

{% assign cv_sections = site.data.cv.cv.sections %}
{% assign presentation_sections = "International Presentations|International Conferences/Workshops,Domestic Presentations|Domestic Conferences/Workshops" | split: "," %}
{% assign presentation_types = "talk|Talks,poster|Posters" | split: "," %}

<div class="presentations-list">
  {% for section_entry in presentation_sections %}
    {% assign section_parts = section_entry | split: "|" %}
    {% assign section_key = section_parts[0] %}
    {% assign section_title = section_parts[1] %}
    {% assign section_presentations = cv_sections[section_key] %}

    {% if section_presentations.size > 0 %}
      <section class="presentation-scope">
        <h2>{{ section_title }}</h2>

        {% for type_entry in presentation_types %}
          {% assign type_parts = type_entry | split: "|" %}
          {% assign type_key = type_parts[0] %}
          {% assign type_title = type_parts[1] %}
          {% assign has_type = false %}

          {% for entry in section_presentations %}
            {% if entry.web_type == type_key %}
              {% assign has_type = true %}
            {% endif %}
          {% endfor %}

          {% if has_type %}
            <section class="presentation-type">
              <h3>{{ type_title }}</h3>
              <ol>
                {% for entry in section_presentations %}
                  {% if entry.web_type == type_key %}
                    <li>
                      {{ entry.web_authors_html }}, {{ entry.web_title }}, {{ entry.web_venue }}, {{ entry.web_location }}, {{ entry.web_date }}.
                    </li>
                  {% endif %}
                {% endfor %}
              </ol>
            </section>
          {% endif %}
        {% endfor %}
      </section>
    {% endif %}

{% endfor %}

</div>

<style>
  .presentation-scope {
    margin-top: 2rem;
  }

  .presentation-scope:first-child {
    margin-top: 0;
  }

  .presentation-type {
    margin-top: 1rem;
  }

  .presentation-type h3 {
    font-size: 1.35rem;
    margin-bottom: 0.5rem;
  }

  .presentation-type ol {
    padding-left: 1.5rem;
  }

  .presentation-type li {
    line-height: 1.55;
    margin-bottom: 0.6rem;
  }
</style>
