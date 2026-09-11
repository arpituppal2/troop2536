---
layout: default
title: Home
description: Scouting America Troop 2536 in Mountain House, CA — adventure, leadership, and character for boys ages 11-17.
---

<section class="hero">
  <h1>Troop 2536</h1>
  <p>
    A Scouts BSA troop in Mountain House, California. Camping, hiking,
    pioneering, service, and leadership — run by the scouts, guided by
    trained adults. Boys ages 11–17 are welcome year-round.
  </p>
  <div class="hero-rule" aria-hidden="true"></div>
</section>

<div class="columns">
  <div>
    <h3>Weekly meetings</h3>
    <p><span class="todo-inline">TODO(dad): meeting night, time, and location</span></p>
  </div>
  <div>
    <h3>Monthly adventures</h3>
    <p>Campouts and outings nearly every month — see the <a href="{{ '/schedule/' | relative_url }}">schedule</a> for what's next.</p>
  </div>
  <div>
    <h3>Youth-led</h3>
    <p>Scouts plan and lead everything. They learn leadership by leading.</p>
  </div>
</div>

<h2>Upcoming events</h2>
<p class="page-lede">The troop calendar, straight from our Google Calendar — always current.</p>
{% include gcal.html mode="AGENDA" height="400" title="Upcoming Troop 2536 events" %}
<p><a href="{{ '/schedule/' | relative_url }}">Full schedule →</a></p>

<h2>Latest announcements</h2>
{% assign recent = site.announcements | sort: "date" | reverse | limit: 3 %}
{% for announcement in recent %}
  <article class="announcement">
    <h2>{{ announcement.title }}</h2>
    <span class="date">{{ announcement.date | date: "%B %-d, %Y" }}</span>
    {{ announcement.content }}
  </article>
{% else %}
  <p>No announcements yet — check back soon!</p>
{% endfor %}
<p><a href="{{ '/announcements/' | relative_url }}">All announcements →</a></p>