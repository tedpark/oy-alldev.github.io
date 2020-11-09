---
layout: main
main: true
title: 소소한 일상
---

<ul class="catalogue">
{% assign sorted = site.pages | sort: 'date' | reverse %}
{% for page in sorted %}
{% if page.type == 'life' %}
{% include post-list.html %}
{% endif %}
{% endfor %}
</ul>
