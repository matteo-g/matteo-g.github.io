---
permalink: /side-quests/
layout: minimal
title: "Side Quests"
author_profile: false
---

Here, a collection of ideas, posts, and other, concerning my side quests.

{% for post in site.posts limit:1 %}
<div class="side-quest-entry">
  <div class="sq-date">{{ post.date | date: "%B %d, %Y" }}</div>
  <div class="sq-title"><a href="{{ post.url }}">{{ post.title }}</a></div>
  {% if post.excerpt %}
  <div class="sq-excerpt">{{ post.excerpt | strip_html | truncatewords: 40 }}</div>
  {% endif %}
</div>
{% endfor %}
