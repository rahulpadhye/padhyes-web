---
layout: default
title: Family List
---

## Padhye Family Members

Here is a list of family members:

<ul>
{% for person_data in site.data.family %}
  {% assign person_slug = person_data.name | slugify %}
  {% assign person_page = site.people | where: "slug", person_slug | first %}
  <li>
    <a href="{{ person_page.url | relative_url }}">
      <strong>{{ person_data.name }}</strong>
    </a>
    (Born: {{ person_data.birth_date }})
  </li>
{% endfor %}
</ul>
