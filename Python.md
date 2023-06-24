---
layout: page
permalink: /python/
title: Python
order: 3
---

{% for post in site.categories.Python %}
 <li><span>{{ post.date | date_to_string }}</span> &nbsp; <a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}