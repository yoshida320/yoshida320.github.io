---
layout: page
permalink: /personal/
title: personal
nav: true
nav_order: 4
---

<h2>{{ site.data.personal.heading }}</h2>

<ul>
  {% for qualification in site.data.personal.qualifications %}
    <li>{{ qualification.name }}（{{ qualification.date }}）</li>
  {% endfor %}
</ul>

<h2>{{ site.data.personal.miscellaneous_heading }}</h2>

<ul>
  {% for item in site.data.personal.miscellaneous %}
    <li>{{ item.name }}（{{ item.date }}）</li>
  {% endfor %}
</ul>
