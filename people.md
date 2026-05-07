---
layout: page
title: People
slug: people
hero_slug: people
permalink: /people/
---

<h2 class="section-heading">Current</h2>

<div class="people-grid">
{% assign current = site.people | sort: "order" %}
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

{% assign alumni = site.alumni | sort: "order" %}
{% assign visible = alumni | slice: 0, 30 %}
{% assign hidden  = alumni | slice: 30, 1000 %}

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
  <summary>Show {{ hidden.size }} earlier alumni</summary>
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
