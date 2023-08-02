---
layout: page
permalink: /misc/
title: Miscellaneous
---

{% for post in site.categories.ML-DL %}
 <li><span>{{ post.date | date_to_string }}</span> &nbsp; <a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}