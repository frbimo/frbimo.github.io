---
layout: archive
permalink: /notes/
title: "Notes"
author_profile: true
---

{% include base_path %}

{% for post in site.notes reversed %}
  {% include archive-single-title.html %}
{% endfor %}