---
layout: default
title: Announcements
description: Latest news and announcements from Troop 2536.
---

<p class="page-lede">The latest news from the troop, newest first. Pinned items stay on top.</p>

{% assign pinned = site.announcements | where: "pinned", true | sort: "date" | reverse %}
{% assign rest = site.announcements | where: "pinned", false | sort: "date" | reverse %}

{% for announcement in pinned %}
  <article class="announcement is-pinned">
    <h2>{{ announcement.title }} <span class="pinned-label">Pinned</span></h2>
    <span class="date">{{ announcement.date | date: "%B %-d, %Y" }}</span>
    {{ announcement.content }}
  </article>
{% endfor %}

{% for announcement in rest %}
  <article class="announcement">
    <h2>{{ announcement.title }}</h2>
    <span class="date">{{ announcement.date | date: "%B %-d, %Y" }}</span>
    {{ announcement.content }}
  </article>
{% endfor %}

{% if pinned == empty and rest == empty %}
  <p>No announcements yet — check back soon!</p>
{% endif %}
