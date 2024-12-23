---
layout: page
title: Chores Schedule
permalink: /rhodie-chores
---
{% assign days = site.data.chore-schedule.days %}

Each visit be sure to:
- Fetch the mail and collect it on the counter (Tanner will take it home on his visits).
- Start the cars for a moment especially if the weather is cold.
- If the weather is cold, make sure faucets are dripping so they don't freeze.
- Text the group when you're done so we know everything's taken care of!

Below you will find the schedules for each volunteer as well as the full schedule at the end.

Thanks again!

# Schedules by Volunteer
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

| Date | Volunteer | Notes |
| ---- | --------- | ----- |
  {% for date in schedule.dates -%}
  {% assign day = schedule.day-start | plus: forloop.index0 | modulo: 7 -%}
| {{ days[day] }}, {{ schedule.month | truncate: 3, "" }} {{ schedule.date-start | plus: forloop.index0 }} | {{ date.person }} | {% if date.unavailable %}Unavailable: {{ date.unavailable | join: ", " }}{% endif %} |
  {% endfor %}
{% endfor %}
