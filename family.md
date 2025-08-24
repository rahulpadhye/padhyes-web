---
layout: default
title: Family List
---

## Padhye Family Members

Here is a list of family members:

{% assign male_avatar = "https://cdn3.iconfinder.com/data/icons/basic-interface/100/user_man-128.png" %}
{% assign female_avatar = "https://cdn3.iconfinder.com/data/icons/avatar-user/64/Artboard_11-128.png" %}

<div class="family-list">
{% for person_data in site.data.family %}
  {% assign person_slug = person_data.name | slugify %}
  {% assign person_page = site.people | where: "slug", person_slug | first %}

  {% if person_data.photo %}
    {% assign person_image = person_data.photo %}
  {% else %}
    {% if person_data.gender == "Male" %}
      {% assign person_image = male_avatar %}
    {% else %}
      {% assign person_image = female_avatar %}
    {% endif %}
  {% endif %}

  <div class="family-list-item">
    <a href="{{ person_page.url | relative_url }}">
      <img src="{{ person_image }}" alt="Photo of {{ person_data.name }}" class="family-list-avatar">
      <div class="family-list-details">
        <strong>{{ person_data.name }}</strong>
        <span>(Born: {{ person_data.birth_date }})</span>
      </div>
    </a>
  </div>
{% endfor %}
</div>
