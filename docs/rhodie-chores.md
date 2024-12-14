---
layout: page
title: Rhodie and Chores Schedule
permalink: /rhodie-chores
---
{% assign days = site.data.chore-schedule.days %}

# Schedules by Person
{% for person in site.data.chore-schedule.persons -%}
## {{ person }}
{% for schedule in site.data.chore-schedule.schedules -%}
{%- for date in schedule.dates -%}
{%- if date.person == person -%}
{%- assign day = schedule.day-start | plus: forloop.index0 | modulo: 7 -%}
- {{ days[day] }}, {{ schedule.month | truncate: 3, "" }} {{ schedule.date-start | plus: forloop.index0 }}
{% endif -%}
{%- endfor %}
{%- endfor %}
{% endfor %}

# Full Schedule

{% for schedule in site.data.chore-schedule.schedules %}
## {{ schedule.month }}

| Date | Person | Notes |
| ---- | ------ | ----- |
  {% for date in schedule.dates -%}
  {% assign day = schedule.day-start | plus: forloop.index0 | modulo: 7 -%}
| {{ days[day] }}, {{ schedule.month | truncate: 3, "" }} {{ schedule.date-start | plus: forloop.index0 }} | {{ date.person }} | {% if date.unavailable %}Unavailable: {{ date.unavailable | join: ", " }}{% endif %} |
  {% endfor %}
{% endfor %}
