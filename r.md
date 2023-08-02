---
layout: page
permalink: /r/
title: R
---

{% for post in site.categories.R %}
 <li><span>{{ post.date | date_to_string }}</span> &nbsp; <a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>
{% endfor %}