---
layout: page
title: Rhodie and Chores Schedule
permalink: /rhodie-chores
---
{% assign days = site.data.chore-schedule.days %}

Thank you so much for helping out with Rhodie and chores for Sarah/Sassy/Momma/Mama. Together we'll get it done!

Each visit be sure to:
- Feed Rhodie by:
  - Filling up his dry food
  - Giving him a third container of wet food (check the fridge for leftovers!)
  - Refreshing his water
- Empty Rhodie's litter box
- Check for any Rhodie vomit. His tummy is sensitive.
- Give Rhodie some company!
- Fetch the mail and collect it on the counter (Tanner will take it home on his visits)
- Start the cars for a moment especially if the weather is cold
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
