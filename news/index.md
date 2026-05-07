---
layout: page
title: News
slug: news
hero_slug: news
permalink: /news/
---

{% assign posts = site.news | sort: "date" | reverse %}
{% assign recent = posts | slice: 0, 10 %}
{% assign older  = posts | slice: 10, 1000 %}

<ul class="news-list">
{% for post in recent %}
  <li class="news-entry">
    {% if post.image %}
      <img class="news-thumb" src="{{ post.image | relative_url }}" alt="">
    {% else %}
      <div class="news-thumb"></div>
    {% endif %}
    <div class="news-body">
      <p class="news-date">{{ post.date | date: "%B %-d, %Y" }}</p>
      {{ post.content }}
    </div>
  </li>
{% endfor %}
</ul>

{% if older.size > 0 %}
<details class="show-more">
  <summary>Previous news</summary>
  <ul class="news-list">
    {% for post in older %}
    <li class="news-entry">
      {% if post.image %}
        <img class="news-thumb" src="{{ post.image | relative_url }}" alt="">
      {% else %}
        <div class="news-thumb"></div>
      {% endif %}
      <div class="news-body">
        <p class="news-date">{{ post.date | date: "%B %-d, %Y" }}</p>
        {{ post.content }}
      </div>
    </li>
    {% endfor %}
  </ul>
</details>
{% endif %}
