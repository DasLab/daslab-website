---
layout: page
title: People
slug: people
hero_slug: people
permalink: /people/
---

{% assign current = site.people | where: "status", "current" | sort_natural: "name" %}
{% assign current = current | sort: "role_order" %}
{% assign alumni  = site.people | where: "status", "alumnus" %}
{% assign alumni  = alumni | sort: "name" | sort: "end_year" | reverse %}

<h2 class="section-heading">Current</h2>

<div class="people-grid">
{% for member in current %}
  <div class="person-card">
    {% if member.photo %}<img class="person-photo" src="{{ member.photo | relative_url }}" alt="{{ member.name }}">{% else %}<div class="person-photo"></div>{% endif %}
    <p class="person-name">{{ member.name }}</p>
    <p class="person-role">{{ member.role }}</p>
    {% if member.cv_url or member.profile_url %}
    <p class="person-links">
      {% if member.cv_url %}<a href="{{ member.cv_url }}" target="_blank" rel="noopener">Curriculum Vitae</a>{% endif %}
      {% if member.profile_url %}<a href="{{ member.profile_url }}" target="_blank" rel="noopener">Stanford profile</a>{% endif %}
    </p>
    {% endif %}
  </div>
{% endfor %}
</div>

<h2 class="section-heading">Alumni</h2>

{% assign visible = alumni | slice: 0, 30 %}
{% assign hidden  = alumni | slice: 30, 9999 %}

<ul class="alumni-list">
{% for a in visible %}
  <li>
    <span class="alum-name">{{ a.name }}</span>
    <span class="alum-role">{{ a.role }}</span>
  </li>
{% endfor %}
</ul>

{% if hidden.size > 0 %}
<details class="show-more">
  <summary>Show more alumni</summary>
  <ul class="alumni-list">
  {% for a in hidden %}
    <li>
      <span class="alum-name">{{ a.name }}</span>
      <span class="alum-role">{{ a.role }}</span>
    </li>
  {% endfor %}
  </ul>
</details>
{% endif %}
