---
title: History
layout: default
---

{% for post in site.posts %}
{% if post.category == 'History' %}
<h1 id="{{ post.version }}">{{ post.title }}</h1>
<small>{{ post.date | date: "%-d %B %Y" }}</small>
{{ post.content }}
{% endif %}
{% endfor %}
